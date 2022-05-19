# XSL

**XSL** son as siglas en inglés de *eXtensible Stylesheet Language* (‘Linguaxe de follas de estilo extensible’), é unha familia de linguaxes desenvoltos polo *[World Wide Web Consortium](https://es.wikipedia.org/wiki/World_Wide_Web_Consortium)* (W3C) que permiten describir como debe ser presentada a información contida nun documento [XML](https://es.wikipedia.org/wiki/XML).

Esta linguaxe consta de tres recomendacións do W3C:

- [XSL Transformations](https://es.wikipedia.org/wiki/XSL_Transformations) (XSLT): permite transformar documentos XML dunha sintaxe a outra.
- [XSL Formatting Objects](https://es.wikipedia.org/wiki/XSL_Formatting_Objects) (XSL-FO): especifica o formato visual co que se quere presentar o documento.
- [XML Path Language](https://es.wikipedia.org/wiki/XPath) (XPath): permite buscar e acceder aos nodos do documento, así como seleccionar partes deste.

## Linguaxes XSL

### [XSL Transformations](https://es.wikipedia.org/wiki/XSL_Transformations)

*XSL Transformations* (XSLT) presenta unha forma de transformar documentos [XML](https://es.wikipedia.org/wiki/XML) en outros e incluso a formatos que non son [XML](https://es.wikipedia.org/wiki/XML) (como [HTML](https://es.wikipedia.org/wiki/HTML)).

Esta transformación se realiza utilizando unha ou varias regras de patrón. Estas regras de patrón, unidas ao documento fonte a transformar, alimentan un procesador de XSLT que realiza as transformacións desexadas e dispón o resultado nun arquivo de saída. Ou coma no caso dunha páxina web, as crea directamente nun dispositivo de presentación, como é o monitor do usuario.

### [XSL Path Language - XPath](https://es.wikipedia.org/wiki/XPath)

*XML Path Language* (XPath) é un linguaxe que permite construír expresións que recorren e procesan un documento XML. A idea é parecida ás [expresións regulares](https://es.wikipedia.org/wiki/Expresiones_regulares) para seleccionar partes dun texto sen formato (*plain text*). XPath permite buscar e seleccionar partes empregando a estrutura xerárquica do XML para chegar a cada unha das ramificacións do documento orixinal de referencia.

XPath foi creado para ser usado no estándar [XSLT](https://es.wikipedia.org/wiki/XSLT) para seleccionar e examinar a estrutura do documento de entrada para transformación. Para iso, un documento XML é procesado por un analizador (ou *parser*), construíndo unha árbore de nodos. Esta árbore comenza co elemento raíz, que se diversifica ao longo dos elementos que colgan del e acaba en nodos *folla*, que conteñen só texto, comentarios, instrucións de proceso ou que poden estar baleiros e só teñen atributos.

### [XSL Formatting Objects](https://es.wikipedia.org/wiki/XSL_Formatting_Objects)

*XSL Formatting Objects* (XSL-FO) é unha linguaxe na que se especifica como se van a formatar os datos dun documento XML para ser presentados en pantalla, papel ou outro medio. Hai que destacar que no documento XSL-FO figuran tanto os datos coma o formato que se lles vai a aplicar.

A unidade básica de traballo nun documento XSL-FO é o ``Formating Object``. Unha unidade básica para presentar (darlle formato) a información. Estes obxectos de formato se refiren a páxinas, parágrafos, táboas, etc.

---

_.ref:_

https://es.wikipedia.org/wiki/Extensible_Stylesheet_Language