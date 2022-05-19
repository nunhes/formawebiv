# XSD

**XSD** (*XML Schema Definition*) é unha linguaxe, tamén chamado simplemente ***XML Schema\***, que sirve para definir a estructura dun documento XML, permitindo a súa validación.

Nos seguintes enlaces se pode consultar a *W3C Recommendation* de XSD, na cal está baseada esta introdución a XML Schema:

- [XML Schema Part 0: Primeiro](http://www.w3.org/TR/xmlschema-0/)
- [XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/)
- [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/)

# Validación dun documento XML con XSD (XML Schema)

**EXEMPLO** Se quere almacenar unha lista de marcadores de páxinas web, gardando de cada un deles o seu nome, unha descrición e a súa URL. Para iso, se crepu o seguinte documento XML (**``marcadores.xml``**) asociado ao arquivo **``marcadores.xsd``**:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<marcadores xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="marcadores.xsd">
   <pagina>
      <nombre>Abrirllave</nombre>
      <descripcion>Tutoriales de informática.</descripcion>
      <url>http://www.abrirllave.com/</url>
   </pagina>
   <pagina>
      <nombre>Wikipedia</nombre>
      <descripcion>La enciclopedia libre.</descripcion>
      <url>http://www.wikipedia.org/</url>
   </pagina>
   <pagina>
      <nombre>W3C</nombre>
      <descripcion>World Wide Web Consortium.</descripcion>
      <url>http://www.w3.org/</url>
   </pagina>
</marcadores>
```



- Para vincular un esquema a un documento XML, é obrigatorio que este último faga referencia ao espazo de nomes **http://www.w3.org/2001/XMLSchema-instance**. Para iso, habitualmente se utiliza o prefixo **xsi**.
- O atributo **noNameSchemaLocation** permite referirse a un arquivo coa definición dun esquema que non ten ningún espazo de nomes asociado. Neste caso, dito arquivo é ***"marcadores.xsd"\***.

O esquema XML gardado en **``marcadores.xsd``** e que permita validar o documento XML **``marcadores.xml``** podería ser:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="marcadores">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="pagina" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="nombre" type="xs:string"/>
              <xs:element name="descripcion" type="xs:string"/>
              <xs:element name="url" type="xs:string"/>
             </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

Para estar ben formado, un esquema XML ten que cumprir as mesmas regras de sintaxe que calquera outro documento XML.



Por outra parte, hai que ter en conta que, en todos os esquemas XML, o elemento raíz é "schema". Agora ben, para escribilo, é muy común utilizar o prefixo **xsd** ou **xs**.

Con **xmlns:xs="http://www.w3.org/2001/XMLSchema"** se ha indicado que:

- Os elementos e tipos de datos utilizados no esquema pertenecen ao espazo de nomes **http://www.w3.org/2001/XMLSchema**.
- Ditos elementos e tipos de datos deben levar o prefixo **xs** (**xs:schema**, **xs:element**, **xs:complexType**, **xs:string**...).

Fíxate tamén que:

- Os elementos "marcadores" e "páxina" son de tipo complexo (**complexType**), xa que, conteñen a outros elementos.
- **sequence** indica que os elementos fillo deben aparecer, no documento XML, na mesma orde na que sexan declarados no esquema.
- Os elementos "nome", "descripción" e "url" son de tipo simple (**string** neste caso) e non poden conter a outros elementos.
- Mediante **maxOccurs="unbounded"** se indica que poden aparecer ilimitados elementos "páxina" no documento XML.

| Exercicio                                                    |
| ------------------------------------------------------------ |
| [Validar un documento XML](https://www.abrirllave.com/xsd/ejercicio-validar-un-documento-xml.php) |

## Definición dun espazo de nomes

**EXEMPLO** No seguinte documento XML se definiu un espazo de nomes escribindo **xmlns:mar="http://www.abrirllave.com/marcadores"**:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<mar:marcadores xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.abrirllave.com/marcadores marcadores.xsd"
xmlns:mar="http://www.abrirllave.com/marcadores">
   <mar:pagina>
      <mar:nombre>Abrirllave</mar:nombre>
      <mar:descripcion>Tutoriales de informática.</mar:descripcion>
      <mar:url>http://www.abrirllave.com/</mar:url>
   </mar:pagina>
   <mar:pagina>
      <mar:nombre>Wikipedia</mar:nombre>
      <mar:descripcion>La enciclopedia libre.</mar:descripcion>
      <mar:url>http://www.wikipedia.org/</mar:url>
   </mar:pagina>
   <mar:pagina>
      <mar:nombre>W3C</mar:nombre>
      <mar:descripcion>World Wide Web Consortium.</mar:descripcion>
      <mar:url>http://www.w3.org/</mar:url>
   </mar:pagina>
</mar:marcadores>
```

No atributo **schemaLocation** se poden escribir parellas de valores:

- No primeiro valor de cada parella, hai que facer referencia a un espazo de nomes.
- No segundo valor, tense que indicar a localización dun arquivo onde hai un esquema dese espazo de nomes.

En canto ao arquivo **``marcadores.xsd``**, agora o código podería ser:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="http://www.abrirllave.com/marcadores"
xmlns="http://www.abrirllave.com/marcadores"
elementFormDefault="qualified">
  <xs:element name="marcadores">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="pagina" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="nombre" type="xs:string"/>
              <xs:element name="descripcion" type="xs:string"/>
              <xs:element name="url" type="xs:string"/>
             </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

- No atributo **targetNamespace** se está indicando que os elementos definidos neste esquema ("marcadores", "páxina", "nome", "descripción" e "url"), proveñen do espazo de nomes **http://www.abrirllave.com/marcadores**.
- **xmlns="http://www.abrirllave.com/marcadores"** especifica que este é o espazo de nomes por defecto.
- O atributo **elementFormDefault="qualified"** indica que todos os elementos declarados localmente no esquema teñen que estar cualificados, é dicir, teñen que pertencer a un espazo de nomes. Por esta razón, en **``marcadores.xml``** se escribiu có prefixo **mar**.

## Elementos globais e locais en XSD

Os elementos poden ser globais o locais:

- Os elementos globais son fillos directos do elemento raíz, **<xs:schema>** neste caso. No  exemplo que estamos tratando, só existe un elemento global: **<xs:element name="marcadores">**.
- Os elementos locais son o resto de elementos.

Cando se define un espazo de nomes, os elementos globais teñen que estar cualificados, obrigatoriamente.



## **elementFormDefault="unqualified"**

**EXEMPLO** No suposto de que o valor do atributo **elementFormDefault** fose **"unqualified"**, para que **``marcadores.xml``** fose válido, se podería escribir algo similar a:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<mar:marcadores xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.abrirllave.com/marcadores marcadores.xsd"
xmlns:mar="http://www.abrirllave.com/marcadores">
   <pagina>
      <nombre>Abrirllave</nombre>
      <descripcion>Tutoriales de informática.</descripcion>
      <url>http://www.abrirllave.com/</url>
   </pagina>
   <pagina>
      <nombre>Wikipedia</nombre>
      <descripcion>La enciclopedia libre.</descripcion>
      <url>http://www.wikipedia.org/</url>
   </pagina>
   <pagina>
      <nombre>W3C</nombre>
      <descripcion>World Wide Web Consortium.</descripcion>
      <url>http://www.w3.org/</url>
   </pagina>
</mar:marcadores>
```

- **"unqualified"** é o valor por defecto do atributo **elementFormDefault**.

  

## **elementFormDefault="qualified"**

**EXEMPLO** Si o atributo **elementFormDefault** se definise **"qualified"**, tamén sería válido o seguinte documento XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<marcadores xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.abrirllave.com/marcadores marcadores.xsd"
xmlns="http://www.abrirllave.com/marcadores">
   <pagina>
      <nombre>Abrirllave</nombre>
      <descripcion>Tutoriales de informática.</descripcion>
      <url>http://www.abrirllave.com/</url>
   </pagina>
   <pagina>
      <nombre>Wikipedia</nombre>
      <descripcion>La enciclopedia libre.</descripcion>
      <url>http://www.wikipedia.org/</url>
   </pagina>
   <pagina>
      <nombre>W3C</nombre>
      <descripcion>World Wide Web Consortium.</descripcion>
      <url>http://www.w3.org/</url>
   </pagina>
</marcadores>
```



Agora, ningún elemento leva prefixo, ao igual que o espazo de nomes ao que pertenecen: **xmlns="http://www.abrirllave.com/marcadores"**

## Validación dun sitemap XML

**EXEMPLO** Para validar o arquivo **``sitemap.xml``** que da solución ao exercicio de XML proposto no seguinte enlace:

- [www.abrirllave.com/xml/ejercicio-crear-un-sitemap-xml.php](http://www.abrirllave.com/xml/ejercicio-crear-un-sitemap-xml.php)

Observa que, é necesario engadir o texto resaltado que se mostra a continuación:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd"
xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
   <url>
      <loc>http://www.ejemplos-de-abrirllave.com/</loc>
      <lastmod>2016-09-30</lastmod>
      <priority>0.8</priority>
   </url>
   <url>
      <loc>http://www.ejemplos-de-abrirllave.com/contactar.html</loc>
      <lastmod>2016-09-30</lastmod>
      <priority>0.3</priority>
   </url>
   <url>
      <loc>http://www.ejemplos-de-abrirllave.com/productos/impresora.html</loc>
      <lastmod>2016-09-30</lastmod>
      <priority>0.5</priority>
   </url>
   <url>
      <loc>http://www.ejemplos-de-abrirllave.com/productos/monitor.html</loc>
      <lastmod>2016-09-30</lastmod>
      <priority>0.5</priority>
   </url>
   <url>
      <loc>http://www.ejemplos-de-abrirllave.com/productos/teclado.html</loc>
      <lastmod>2016-09-30</lastmod>
      <priority>0.5</priority>
   </url>
</urlset>
```



Ao visualizar nun navegador o código fonte do arquivo **``sitemap.xsd``** localizado en:

- http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd

Verás algo coma isto na pantalla :

![Código fuente do arquivo sitemap.xsd](https://www.abrirllave.com/xsd/images/codigo-sitemap-xsd.gif)

Ver que, no arquivo **``sitemap.xsd``**, a etiqueta **<xsd:schema>** contén os atributos **xmlns:xsd**, **targetNamespace**, **xmlns** e **elementFormDefault**.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            targetNamespace="http://www.sitemaps.org/schemas/sitemap/0.9"
            xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
            elementFormDefault="qualified">
```

| Exercicios                                                   |
| ------------------------------------------------------------ |
| [Validar un sitemap XML](https://www.abrirllave.com/xsd/ejercicio-validar-un-sitemap-xml.php)<br>[Mensaxe entre personas](https://www.abrirllave.com/xsd/ejercicio-mensaje-entre-personas.php) |

# Elementos simples en XSD (XML Schema)

**Os elementos simples só poden conter texto** (caracteres). Ou dito doutro xeito, os elementos simples non poden conter a outro u outros elementos (fillos), nin tampouco poden ter atributos. Agora ben, o texto contido nun elemento simple, pode ser de diferentes tipos de datos predefinidos en ***W3C XML Schema\*** ou definidos polo usuario (programador).

Os tipos de datos predefinidos poden ser primitivos (**string**, **boolean**, **decimal**...) ou derivados destes (**integer**, **ID**, **IDREF**...). Ver na imaxe onde se pode ver a relación que existe entre todos eles:

![](./assets/w3c-xml-schema-type-hierarchy.gif)

Para definir un elemento simple se pode utilizar a seguinte sintaxis:

```xml
<xs:element name="nome_do_elemento" type="tipo_de_dato"/>
```

**EXEMPLO** Para os seguintes elementos XML:

```xml
<nome>Elsa</nome> <edad>23</edad>
```

Sus definicións poden ser:

```xml
<xs:element name="nome" type="xs:string"/> <xs:element name="edad" type="xs:integer"/>
```

## Tipos de declaración de elementos simples (**fixed**, **default**)

Si se quere indicar que un valor é fixo (**fixed**), se pode escribir, por exemplo:

```xml
<xs:element name="mes" type="xs:string" fixed="agosto"/>
```

Tamén, se pode especificar un valor por defecto (**default**), por exemplo, tecleando:

```xml
<xs:element name="mes" type="xs:string" default="agosto"/>
```

| Exercicios resueltos                                         |
| ------------------------------------------------------------ |
| [Definición de elementos simples](https://www.abrirllave.com/xsd/ejercicio-definicion-de-elementos-simples.php)<br>[Puerta cerrada e ventana abierta](https://www.abrirllave.com/xsd/ejercicio-puerta-cerrada-y-ventana-abierta.php) |

# Atributos en XSD (XML Schema)

Para definir un atributo se pode empregar a seguinte sintaxis:

```xml
<xs:attribute name="nome_del_atributo" type="tipo_de_dato"/>
```

**EXEMPLO** Para o elemento "curso" seguinte, onde aparece o atributo "grupo":

```xml
<curso grupo="B">2</curso>
```

Sus definicións poden ser:

```xml
<xs:element name="curso" type="xs:integer"/> <xs:attribute name="grupo" type="xs:string"/>
```

- Tódolos atributos poden tomar tipos simples por valor.
- Por outra banda, cando un elemento ten alo menos un atributo –como é o caso do elemento "curso" deste exemplo–  se di que dito elemento é complexo.

## Tipos de declaración de atributos (**fixed**, **default**, **optional**, **required**)

Para indicar que o valor dun atributo é fijo (**fixed**), é posible escribir, por exemplo:

```
<xs:attribute name="grupo" type="xs:string" fixed="B"/>
```

Para especificar o valor por defecto (**default**) dun atributo, se pode escribir:

```
<xs:attribute name="grupo" type="xs:string" default="B"/>
```

Para indicar que un atributo é obrigatorio (**required**), se pode indicar:

```
<xs:attribute name="grupo" type="xs:string" use="required"/>
```

Por defecto, si non se indica nada, o atributo será opcional (**optional**).

| Exercicio resolto                                            |
| ------------------------------------------------------------ |
| [Fichas de personas](https://www.abrirllave.com/xsd/ejercicio-fichas-de-personas.php) |

# Restricións (facetas) en XSD (XML Schema)

***XML Schema\*** permite definir restricións aos posibles valores dos tipos de datos. Ditas restricións se poden establecer en diferentes aspectos, chamados facetas.

Ou se se quere, **as facetas permiten definir restricións sobre os posibles valores de atributos ou elementos.** As facetas que se poden empregar son:

| Faceta                | Descrición                                                   |
| --------------------- | ------------------------------------------------------------ |
| **xs:length**         | Especifica unha lonxitude fija.                              |
| **xs:minLength**      | Especifica unha lonxitude mínima.                            |
| **xs:maxLength**      | Especifica unha lonxitude máxima.                            |
| **xs:pattern**        | Especifica un patrón de caracteres admitidos.                |
| **xs:enumeration**    | Especifica unha lista de valores admitidos.                  |
| **xs:whiteSpace**     | Especifica como se debe tratar os posibles espazos en branco, as tabulacións, os saltos de liña e os retornos de carro que poidan aparecer. |
| **xs:maxInclusive**   | Especifica que o valor debe ser menor ou igual que o indicado. |
| **xs:maxExclusive**   | Especifica que o valor debe ser menor que o indicado.        |
| **xs:minExclusive**   | Especifica que o valor debe ser maior que o indicado.        |
| **xs:minInclusive**   | Especifica que o valor debe ser maior ou igual que o indicado. |
| **xs:totalDigits**    | Especifica o número máximo de díxitos que pode ter un número. |
| **xs:fractionDigits** | Especifica o número máximo de decimais que pode ter un número. |

Seguidamente, se amosan algúns exemplos de restricións definidas cunha ou máis facetas:

## **xs:minExclusive** e **xs:maxInclusive**

**EXEMPLO** No seguinte código se define un elemento chamado "mes" coa restrición de que o valor que tome non poida ser menor que 1 nin maior que 12:

```xml
<xs:element name="mes">
   <xs:simpleType>
      <xs:restriction base="xs:integer">
         <xs:minInclusive value="1"/>
         <xs:maxInclusive value="12"/>
      </xs:restriction>
   </xs:simpleType>
</xs:element>
```

- **xs:simpleType** permite definir un tipo simple e especificar as súas restricións.
- **xs:restriction** sirve para definir restricións dun **xs:simpleType** (como se fixo no exemplo). Tamén sirve para definir restricións dun **xs:simpleContent** o dun **xs:complexContent**. Veremos máis adiante estes elementos.
- No atributo **base** se indica o tipo de dato a partir do cal se define a restrición.
- **xs:minInclusive** sirve para especificar que o valor debe ser maior ou igual que o indicado no seu atributo **value**, (neste caso, maior ou igual que 1).
- **xs:maxInclusive** sirve para especificar que o valor debe ser menor ou igual que o indicado no seu atributo **value**, (neste caso, menor ou igual que 12).

Tamén se podería ter escrito:

```xml
<xs:element name="mes" type="numeroMes"/>

<xs:simpleType name="numeroMes">
   <xs:restriction base="xs:integer">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="12"/>
   </xs:restriction>
</xs:simpleType>
```

Facendo isto, o tipo **numeroMes** definido, podería ser utilizado por outros elementos, xa que, non está contido no elemento "mes".

| Exercicios resoltos                                          |
| ------------------------------------------------------------ |
| [Idade entre 0 e 130 años](https://www.abrirllave.com/xsd/ejercicio-edad-entre-0-y-130.php)<br>[Prezos de tres dígitos](https://www.abrirllave.com/xsd/ejercicio-precios-de-tres-digitos.php) |

## **xs:enumeration**

**EXEMPLO** No  seguinte exemplo se define un elemento chamado "color" coa restrición de que os únicos valores admitidos son: **"verde"**, **"amarillo"** e **"rojo"**.

```xml
<xs:element name="color">
   <xs:simpleType>
      <xs:restriction base="xs:string">
         <xs:enumeration value="verde"/>
         <xs:enumeration value="amarillo"/>
         <xs:enumeration value="rojo"/>
      </xs:restriction>
   </xs:simpleType>
</xs:element>
```

- **xs:enumeration** sirve para definir unha lista de valores admitidos.

| Exercicio resolto                                            |
| ------------------------------------------------------------ |
| [Tipo de vehículo](https://www.abrirllave.com/xsd/ejercicio-tipo-de-vehiculo.php) |

## **xs:pattern**

**EXEMPLO** No seguinte exemplo se define un elemento chamado "letra" coa restricción de que o único valor admitido é unha das letras minúsculas da **"a"** á **"z"**:

```xml
<xs:element name="letra">
   <xs:simpleType>
      <xs:restriction base="xs:string">
         <xs:pattern value="[a-z]"/>
      </xs:restriction>
   </xs:simpleType>
</xs:element>
```

- **xs:pattern** sirve para definir un patrón de caracteres admitidos ( neste caso se admite unha única letra minúscula da **"a"** á **"z"**). **O valor do patrón ten que ser unha expresión regular.**

| Ejercicios resueltos                                         |
| ------------------------------------------------------------ |
| [Iniciais de persoas famosas](https://www.abrirllave.com/xsd/ejercicio-iniciales-de-personas-famosas.php)<br>[Iniciais ao revés](https://www.abrirllave.com/xsd/ejercicio-iniciales-al-reves.php)<br>[Respostas admitidas](https://www.abrirllave.com/xsd/ejercicio-respuestas-admitidas.php)<br>[Números e letras](https://www.abrirllave.com/xsd/ejercicio-numeros-y-letras.php)<br>[Escribir expresións regulares](https://www.abrirllave.com/xsd/ejercicio-escribir-expresións-regulares.php)<br>[Letras admitidas](https://www.abrirllave.com/xsd/ejercicio-letras-admitidas.php) |

## **xs:length**

**EXEMPLO** No seguinte exemplo se define un elemento chamado "clave" coa restrición de que o seu valor ten que ser unha cadea de, exactamente, doce caracteres:

```xml
<xs:element name="clave">
    <xs:simpleType>
        <xs:restriction base="xs:string">
        <xs:length value="12"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
```

- **xs:length** sirve para especificar unha lonxitude fixa.

| Ejercicios resueltos                                         |
| ------------------------------------------------------------ |
| [Longitud fija de unha clave](https://www.abrirllave.com/xsd/ejercicio-longitud-fija-de-una-clave.php)<br>[Longitud mínima e máxima de unha clave](https://www.abrirllave.com/xsd/ejercicio-longitud-minima-y-maxima-de-una-clave.php) |

## **xs:whiteSpace**

**EXEMPLO** No  seguinte exemplo se define un elemento chamado "dirección" coa restricción de que os espazos en branco, as tabulacións, os saltos de liña e os retornos de carro que aparezan nel, se deben manter (**preserve**):

```xml
<xs:element name="direccion">
   <xs:simpleType>
      <xs:restriction base="xs:string">
         <xs:whiteSpace value="preserve"/>
      </xs:restriction>
   </xs:simpleType>
</xs:element>
```

- **xs:whiteSpace** sirve para especificar como se debe tratar aos posibles espazos en branco, as tabulacións, os saltos de línea e os retornos de carro que poidan aparecer.

En vez de **preserve** tamén se pode utilizar:

- **replace** para sustituir todas as tabulacións, os saltos de línea e os retornos de carro por espazos en branco.
- **collapse** para, después de reemplazar todas as tabulacións, os saltos de línea e os retornos de carro por espazos en branco, eliminar todos os espazos en branco únicos e sustituir varios espazos en branco seguidos por un único espazo en branco.



# Extensións en XSD (XML Schema)

**xs:extension** sirve para extender un elemento **simpleType** o **complexType**.

## **xs:extension** (**complexContent**)

**EXEMPLO** Dado o seguinte documento XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<fichas xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="fichas.xsd">
   <ficha numero="1">
      <nombre>Eva</nombre>
      <edad>25</edad>
      <ciudad>París</ciudad>
      <pais>Francia</pais>
   </ficha>
   <ficha numero="2">
      <nombre>Giovanni</nombre>
      <edad>26</edad>
      <ciudad>Florencia</ciudad>
      <pais>Italia</pais>
   </ficha>
</fichas>
```

E o arquivo ***"fichas.xsd"\*** que permite validalo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="fichas">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ficha" type="infoPersonaAmpliada"
                    maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>

  <xs:complexType name="infoPersonaAmpliada">
    <xs:complexContent>
      <xs:extension base="infoPersona">
        <xs:sequence>
          <xs:element name="ciudad" type="xs:string"/>
          <xs:element name="pais" type="xs:string"/>
        </xs:sequence>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>

  <xs:complexType name="infoPersona">
    <xs:sequence>
      <xs:element name="nombre" type="xs:string"/>
      <xs:element name="edad" type="edadPersona"/>
    </xs:sequence>
    <xs:attribute name="numero" type="xs:integer"/>
  </xs:complexType>

  <xs:simpleType name="edadPersona">
     <xs:restriction base="xs:integer">
        <xs:minExclusive value="-1"/>
        <xs:maxExclusive value="131"/>
     </xs:restriction>
  </xs:simpleType>

</xs:schema>
```

- Observa que, **infoPersonaAmpliada** se basea en **infoPersona**, engadindolle dous elementos: "ciudad" e "país".
- En canto a **xs:complexContent**, sirve para definir restricións ou extensións a un tipo complexo (**complexType**).

| Exercicio resolto                                            |
| ------------------------------------------------------------ |
| [Información de persona ampliada](https://www.abrirllave.com/xsd/ejercicio-informacion-de-persona-ampliada.php) |

## **xs:extension** (**simpleContent**)

**xs:simpleContent** permite definir restricións ou extensións a elementos que só conteñen datos, é dicir, non conteñen outros elementos.

**EXEMPLO** O seguinte arquivo ***"precios.xsd"\***:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="precios">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="precio" maxOccurs="unbounded">
          <xs:complexType>
            <xs:simpleContent>
              <xs:extension base="xs:decimal">
                <xs:attribute name="moneda" type="xs:string"/>
              </xs:extension>
            </xs:simpleContent>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

Permite validar o seguinte documento XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<precios xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="precios.xsd">
   <precio moneda="Euro">5</precio>
   <precio moneda="Dólar">6.2</precio>
   <precio moneda="Libra esterlina">4.3</precio>
</precios>
```

- Nótese que, utilizando **xs:extension**, ao elemento "precio" se lle incorporou o atributo **moneda**.

| Exercicios resoltos                                          |
| ------------------------------------------------------------ |
| [Prezos de artigos](https://www.abrirllave.com/xsd/ejercicio-precios-de-articulos.php)<br>[Información de ubicacións](https://www.abrirllave.com/xsd/ejercicio-informacion-de-ubicaciones.php)<br>[Colores de muebles](https://www.abrirllave.com/xsd/ejercicio-colores-de-muebles.php) |

# Elementos complexos en XSD (XML Schema)

Un elemento é complexo (**complexType**) cando contén un ou máis elementos e/ou atributos. De entre as posibles combinacións de elementos e/ou atributos que pode conter un elemento complexo (1 elemento e 0 atributos, 1 elemento e 1 atributo, 1 elemento e varios atributos, 0 elementos e 1 atributo...) cabe destacar as seguintes:

- **Un elemento complexo pode estar baleiro**, é dicir, non conter elementos ni texto, pero si ter alo menos un atributo.
- **Un elemento complexo pode ter contido mixto**, é dicir, conter un ou máis elementos, a demais de texto. Por otra parte, podería ter atributos, ou non.

## Elemento baleiro

**EXEMPLO** No  seguinte código definiuse baleiro o elemento "bola", non podendo conter nin outros elementos nin texto. Agora ben, ver que si ten un atributo, chamado **numero**:

```xml
<xs:element name="bola">
  <xs:complexType>
    <xs:attribute name="numero" type="numeroDeBola"/>
  </xs:complexType>
</xs:element>

<xs:simpleType name="numeroDeBola">
   <xs:restriction base="xs:positiveInteger">
      <xs:minInclusive value="1"/>
      <xs:maxExclusive value="90"/>
   </xs:restriction>
</xs:simpleType>
```

- **xs:positiveInteger** indica que o valor do atributo **numero** debe ser un número enteiro maior que cero.

| Exercicio resolto                                            |
| ------------------------------------------------------------ |
| [Números do bingo](https://www.abrirllave.com/xsd/ejercicio-numeros-del-bingo.php) |

## Contido mixto

Fíxate que, no seguinte código se definiu o elemento "persona" de tipo complexo mixto (**mixed="true"**):

```xml
<xs:element name="persona">
  <xs:complexType mixed="true">
    <xs:sequence>
      <xs:element name="nombre" type="xs:string"/>
      <xs:element name="ciudad" type="xs:string"/>
      <xs:element name="edad" type="xs:positiveInteger"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

| Exercicio resolto                                            |
| ------------------------------------------------------------ |
| [Información de personas en contenido mixto](https://www.abrirllave.com/xsd/ejercicio-informacion-de-personas-en-contenido-mixto.php) |



# Indicadores en XSD (XML Schema)

Os indicadores permiten establecer como se van a escribir –ou utilizar– os elementos nun documento XML. Hai sete tipos de indicadores que se poden clasificar en:

- **Indicadores de orde:** secuencia (**sequence**), todo (**all**) e elección (**choice**).
- **Indicadores de ocorrencia:** **maxOccurs** e **minOccurs**.
- **Indicadores de grupo:** de elementos (**group**) e de atributos (**attributeGroup**).

## Indicadores de orde (**xs:sequence**, **xs:all**, **xs:choice**)

Mentres que **xs:sequence** sirve para especificar a orde na que obrigatoriamente deben aparecer os elementos fillo dun elemento, **xs:all** sirve para indicar que ditos elementos poden aparecer en calquera orde.

**EXEMPLO** O seguinte arquivo ***"lugar.xsd"\***:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="lugar">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ciudad">
          <xs:complexType>
            <xs:all>
              <xs:element name="nombre" type="xs:string"/>
              <xs:element name="pais" type="xs:string"/>
            </xs:all>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

Permite validar o seguinte documento XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<lugar xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="lugar.xsd">
   <ciudad>
      <pais>Italia</pais>
      <nombre>Florencia</nombre>
   </ciudad>
</lugar>
```

Por outra parte, **xs:choice** sirve para especificar que só se permite escribir un dos elementos fillo. Por exemplo, neste caso, se podería utilizar para indicar que habería que elixir entre escribir o "nome" ou escribir o "país" da "ciudad", pero non ambos.

## Indicadores de ocurrencia (**maxOccurs**, **minOccurs**)

**maxOccurs** e **minOccurs** permiten establecer, respectivamente, o número máximo e mínimo de veces que pode aparecer un determinado elemento. O valor por defecto para **maxOccurs** e **minOccurs** é 1.

**EXEMPLO** Dado o seguinte documento XML ***"paises.xml"\***:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<paises xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="paises.xsd">
   <pais>
      <nombre>Argentina</nombre>
      <ciudad>Buenos Aires</ciudad>
      <ciudad>Rosario</ciudad>
   </pais>
   <pais>
      <nombre>México</nombre>
      <ciudad>Guadalajara</ciudad>
      <ciudad>Monterrey</ciudad>
      <ciudad>Cancún</ciudad>
      <ciudad>Mérida</ciudad>
      <ciudad>Ciudad de México</ciudad>
   </pais>
   <pais>
      <nombre>Colombia</nombre>
   </pais>
</paises>
```

Considerando que se quere especificar que:

- "país" poida aparecer unha ou ilimitadas veces.
- "nome" teña que escribirse obrigatoriamente, e só unha vez, dentro de "país".
- De cada "país" poidan escribirse de cero a cinco "ciudades".

O código do arquivo ***"paises.xsd"\*** que permita validar ***"paises.xml"\***, podería ser:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="paises">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="pais" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="nombre" type="xs:string"/>
              <xs:element name="ciudad" type="xs:string"
                          minOccurs="0" maxOccurs="5"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## Indicadores de grupo (**xs:group**, **xs:attributeGroup**)

**xs:group** sirve para agrupar un conxunto de declaracións de elementos relacionados.

**EXEMPLO** Dado o seguinte documento XML ***"personas.xml"\***:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<personas xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="personas.xsd">
   <persona>
      <nombre>Eva</nombre>
      <edad>25</edad>
      <pais>Francia</pais>
      <telefono>999888777</telefono>
   </persona>
   <persona>
      <nombre>Giovanni</nombre>
      <edad>26</edad>
      <pais>Italia</pais>
      <telefono>111222333</telefono>
   </persona>
</personas>
```



E o arquivo ***"personas.xsd"\*** que permite validarlo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="personas">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="persona" type="datosDePersona"
                    maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>

  <xs:complexType name="datosDePersona">
    <xs:sequence>
      <xs:group ref="datosBasicos"/>
      <xs:element name="telefono" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>

  <xs:group name="datosBasicos">
    <xs:sequence>
      <xs:element name="nombre" type="xs:string"/>
      <xs:element name="edad" type="xs:positiveInteger"/>
      <xs:element name="pais" type="xs:string"/>
    </xs:sequence>
  </xs:group>

</xs:schema>
```

- Observa que, se definiu o grupo **datosBasicos**, o cal foi incorporado á definición do tipo complexo **datosDePersona**.

Do mesmo xeito, **attributeGroup** sirve para definir un grupo de atributos. Por exemplo, para validar o seguinte documento XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<personas xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="personas.xsd">
   <persona nombre="Eva" edad="25" pais="Francia"/>
   <persona nombre="Giovanni" edad="26" pais="Italia"/>
</personas>
```

Se pode escribir o seguinte código no arquivo ***"personas.xsd"\***:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="personas">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="persona" maxOccurs="unbounded">
          <xs:complexType>
            <xs:attributeGroup ref="datosDePersona"/>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>

  <xs:attributeGroup name="datosDePersona">
    <xs:attribute name="nombre" type="xs:string"/>
    <xs:attribute name="edad" type="xs:positiveInteger"/>
    <xs:attribute name="pais" type="xs:string"/>
  </xs:attributeGroup>

</xs:schema>
```

- Neste caso, se definiu o grupo de atributos **datosDePersona**, o cal foi incorporado á definición do elemento **persona**.

| Exercicios resoltos                                          |
| ------------------------------------------------------------ |
| [Panel de vuelos](https://www.abrirllave.com/xsd/ejercicio-panel-de-vuelos.php)<br>[Factura](https://www.abrirllave.com/xsd/ejercicio-factura.php)<br>[Registro de conexións](https://www.abrirllave.com/xsd/ejercicio-registro-de-conexiones.php)<br>[Personal de departamentos](https://www.abrirllave.com/xsd/ejercicio-personal-de-departamentos.php) |

---

_.ref:_ https://www.abrirllave.com/xsd/validacion-de-un-documento-xml-con-xsd.php


