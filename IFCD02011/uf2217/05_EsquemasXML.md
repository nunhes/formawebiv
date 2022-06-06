# Esquemas XML

## introdución

XML Schema é unha linguaxe de esquema que se usa para describir a estrutura e as restricións de contido dos documentos XML dunha forma moi precisa, máis aló das regras sintácticas impostas pola propia linguaxe XML. Deste xeito, conséguese unha percepción do tipo de documento cun alto nivel de abstracción. Foi desenvolvido polo World Wide Web Consortium (W3C) e alcanzou o nivel de recomendación en maio de 2001.

O esquema XML pretende proporcionar maior poder expresivo que os DTD, que son menos capaces de describir documentos a nivel formal.

As vantaxes que proporciona son:

- Está baseado en XML, polo que ten todas as vantaxes dun documento XML.
- Ten unha gran variedade de tipos de datos.
- Ten un modelo de datos abertos.
- Admite espazos de nomes (unicidade dos nomes, algo que non poderiamos ter coas DTD).
- Admite tipos en atributos.

## Nodo raíz `schema`

Os esquemas manteñen a estrutura e a sintaxe dos documentos XML, polo que deben ter un nodo raíz e conter o esquema completo dentro del. Por suposto que debes ter o prólogo (é dicir, a definición da versión XML).

```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  ...
</xs:schema>
```



Ter en conta que te refires a unha URL, ese enderezo contén a definición de todos os elementos e atributos que se poden usar nun esquema. Isto non significa que para programar en XML necesites estar conectado a Internet.

Usa un atributo `xmlns` que significa espazo de *nomes XML* para crear un espazo de nomes XML ligado a un prefixo que neste caso é `xs`, pero que pode ser calquera cousa xa que só actúa como variable ( tamén se usa `xsd`). Serve para que cada vez que se utilice un elemento ou tipo desa "biblioteca" se dea ese prefixo, no caso de que se utilizaran máis referencias a outras URL, os elementos de cada unha delas se distinguirían claramente mediante os prefixos.

Usando este atributo `xmlns`, crea un espazo de nomes para cada URL referenciado, polo que se hai dous elementos co mesmo nome diferenciaranse claramente.

## Declaración de elementos

### Tipos de elementos

Existen tres tipos de elementos a definir nun esquema:

- **elementos estándar**

  Sen fillos e sen restricións nin atributos.

- **elementos sinxelos**

  Elementos sen fillos pero con restricións e sen atributos.

- **elementos complexos**

  Elementos con fillos e/ou atributos.

[![../_images/personal_interno.png](https://lm-xml-apuntes.readthedocs.io/_images/personal_interno.png)](https://lm-xml-apuntes.readthedocs.io/_images/personal_interno.png)

Exemplo de xerarquía.

Neste exemplo temos os seguintes tipos de elementos:

- Elementos complexos: `PERSONAL`e `INTERNO`(con fillos).
- Elementos sinxelos: `TELEFONO`e `DIRECCIÓN`(con restricións).
- Elementos estándar: `NOMBRE`(sen fillos nin restricións).

### Estruturas

As dúas estruturas posibles son:

```
<xs:element name="nome_do_elemento" type="tipo" />
```



Esta estrutura está baleira, é dicir, defínese un nome de elemento e un tipo, o tipo pode ser un estándar XML ou un tipo definido por nós que describiría aqueles elementos que teñen fillos (complexos ou aqueles elementos que non teñen fillos pero teñen restricións).

Seguida por esta definición, quedaría por debaixo da definición do tipo. Esta estrutura é a máis aconsellable pero non a única.

```
<xs:element name="nome_do_elemento">
  ...
</xs:element>
```



Esta estrutura sería equivalente á anterior, agás que neste caso non se pon como atributo o tipo de elemento, senón que esa definición se faría entre as etiquetas de inicio e peche de `element`.

Pode conter atributos cuxos valores están sempre entre comiñas:

- `name`

  Nome do elemento.

- `type`

  Tipo simple predefinido, ya sean los estándares o unos propios.

- `maxOccurs`

  Número máximo de veces que pode aparecer `[0..unbounded]`.

- `minOccurs`

  Número mínimo de veces que pode aparecer.

- `ref`

  Para importar doutros esquemas ou referirse a un elemento xa declarado anteriormente neste mesmo esquema.

:eye: Sen poñer `maxOccurs` nin  `minOccurs`, este elemento sempre aparece exactamente unha vez.

### Tipos de datos

As dúas táboas seguintes enumeran os tipos de datos primitivos e derivados que podemos usar nos esquemas XML.

#### Primitivos

| tipo de data   | Descrición                                                   |
| -------------- | ------------------------------------------------------------ |
| `string`       | Representa cadeas de caracteres.                             |
| `boolean`      | Representa valores booleanos, que son `true` o `false`.      |
| `decimal`      | Representa números de precisión arbitraria.                  |
| `float`        | Representa números de coma flotante de 32 bits de precisión simple. |
| `double`       | Representa números de coma flotante de 64 bits de dobre precisión. |
| `duration`     | Representa unha duración de tempo. O modelo de `duration`é `PnYnMnDTnHnMnS`, onde `nY`representa o número de anos, `nM`o número de meses, `nD`o número de días, `T`o separador de data e hora, `nH`o número de horas, `nM`o número de minutos e `nS`o número de segundos. |
| `dateTime`     | Representa unha instancia específica de tempo. O patrón `dateTime`is `CCYY-MM-DDThh:mm:ss`onde `CC`representa o século, `YY`ano, `MM`mes e `DD`día, precedido dun `-`carácter negativo inicial opcional ( ) para indicar un número negativo. Se se omite o carácter negativo, `+`asúmese positivo ( ). O `T`é o separador de data e hora, e `hh`, `mm`e `ss` representan a hora, o minuto e o segundo, respectivamente. Pódense usar díxitos adicionais para aumentar a precisión dos segundos decimais, se o desexa. Por exemplo, `ss.ss...`admite o formato con calquera número de díxitos despois do punto decimal. A parte de segundos decimais é opcional. |
| `time`         | Representa unha instancia de tempo que se repite todos os días. O modelo `time`ten `hh:mm:ss.sss`un indicador de zona horaria opcional. |
| `date`         | Representa unha data do calendario. O modelo de `date`ten `CCYY-MM-DD`un indicador de zona horaria opcional como o de `dateTime`. |
| `hexBinary`    | Representa datos binarios arbitrarios codificados en hexadecimal. `hexBinary`é o conxunto de secuencias de lonxitude finita de octetos binarios. Cada octeto binario está codificado como unha tupla de caracteres formada por dous díxitos hexadecimais ( `[0-9a-fA-F]`) e representa o código do octeto. |
| `base64Binary` | Representa datos binarios codificados en Base64 arbitrarios. `base64Binary`é o conxunto de secuencias de lonxitude finita de octetos binarios. |
| `anyURI`       | Representa un URI segundo o definido polo RFC 2396. Un valor `anyURI`pode ser absoluto ou relativo e pode ter un identificador de fragmento opcional. |
| `QName`        | Representa un nome completo, que está formado por un prefixo e un nome local separados por dous puntos. Tanto o prefixo como os nomes locais deben ser un NCName. O prefixo debe estar asociado cunha referencia a un URI de espazo de nomes mediante unha declaración de espazo de nomes. |
| `NOTATION`     | Representa un conxunto de `QName`.                           |

#### Derivados

| tipo de data         | Descrición                                                   |
| -------------------- | ------------------------------------------------------------ |
| `normalizedString`   | Representa cadeas normalizadas de espazos en branco. Este tipo de datos deriva de `string`. |
| `token`              | Representa cadeas convertidas en símbolos. Este tipo de datos deriva de `normalizedString`. |
| `language`           | Representa identificadores de linguaxe natural (definidos polo RFC 1766). Este tipo de datos deriva de `token`. |
| `IDREFS`             | Representa o tipo de atributo `IDREFS`. Contén un conxunto de valores de tipo `IDREF`. |
| `ENTITIES`           | Representa o tipo de atributo `ENTITIES`. Contén un conxunto de valores de tipo `ENTITY`. |
| `NMTOKEN`            | Representa o tipo de atributo `NMTOKEN`. `NMTOKEN`é un conxunto de caracteres de nomes (letras, díxitos e outros caracteres) en calquera combinación. A diferenza de `Name`e `NCName`, `NMTOKEN`, non ten restricións sobre o carácter inicial. Este tipo de datos deriva de `token`. |
| `NMTOKENS`           | Representa o tipo de atributo `NMTOKENS`. Contén un conxunto de valores de tipo `NMTOKEN`. |
| `Name`               | Representar nomes en XML. `Name`é un símbolo que comeza cunha letra, guión baixo ou dous puntos e continúa con caracteres de nome (letras, díxitos e outros caracteres). Este tipo de datos deriva de `token`. |
| `NCName`             | Representa os nomes sen dous puntos. Este tipo de datos é o mesmo que `Name`, excepto que non pode comezar con dous puntos. Este tipo de datos deriva de `Name`. |
| `ID`                 | Representa o tipo de atributo `ID`definido na recomendación XML 1.0. Non `ID`debe incluír dous puntos (como `NCName`) e debe ser único dentro do documento XML. Este tipo de datos deriva de `NCName`. |
| `IDREF`              | Representa unha referencia a un elemento que ten un atributo `ID`que coincide co `ID`especificado. `IDREF` debe ser un `NCName`e ter un valor dun elemento ou un atributo de tipo `ID`dentro do documento XML. Este tipo de datos deriva de `NCName`. |
| `ENTITY`             | Representa o tipo de atributo `ENTITY`definido na recomendación XML 1.0. É unha referencia a unha entidade non analizada cun nome que coincide co especificado. `ENTITY`debe ser a `NCName`e declarado no esquema como un nome de entidade non analizado. Este tipo de datos deriva de `NCName`. |
| `integer`            | Representa unha secuencia de díxitos decimais cun signo inicial opcional ( `+`ou ). `-`Este tipo de datos deriva de `decimal`. |
| `nonPositiveInteger` | Representa un número enteiro menor ou igual a cero. `nonPositiveInteger`consta dun signo negativo ( `-`) e dunha secuencia de díxitos decimais. Este tipo de datos deriva de `integer`. |
| `negativeInteger`    | Representa un número enteiro menor que cero. Consta dun signo negativo ( `-`) e dunha secuencia de díxitos decimais. Este tipo de datos deriva de `nonPositiveInteger`. |
| `long`               | Representa un número enteiro cun valor mínimo de -9223372036854775808 e un valor máximo de 9223372036854775807. Este tipo de datos deriva de `integer`. |
| `int`                | Representa un número enteiro cun valor mínimo de -2147483648 e un valor máximo de 2147483647. Este tipo de datos deriva de `long`. |
| `short`              | Representa un número enteiro cun valor mínimo de -32768 e un valor máximo de 32767. Este tipo de datos deriva de `int`. |
| `byte`               | Representa un número enteiro cun valor mínimo de -128 e un valor máximo de 127. Este tipo de datos deriva de `short`. |
| `nonNegativeInteger` | Representa un número entero mayor o igual que cero. Este tipo de datos se deriva de `integer`. |
| `unsignedLong`       | Representa un número entero con un valor mínimo de cero y un valor máximo de 18446744073709551615. Este tipo de datos se deriva de `nonNegativeInteger`. |
| `unsignedInt`        | Representa un número entero con un valor mínimo de cero y un valor máximo de 4294967295. Este tipo de datos se deriva de `unsignedLong`. |
| `unsignedShort`      | Representa un número entero con un valor mínimo de cero y un valor máximo de 65535. Este tipo de datos se deriva de `unsignedInt`. |
| `unsignedByte`       | Representa un número entero con un valor mínimo de cero y un valor máximo de 255. Este tipo de datos se deriva de `unsignedShort`. |
| `positiveInteger`    | Representa un número entero mayor que cero. Este tipo de datos se deriva de `nonNegativeInteger`. |

## Tipo complejo: `complexType`x

Utilízase para definir elementos que teñen subelementos e/ou atributos.

```xml
<xs:complexType name="nome_do_tipo_complexo">
  <xs:sequence> <!-- sequence/all/choice -->
    ... subelementos ...
  </xs:sequence>
  ... atributos ...
</xs:complexType>
```



Pode conter elementos fillos:

- `sequence`

  Implica que todos os elementos deben aparecer e nesa orde (AND).

- `all`

  Implica que deben aparecer todos os elementos, independentemente da orde.

- `choice`

  Implica que só debería aparecer un deses elementos (OR).

- `attribute`

  Para establecer atributos.

Pode ter os seguintes atributos:

- `name`

  Nome do tipo complexo.

- `mixed`

  Pode ter dous valores `true`ou `false`.

- `type`

  Tipo de datos cos que se identifica.

Dúas estruturas posibles:

- O primeiro contén o tipo dentro da estrutura `element`:

  ```
  <xs:element name="contacto">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="destinatario" type="xs:string" />
        <xs:element name="remitente" type="xs:string" />
        <xs:element name="titulo" type="xs:string" />
        <xs:element name="contenido" type="xs:string" />
      </xs:sequence>
      <xs:attribute name="fecha" type="xs:date"/>
    </xs:complexType>
  </xs:element>
  ```

  

- O que fai a segunda estrutura é definir primeiro o elemento cun tipo e despois definir fóra dese tipo:

  ```xml-dtd
  <xs:element name="contacto" type="tipo_contacto"/>
  
  <xs:complexType name="tipo_contacto">
    <xs:sequence>
      <xs:element name="destinatario" type="xs:string" />
      <xs:element name="remitente" type="xs:string" />
      <xs:element name="titulo" type="xs:string" />
      <xs:element name="contenido" type="xs:string" />
    </xs:sequence>
    <xs:attribute name="fecha" type="xs:date"/>
  </xs:complexType>
  ```

:eye: A segunda opción é a mellor porque permite reutilizar ese tipo para outros elementos. Ademais, os analizadores toleran mellor esta estrutura.

### Elementos `sequence`, `all`  e  `choice`

Estes tres elementos nunca se usan xuntos, só aparece un deles no elemento `complexType`. Utilízase para describir en que orde e como deben aparecer os subelementos do `complexType`.

É equivalente a, no DTD, poñer comas ou barras verticais na descrición dun elemento con fillos.

#### `sequence`

Este elemento indica que é obrigatorio que aparezan todos os elementos especificados e na orde en que se definen. É o equivalente a un AND.

Neste exemplo, defínese o elemento  `libro`, con tres subelementos obrigatorios que deben aparecer exactamente nesta orde (1º `titulo`, 2º `autor`e 3º `editorial`) e se non é asi  - non aparecen nesa orde ou non aparece un deles- o analizador produciría un erro.

```
<xs:element name="libro" type="tipo_libro"/>

<xs:complexType name="tipo_libro">
  <xs:sequence>
    <xs:element name="titulo" type="xs:string" />
    <xs:element name="autor" type="xs:string" />
    <xs:element name="editorial" type="xs:string" />
  </xs:sequence>
</xs:complexType>

<libro>
  <titulo>El señor de los anillos</titulo>
  <autor>John Ronald Ruelen Tolkien</autor>
  <editorial>Tirant Lo Blanch</editorial>
</libro>
```



#### `all`

Este elemento indica que é obrigatorio que todos os elementos especificados aparezan, pero NON na orde en que se definen.

Este exemplo define o elemento `libro`, con tres subelementos necesarios.

```
<xs:element name="libro" type="tipo_libro"/>

<xs:complexType name="tipo_libro">
  <xs:all>
    <xs:element name="titulo" type="xs:string" />
    <xs:element name="autor" type="xs:string" />
    <xs:element name="editorial" type="xs:string" />
  </xs:all>
</xs:complexType>

<libro>
  <titulo>El señor de los anillos</titulo>
  <editorial>Tirant Lo Blanch</editorial>
  <autor>John Ronald Ruelen Tolkien</autor>
</libro>
```



#### `choice`

Este elemento indica que só debe aparecer un de todos os elementos especificados. É o equivalente a OR.

Este exemplo define o elemento `libro`, con tres posibles subelementos. Podes ter  `titulo`  ou  `autor`  ou  `editorial`.

```
<xs:element name="libro" type="tipo_libro"/>

<xs:complexType name="tipo_libro">
  <xs:choice>
    <xs:element name="titulo" type="xs:string" />
    <xs:element name="autor" type="xs:string" />
    <xs:element name="editorial" type="xs:string" />
  </xs:choice>
</xs:complexType>

<libro>
  <titulo>El señor de los anillos</titulo>
</libro>
```



### Elemento`attribute`

Para definir os atributos dun elemento ou tipo de elemento utilizamos a seguinte estrutura:

```
<xs:attribute name="nome_atributo" type="tipo_atributo" use="modificador" />
```



Pode conter os seguintes atributos:

- `name`

  É o nome do atributo.

- `type`

  É o tipo do atributo.

- `use`

  Para definir se é un atributo obrigatorio ou opcional. Para definir un atributo como obrigatorio, asignaremos o valor `required`. Por defecto é opcional.

A localización do atributo non pode ir por si mesma, xa que con esta estrutura non saberiamos a que elemento se refire. Para iso, sempre colócase dentro dunha estrutura `complexType`.

## tipo simple:`simpleType`

Un tipo simple utilízase para definir unha serie de restricións a un elemento ou a un atributo. É moi útil para definir intervalos, tipos enumerados, etc.

```
<xs:simpleType name="nome_del_tipo_simple">
  <xs:restriction>
    ... restricciones ...
  </xs:restriction>
</xs:simpleType>
```



Pode conter elementos fillos:

- `restriction`

  Para poñer intervalos, patróns, listar valores posibles, etc.

- `list`

  Para definir un tipo de lista.

- `union`

  Para unir varios tipos previamente definidos nun só.

Pode conter atributos:

- `name`

  Para poñerlle o nome ao tipo sinxelo.

### Elemento`restriction`

Úsase para poñer rangos, patróns, listar valores posibles, etc.

```
<xs:restriction base="xs:string">
  <xs:nome_restriccion value=""/>
</xs:restriction>
```



Ten o atributo `base`. É o tipo de datos predefinido sobre o que se constrúe a restrición.

Pode conter as seguintes restricións:

- `enumeration`

  Establécense os valores que pode tomar o elemento.

- `maxExclusive`, `minExclusive`

  Valores mínimos ou máximos que pode tomar o elemento, sen incluír o último valor.

- `maxInclusive`,`minInclusive`

  Valores mínimos ou máximos que pode tomar o elemento, incluído o último valor.

- `pattern`

  Expresión regular que expresa a restrición.`<xs:pattern value="([a-zA-Z0-9])*"/> `Neste caso dicimos que o patrón é de lonxitude indefinida, e que pode conter letras maiúsculas, minúsculas e números.`<xs:pattern value="\d{2}-\d{4}"/> `Neste caso dicimos que o patrón son dous díxitos seguidos dun guión e outros 4 díxitos. Por exemplo, 25-6789.

- `length`, `maxLength`, `minLength`

  Lonxitude dun elemento de texto tipo.

- `totalDigits`

  Número exacto de díxitos permitidos.

- `fractionDigits`

  Número máximo de cifras decimais permitidas.

Tamén neste caso hai dúas estruturas posibles:

- O primeiro contén o tipo dentro da estrutura do elemento:

  ```
  <xs:element name="lista_de_enteros">
    <xs:simpleType>
      <xs:restriction base="xs:integer">
        <xs:minInclusive value="100"/>
        <xs:maxInclusive value="200"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:element>
  ```

  

- O que fai a segunda estrutura é primeiro definir o elemento cun tipo e despois definir ese tipo fóra:

  ```xml
  <xs:element name="lista_de_enteros" type="tipo_lista_enteros"/>
  
  <xs:simpleType name="tipo_lista_enteros">
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="100"/>
      <xs:maxInclusive value="200"/>
    </xs:restriction>
  </xs:simpleType>
  ```

:eye: A segunda opción é a mellor porque permite reutilizar ese tipo para outros elementos. Ademais, os analizadores toleran mellor esta estrutura.

#### Exemplos de restricións

```
<xs:element name="sexo" type="tipo_sexo"/>

<xs:simpleType name="tipo_sexo">
  <xs:restriction base="xs:string">
    <xs:enumeration value="mujer"/>
    <xs:enumeration value="hombre"/>
  </xs:restriction>
</xs:simpleType>
```



```
<xs:element name="codigo_postal" type="tipo_cp"/>

<xs:simpleType name="tipo_cp">
  <xs:restriction base="xs:string">
    <xs:length value="5"/>
  </xs:restriction>
</xs:simpleType>
```



```
<xs:element name="password" type="tipo_password"/>

<xs:simpleType name="tipo_password">
  <xs:restriction base="xs:string">
    <xs:pattern value="\d{3}-[A-Z]{2}"/>
  </xs:restriction>
</xs:simpleType>
```



### Elemento`list`

Permite definir un tipo sinxelo composto por unha lista doutros tipos sinxelos sempre separados por espazos:

```
<xs:simpleType name="lista_numeros">
  <xs:list itemType="xs:integer"/>
</xs:simpleType>
```



### Elemento`union`

Permite combinar varios tipos sinxelos nun só:

```
<xs:simpleType name="entero_o_fecha">
  <xs:union memberTypes="xs:integer xs:date"/>
</xs:simpleType>
```



## Ampliar un tipo

Utilizándoo `xs:extension`podemos estender un `simpleType`, `complexType`engadindo elementos ou atributos adicionais a un tipo base definido anteriormente.

```
<xs:complexType name="tipo_persona">
  <xs:sequence>
    <xs:element name="nome" type="xs:string"/>
    <xs:element name="edad" type="xs:integer"/>
  </xs:sequence>
  <xs:attribute name="id" type="xs:integer"/>
</xs:complexType>

<xs:complexType name="tipo_contacto">
  <xs:complexContent>
    <xs:extension base="tipo_persona">
      <xs:sequence>
        <xs:element name="email" type="xs:string"/>
        <xs:element name="telefono" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```



## Elementos sen subelementos

Usando `simpleContent`podemos definir un elemento que só pode conter texto e atributos, non subelementos.

```
<xs:complexType name="tipo_documento">
  <xs:simpleContent>
    <xs:extension base="xs:string">
      <xs:attribute name="plantilla" type="xs:string" use="required"/>
      <xs:attribute name="revisado" type="xs:boolean" default="false"/>
    </xs:extension>
  </xs:simpleContent>
</xs:complexType>
```



## Elementos baleiros

Para definir un elemento baleiro, que non pode ter texto nin subelementos, simplemente non coloques ningún subelemento na declaración de tipo:

```
<xs:complexType name="tipo_evento">
  <xs:attribute name="nome" type="xs:string" use="required"/>
  <xs:attribute name="activo" type="xs:boolean" default="false"/>
</xs:complexType>
```



## Converter DTDs en esquemas XML

Inicialmente, coa creación de XML, os DTD utilizáronse como forma de especificar modelos; a existencia de máis ferramentas para iso fixo que moitas das empresas que comezaron a traballar con XML adoptasen o uso das DTD. Actualmente o uso destes foi máis restrinxido no seu uso, e comeza a desenvolverse segundo o estándar XML Schema; por iso, a continuación, presentaremos as transformacións que se deben realizar para converter un DTD nun Esquema.

Nun primeiro momento, mostraremos a que elemento XML Schema que elementos dos DTD corresponden, aínda que existen ferramentas de tradución (DTD2HTML en Perl, XMLSpy,...) entre estas dúas linguaxes, a seguinte táboa tenta expresar como funciona para unha mellor comprensión. .

| DTD                                                    | Esquema                           | Comentarios                                                  |
| ------------------------------------------------------ | --------------------------------- | ------------------------------------------------------------ |
| `ELEMENT`                                              | `<element>`                       | Crea unha ligazón entre un nome e atributos, modelos de contido e anotacións. |
| `#PCDATA`                                              |                                   | Soportado como parte de un tipo simple                       |
| `ANY`                                                  | `<any>`                           | Conta con diferentes bromistas para un maior conxunto de posibilidades. Tamén existe `<anyAttribute>`con comodíns similares. |
| `EMPTY`                                                | apoiado                           | Elimínase a existencia de elementos descendentes do actual, a diferenza da presenza dunha cadea baleira nun elemento. |
| modelo de contido                                      | `<complexType>`                   |                                                              |
| Conector de secuencia ( `,`)                           | `<sequence>`                      |                                                              |
| Conector alternativo ( `|`)                            | `<choice>`                        |                                                              |
| Opcional ( `?`)                                        | apoiado                           | Ten que usar os atributos predefinidos de `maxOccurs`e`minOccurs` |
| Obrigatorio e repetible ( `+`)                         | apoiado                           | Ten que usar os atributos predefinidos de `maxOccurs`e`minOccurs` |
| Opcional e repetible ( `*`)                            | apoiado                           | Ten que usar os atributos predefinidos de `maxOccurs`e`minOccurs` |
| `ATTLIST`                                              | `<attributeGroup>`                | As declaracións pódense agrupar `<attributes>`               |
| Tipo de atributo `CDATA`, `ID`, `IDREF`, `NOTATION` ,… | tipos `<simpleType>` predefinidos |                                                              |
| `ENTITY`                                               | Non é compatible                  | As entidades decláranse en declaracións de marcado no XML.   |
| `ENTITY%Parameter`                                     | non soportado                     |                                                              |

## Usando o esquema

Para utilizar o esquema dun documento XML, temos que ter en conta se está no noso sistema de arquivos local ou se é un esquema público.

- No caso de que o esquema estea nun sitio público:

  ```
  <nodo_raiz xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.miempresa.com/mi_esquema.xsd">
  ```

  

- No caso de que o esquema sexa local:

  ```
  <nodo_raiz xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="mi_esquema.xsd">
  ```

  

----

_.ref:_

https://lm-xml-apuntes.readthedocs.io/apuntes/50_parsers_xml.html

https://lm-xml-apuntes.readthedocs.io/apuntes/30_dtds.html