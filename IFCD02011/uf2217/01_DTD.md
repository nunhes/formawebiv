## Que é un DTD?

Un DTD (*Document Type Definition*) é un conxunto de regras sintácticas para definir etiquetas. Indica que etiquetas se poden usar nun documento, en que orden deben aparecer, cales poden aparecer dentro de outras, cales teñen atributos, etc. Toda esta información se garda nun arquivo de texto con extensión `.dtd`.

Non é un documento XML e polo tanto non necesita prólogo, salvo en certos casos especiais.

Crear unha definición do tipo de documento (DTD) é como crear a nosa propia linguaxe de marcado para unha aplicación específica. 

A DTD pode ser parte do documento XML, aínda que soe colocarse aparte para poder ser reutilizado.

Posto que XML é unha linguaxe para definir linguaxes, quen necesite usar XML para intercambio de datos debería definir o seu propio DTD.

Un problema que presentan os DTDs é que non seguen a sintaxe XML, senón que empregan a súa sintaxe propia.

## Definición de elementos 

Os elementos permitidos se especifican con `ELEMENT`, seguido do nome e o tipo de elemento:

```
<!ELEMENT nome_elemento tipo_elemento>
```

Os elementos que se poden aniñar dentro doutros se especifican entre parénteses.

Se van separados por comas exixen que sigan exactamente esa orde:

```
<!ELEMENT libro (titulo, autor, capitulo)>
```

Segundo este exemplo, `libro` debe conter un `titulo`, un `autor` e un `capitulo` exactamente e por esa orde.

Si van separados por unha barra vertical `|` non exixen esa orde, e poderán aparecer en calquera posición.

```
<!ELEMENT libro (titulo | autor | capitulo)>
```

Segundo este exemplo, `libro` debe conter ou un `titulo`, ou un `autor` ou un `capitulo` e no en esa orde exactamente.

Si o que necesitamos é que sempre apareza un de cada pero en diferente orden, poríamos:

```
<!ELEMENT libro (titulo | autor | capitulo)+ >
```

Agora con esta modificación si haberá polo menos un elemento de cada e en orde aleatoria.

Incluso poderíamos especificar subelementos, por exemplo:

```
<!ELEMENT libro (titulo, autor, (fotografia|debuxo), capitulo)+ >
```

O tipo menos restritivo é `ANY`. Ao ser un elemento que permite calquera contido, non ten estrutura algunha. O mellor é evitar este tipo de elementos.

```
<!ELEMENT calquera ANY>
```

Para datos de tipo texto, se usa `#PCDATA`. Este dato pode incluso chegar a estar baleiro. Pero non pode conter nin gráficos nin elementos multimedia.

```
<!ELEMENT texto (#PCDATA)>
```

Para elementos baleiros, `EMPTY`. Non teñen contido, só poderían conter información nos seus atributos.

```
<!ELEMENT img EMPTY>
```

Poden utilizarse no documento XML con duas etiquetas:

```
<img src="logotipo.gif"></img>
```

Ou só con unha:

```
<img src="logotipo.gif" />
```

Para opcións alternativas, separar con `|`. Por exemplo:

```xml-dtd
<!ELEMENT sexo (muller | home)>
<!ELEMENT parrafo (#PCDATA | lineas)>
```



Modificadores de número de ocorrencias:

| Modificador | Significado                                                  |
| ----------- | ------------------------------------------------------------ |
| `()`        | Os parénteses sinxelos agrupan subetiquetas, conteñen valores de atributo e claves. |
| `,`         | Partícula “e” (AND). A coma indica a ordenación exacta dos elementos na orde establecida. |
| `|`         | Partícula “ou” (OR). A barra vertical significa que só se pode utilizar un dos elementos propostos. |
| `?`         | Unha vez ou ningunha, `[0,1]`.                               |
| `+`         | Alo menos unha vez, `[1..n]`.                                |
| `*`         | Calquera número de veces ou ningunha, `[0,n]`.               |
| (nada)      | Si aparece só o nome do elemento, exactamente unha vez.      |

Exemplo:

```
<!ELEMENT libro (titulo, autor+, capitulo+, apartados*, CD?)>
```

Un `libro` deberá ter, un `titulo`, un `autor` como mínimo, un `capitulo` como mínimo, pode que haxa ou non `apartados` e por último si hai `CD` haberá un só.

## Definición de atributos

Os atributos permitidos para un elemento se especifican con `ATTLIST` e o nome do elemento seguido dos nomes dos atributos, con un tipo e modificador obrigatorios.

```
<!ATTLIST nome_elemento nome_atributo tipo_atributo modificador>
```



Os tipos de definicións de atributos que podemos atopar son:

- Definición dun atributo de tipo estándar, para calquera valor, ou unha enumeración dos valores permitidos:

  ```
  <!ATTLIST libro ISBN CDATA #REQUIRED>
  ```

  Neste exemplo se define un atributo chamado `ISBN` para o elemento `libro`, sendo este atributo obrigatorio.

- Definición dun atributo de valores enumerados:

  ```
  <!ATTLIST libro portada (foto | debuxo) #REQUIRED>
  ```

  Neste exemplo se define para o elemento ``libro`` o atributo ``portada``, que é obrigatorio e con dous posibles valores.

- Definición de varios atributos nunha soa instrucción:

  ```xml-dtd
  <!ATTLIST
    autor nacionalidade CDATA #IMPLIED
    sexo (home | muller) "muller"
  >
  ```

  

Tipos de datos que pode conter un atributo:

- `CDATA`

  Calquera valor, ou unha enumeración dos valores permitidos.

- `NMTOKEN`

  Para restrinxir o valor a un nome XML válido (é dicir, que empece cunha letra ou guión baixo e conteña só letras, números, guións de subliñado, guións e puntos sen espazos)

- `NMTOKENS`

  Múltiples atributos `NMTOKEN`.

- `ID`

  A demais das restricións que impón `NMTOKEN`, impón que o valor sexa único en todo o documento.`<!ATTLIST libro id ID #REQUIRED> `

- `IDREF`

  Unha referencia a un `ID` declarado en alguna parte do DTD.`<!ATTLIST libro referencia IDREF #REQUIRED> `

- `IDREFS`

  Múltiples `IDREF`.

- `ENTITY`

  Entidade binaria externa. (Fai referencia a un bloque de datos xa especificado).

- `ENTITIES`

  Múltiples `ENTITY` separadas con espazos.

- `NOTATION`

  Notación declarada noutra parte do DTD.

O modificador pode ser:

- `#REQUIRED`

  Para atributos obrigatorios.`<!ATTLIST libro ISBN CDATA #REQUIRED> `

- `#IMPLIED`

  Para atributos opcionais.`<!ATTLIST libro ISBN CDATA #IMPLIED> `

- `#FIXED`

  Para atributos con valores fixos.`<!ATTLIST libro ISBN CDATA #FIXED> `

Tamén pode ser un valor por defecto:

```
<!ATTLIST autor sexo (home | muller) "muller">
```



## Crear o DTD

Para iso creamos un arquivo de texto con extensión `.dtd`.

Vamos describindo cada elemento un a un desde o nodo raíz hasta o último elemento.

## Declaración DOCTYPE

Esta declaración é necesaria no documento XML. Sirve para especificar a que DTD está unido o documento. Sempre debe ir colocado despois do prólogo e antes do nodo raíz.

Aquí temos as tres formas de especificar un DTD:

- `SYSTEM` Se utiliza no caso de DTDs “personais”. Para especificar un arquivo local:

  `<!DOCTYPE nodo_raiz SYSTEM "arquivo.dtd"> `

- `PUBLIC` Se utiliza no caso dunha DTD pública.

  `<!DOCTYPE nodo_raiz PUBLIC "-//OASIS//DTD Libro XML//EN" "../dtds/cap.dtd"> `

Tamén é posible incrustar a DTD internamente no documento XML:

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<!DOCTYPE capitulo
  [<!ELEMENT capitulo (titulo, apartado+)>
   <!ELEMENT titulo (#PCDATA)>
   <!ELEMENT apartado (#PCDATA)>
  ]>
<capitulo>
  <titulo>Introducción</titulo>
  <apartado>Primeros pasos con DTDs.</apartado>
</capitulo>
```

Incluso é posible ter unha DTD interna e outra externa (sabendo que vai prevalecer a interna).

## Entidades

As entidades son unha especie de comodíns que serven para reutilizar información. Xa sexa un texto para mostrar nun documento de xml como para reutilizar código nunha DTD.

### Entidades internas

Se empregan cando vamos a utilizar (unha ou varias veces) certa información. Nese caso en vez de engadila varias veces no documento de XML, se crea unha entidade no DTD, onde se lle asigna a unha especie de “constante” a información e despois no documento xml, chamamos a dita “constante” todas as veces que queiramos.

O primeiro que temos que facer é declarar a entidade no DTD:

```
<!ENTITY nome_entidade "datos">
```

Para chamala desde o documento de XML, poñemos:

```
<elemento> ... &nome_entidade; ... </elemento>
```

Un exemplo sería:

| DTD                       | XML      |
| ------------------------- | -------- |
| ``<!ENTITY amp "&#38;">`` | `&amp;`  |
| `<!ENTITY apos "&#39;">`  | `&apos;` |

Neste caso, onde apareza `&amp;` no arquivo XML, se sustituirá por `&\#38;`.

### Entidades externas

O obxectivo deste tipo de entidade é o mesmo que a anterior. Este tipo é moito máis útil cando a información que se vai a incluír na entidade é moi grande, ou cando a información vai a estar sempre gardada nun arquivo que se irá modificando cada certo tempo sen que isto supoña a modificación do DTD. A información estará gardada nun arquivo de texto ou nun arquivo xml, na DTD asociaremos a entidade a este arquivo.

Para facer referencia a un arquivo de texto en local, poremos:

```xml-dtd
<!ENTITY nome_entidade SYSTEM "datos.txt">
```

Para facer referencia a un arquivo de texto que no está en local, poremos:

```xml
<!ENTITY nome_entidade PUBLIC "datos.txt">
```

No documento XML se invocan as entidades exrernas con:

```xml
&nome_entidade;
```

Por exemplo, para incluir este fragmento de texto:

![Arquivo de texto co contido da LOPD.](https://lm-xml-apuntes.readthedocs.io/_images/01_LeyProteccionDeDatos.png)*<small>Arquivo de texto co contido da LOPD.</small>*

Poríamos no DTD:

```xml-dtd
<!ENTITY lei SYSTEM "LeiProteccionDeDatos.txt>
```



Poñer no documento XML:

```xml
<elemento> ... &lei; ... </elemento>
```



### Entidades parámetro

Este tipo de entidades son totalmente distintas ás dos exemplos anteriores, xa que estas non son para ser chamadas desde o documento XML, senón desde a mesma DTD. É dicir, si hai un anaco de código na DTD que está repetido moitas veces, en vez de escribilo de cada vez, creamos unha entidade parámetro ao principio da DTD e despois la chamámola todas as veces que necesitemos ao longo da mesma DTD.

Se declaran ao principio da DTD da siguiente maneira:

```
<!ENTITY % nome_entidade "datos">
```

Se chaman na mesma DTD, da seguinte maneira:

```
%nome_entidade;
```

Exemplo:

```xml-dtd
<!ENTITY % coches "(FIAT | SEAT | AUDI | CITROEN)*">
<!ELEMENT concesionario (familiares | turismos | deportivos)*>
<!ELEMENT familiares %coches;>
<!ELEMENT turismos %coches;>
<!ELEMENT deportivos %coches;>
```



------

https://lm-xml-apuntes.readthedocs.io/apuntes/40_esquemas_xml.html

https://lm-xml-apuntes.readthedocs.io/apuntes/20_sintaxis_xml.html