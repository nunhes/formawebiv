# XPath

---

**XPath** (*XML Path Language*) é unha linguaxe que permite construír expresións que recorren e procesan un documento XML. A idea é parecida ás [expresións regulares](https://es.wikipedia.org/wiki/Expresiones_regulares) para seleccionar partes dun texto sin atributos (*plain text*). XPath permite buscar e seleccionar tendo en conta a estrutura xerárquica da XML. XPath foi creado para o seu uso no estándar [XSLT](https://es.wikipedia.org/wiki/XSLT), no que se usa para seleccionar e examinar a estrutura do documento de entrada da transformación. XPath foi definido polo consorcio [W3C](https://es.wikipedia.org/wiki/W3C).

Daquela, XPath é a linguaxe utilizada para navegar por documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/). Permite localizar calquera nodo na estrutura de arbore XML, dende o elemento raíz ata a última ramificación do mesmo. Coas funcións adicionais da versión actualizada XPath 2.0 pode satisfacer case tódolos escenarios e consultas.



----

## Introdución á técnica de acceso a estruturas XML

[XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) é unha linguaxe de acceso a documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/) e forma parte da especificación XSL. Permite navegar por documentos XML e acceder a determinadas partes do mesmo. Ademáis, XPath dispón dunha biblioteca de funcións coa que é posible realizar distintas operacións. Aquí nos limitaremos ás funcións que más usadas. 

<small>*Para a comprobación de expresións XPath se recomenda o programa online gratuíto [XPath tester](http://www.xpathtester.com/). As expresións XPath poden ser bastante complexas na práctica, o que as fai propensas a erros. Na maioría dos casos, estes erros fan que non se atope o destino e non se xere un resultado, ou ben non se xere o resultado correcto. En *XPath tester* se amosa o resultado de expresións XPath en documentos XML, o que permite comprobar si se xera o resultado esperado.*</small>

### Indicacións para a comprobación con *XPath tester*

 Visita a páxina web [www.xpathtester.com](http://www.xpathtester.com/).

- Copie o contido de Europa.xml na xamela XML.
- Introduce no eido de entrada XPath a expresión XPath desexada, por exemplo, ``//habitantes``. ![XPath tester](C:\laragon\www\uf2217\assets\xpathtester1.png)

- Fai clic no botón ``Test!``. O resultado da selección aparecerá na xanela XML:

  ![XPath tester](C:\laragon\www\uf2217\assets\xpathtester2.png)

## Tipos de nodos

As partes dun documento [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/) se denominan **nodos**. Existen 7 tipos de nodos diferentes:

- **Raíz**: El nodo raíz o nodo documento (root node) no debe confundirse con el elemento raíz. Éste es más bien el nodo padre virtual do elemento raíz.
- **Elemento** (element node)
- **Atributo** (attribute node)
- **Texto** (text node)
- **Espazo de nomes** (namespace node)
- **Instrución de procesamento** (processing instruction node)
- **Comentario** (comment node)

Cada un destes nodos pode ser seleccionado con [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) para o seu procesamento posterior en XSL.

## Os eixos

A navegación dentro dun documento XML a través de XPath ten lugar desde un nodo de contexto, que nas seguintes imaxes se representan como ``SELF``. O nodo de contexto é sempre o punto de partida no que se atopa o procesador [XSLT](https://www.data2type.de/es/xml-xslt-xslfo/xslt/). Os nomes dos eixos definen as relacións de parentesco respecto ao mesmo. Nas imaxes se amosan 11 dos 13 eixos dispoñibles. Xunto aos eixos que presentamos a continuación, que permiten a navegación nun documento, é posible seleccionar atributos dun nodo ou nodos do espazo de nomes a través dos eixos *attribute* ou *namespace*.

O eixe ``self`` contén o nodo de contexto.

![nodo actual](C:\laragon\www\uf2217\assets\XPath_img_3.jpg)

O eixo ``child`` contén os nodos fillo do nodo de contexto.



[![hijos](C:\laragon\www\uf2217\assets\XPath_img_4.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_4.jpg)



O eixo ``descendant`` contén os descendentes do nodo de contexto.



[![descendientes](C:\laragon\www\uf2217\assets\XPath_img_5.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_5.jpg)



O eixo ``descendant-or-self`` contén o nodo de contexto e seus descendentes.



[![nodo de contexto y descendientes](C:\laragon\www\uf2217\assets\XPath_img_6.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_6.jpg)



O eixo ``parent`` contén o pai do nodo de contexto.



[![padre](C:\laragon\www\uf2217\assets\XPath_img_7.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_7.jpg)



O eixo ``ancestor`` contén os ancestros do nodo de contexto.



[![ancestros](C:\laragon\www\uf2217\assets\XPath_img_8.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_8.jpg)



O eixo ``ancestor-or-self`` contén o nodo de contexto e seus descendentes.



[![nodo de contexto y ancestros](C:\laragon\www\uf2217\assets\XPath_img_9.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_9.jpg)



O eixo ``preceding`` contén tódolos nodos que aparecen antes do nodo de contexto, excluíndo os ancestros. O eixo ``following`` contén tódolos nodos que aparecen despois do nodo de contexto, excluíndo os descendentes.



[![nodos anteriores sin ancestros](C:\laragon\www\uf2217\assets\XPath_img_10.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_10.jpg)



O eixo ``preceding-sibling`` contén os irmáns precedentes do nodo de contexto. O eixo ``following-sibling`` contén os irmáns situados detrás do nodo de contexto.



[![irmáns anteriores/posteriores](C:\laragon\www\uf2217\assets\XPath_img_11.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_11.jpg)



## Localización

La localización es la expresión que permite al procesador seleccionar nodos o un conjunto de nodos. Esta localización se conoce como camino o ruta de localización y puede presentar diversas formas:

- con sintaxis abreviada o completa
- como ruta de localización relativa o absoluta.

### Sintaxis abreviada o completa

En [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) existen dos formas de sintaxis, que en la práctica se pueden utilizar de manera combinada. La sintaxis abreviada se usa normalmente cuando se trata de nodos y ejes que son seleccionados con mucha frecuencia, mientras que la sintaxis completa se utiliza en caso de nodos y ejes a los que se accede con menor frecuencia. En los siguientes apartados se utilizará la sintaxis completa, recurriendo a la sintaxis abreviada cuando se trate de expresiones más frecuentes.

**Un ejemplo de sintaxis completa:**

```markup
/child::libro/child::autor/child::nombre/attribut::apellido
```

**En sintaxis abreviada:**

```markup
/libro/autor/nombre/@apellido
```

En la sintaxis abreviada se prescinde del nombre del eje child:: y el atributo se introduce anteponiendo el carácter @. En los próximos ejemplos se ofrecerán más detalles sobre la sintaxis abreviada.

#### Equivalencias entre sintaxis completa y abreviada

| Sintaxis completa           | Sintaxis abreviada                |
| --------------------------- | --------------------------------- |
| child::                     | Eje por defecto. Se puede omitir. |
| attribute::                 | @                                 |
| descendant-or-self::node()/ | //                                |
| self::node()                | .                                 |
| parent::node()              | ..                                |

### Rutas relativas y absolutas

La ruta de localización XPath puede ser relativa o absoluta. Una ruta absoluta comienza por el nodo raíz, que es el nodo situado directamente sobre el elemento raíz. Esta distinción es necesaria, ya que desde el elemento raíz no sería posible acceder, por ejemplo, a comentarios o instrucciones que se encuentran fuera del mismo.
Las rutas de localización constan de pasos de localización separados por /.

Un ejemplo:

```markup
/child::Europa/child::pais/child::nombre
```

En este caso se trata de una ruta absoluta que parte del nodo raíz. El nodo raíz se indica mediante una barra diagonal. Desde ahí se selecciona el elemento raíz <Europa>. La expresión generará un resultado si el elemento raíz tiene un nodo hijo <pais> y éste a su vez contiene un nodo hijo <nombre>. Los ejes se definen mediante el nombre del eje seguido de dos signos de dos puntos. En el caso del eje child, puede omitirse la expresión child::. Así, la ruta de localización Europa/pais/nombre equivale a la ruta del ejemplo con sintaxis abreviada. Por el contrario, las rutas de localización relativas necesitan un nodo de contexto. La ruta se evaluará desde esta posición.

**Ejemplo:**

```markup
child::pais/child::nombre
```

De igual forma que en la ruta absoluta, en este caso se generará un resultado si el nodo de contexto tiene un nodo hijo <pais>, que a su vez posee un nodo hijo <nombre>.

La descripción aquí presentada de las rutas relativas es incompleta. Podrá encontrar más información sobre rutas relativas en literatura especializada sobre XPath.

### Ejemplos de XPath en el contexto de una hoja de estilo XSLT

**Nuestro ejemplo Europa.xml:**

```markup
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="style.xsl"?>          
<Europa>
    <pais>
        <nombre>Alemania</nombre>
        <habitantes unidad="millones">82.4</habitantes>
        <capital>Berlín</capital>
        <sigla-pais>D</sigla-pais>
        <prefijo>0049</prefijo>
    </pais>
    <pais>
        <nombre>Francia</nombre>
        <habitantes unidad="millones">58.5</habitantes>
        <capital>Paris</capital>
        <sigla-pais>F</sigla-pais>
        <prefijo>0033</prefijo>
     </pais>
     <pais>
        <nombre>España</nombre>
        <habitantes unidad="millones">39.4</habitantes>
        <capital>Madrid</capital>
        <sigla-pais>E</sigla-pais>
        <prefijo>0034</prefijo>
     </pais>
</Europa> 
```

A continuación se muestra un ejemplo de [XSLT](https://www.data2type.de/es/xml-xslt-xslfo/xslt/) con expresiones XPath:

```markup
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
   <xsl:template match="/">                                                (1)
      <html>
         <title></title>
         <body>
            <h3>
                <xsl:apply-templates/>
            </h3>
         </body>
      </html>
   </xsl:template>
   <xsl:template match="Europa">                                           (2)                    
   <xsl:if test="pais/nombre">                                             (2)
    RESULTADO : /Europa/pais/nombre
    <br/>
   </xsl:if>
   <xsl:if test="pais/habitantes">                                         (3)
    RESULTADO : /Europa/pais/habitantes
    <br/>
   </xsl:if>
   <xsl:if test="pais/capital">                                            (4)        
    RESULTADO : /Europa/pais/capital
    <br/>
   </xsl:if>
   <xsl:if test="child::habitantes">                                       (5)
    RESULTADO : /Europa/habitantes
    <br/>
   </xsl:if>
   <xsl:if test="descendant::habitantes">                                  (6)
    RESULTADO : /Europa/descendant::habitantes
    <br/>
   </xsl:if>
   <xsl:if test="pais/nombre/following-sibling::habitantes">               (7)
    RESULTADO : /Europa/pais/nombre/following-sibling::habitantes
    <br/><br/><br/><br/>
   </xsl:if>
   <xsl:if test="pais/nombre/following-sibling::habitantes/                (8)  
    parent::pais/descendant::capital">
    RESULTADO : /Europa/pais/nombre/following-sibling::habitantes/
    parent::pais/descendant::capital
    <br/><br/><br/><br/>
   </xsl:if>
   <xsl:apply-templates/> 
   </xsl:template> 
   <xsl:template match="pais">                                             (9)
   <xsl:if test="capital"> RESULTADO : /Europa/pais/capital                (9)
       <br/>
   </xsl:if> 
   <xsl:if test="parent::Europa"> RESULTADO : /Europa/pais/parent::Europa  (10)
       <br/>
   </xsl:if>
   </xsl:template>
</xsl:stylesheet>
 
```

(1) El carácter / indica el nodo raíz.

(2) El elemento <xsl:template> se refiere al elemento raíz <Europa>. En los siguientes elementos <xsl:if> se trata en cada caso del nodo de contexto. Esto significa que todas las rutas de localización siguientes partirán desde este punto. En el primer ejemplo la condición son los pasos de localización pais/nombre. Puesto que existe un nodo hijo de <Europa> con el elemento <pais>, que a su vez posee un nodo hijo con el elemento <nombre>, se copiará el contenido de <xsl:if> en el resultado. En el resultado generado aparecerá la ruta absoluta /Europa/pais/nombre.

(3) Otro ejemplo que muestra la posición del nodo de contexto.

(4) Otro ejemplo que muestra la posición del nodo de contexto.

(5) En este caso no se generará ningún resultado, ya que, partiendo del nodo de contexto <Europa>, no existe ningún nodo hijo con el elemento <habitantes>. En esta expresión hubiera sido suficiente escribir "habitantes", que se correspondería con la sintaxis abreviada de "child::habitantes".

(6) Aquí se genera de nuevo un resultado, ya que el elemento <Europa> posee un descendiente <habitantes>.

(7) En este punto el procesador busca en un nodo hermano (following-sibling::) un elemento <habitantes> situado tras el elemento <nombre>. Ambos tienen como padre al elemento <pais>. Puesto que el elemento <habitantes> está situado tras <nombre>, se genera un resultado.

(8) A través de este patrón de búsqueda se muestra cómo es posible aumentar la complejidad de las expresiones. Aquí se busca un elemento <pais> que es hijo del nodo de contexto <Europa>. El elemento <pais> tendrá a su vez un hermano posterior <habitantes>. Hasta aquí la consulta se corresponde con las anteriores, por lo que sabemos que se cumplen estas condiciones. El elemento <habitantes> deberá tener además un descendiente <capital>. Como puede comprobarse en el resultado, se cumplen todas las condiciones.

(9) La nueva plantilla hace que se cambie el nodo de contexto. Los patrones de búsqueda ahora tendrán como nodo contextual el elemento <pais>. Aquí se realiza la consulta, si el elemento <pais> tiene un elemento hijo <capital>.

(10) Aquí se busca el elemento padre <Europa> del nodo de contexto <pais>.

**A continuación se muestra el resultado obtenido:**

```markup
<html>
<title></title>
<body>
   <h3> 
       RESULTADO : /Europa/pais/nombre                                         (2)
       <br/> 
       RESULTADO : /Europa/pais/habitantes                                     (3)
       <br/>
       RESULTADO : /Europa/pais/capital                                        (4)
       <br/> 
       RESULTADO : /Europa/descendant::habitantes                              (6)
       <br/> 
       RESULTADO : /Europa/pais/nombre/following-sibling::habitantes           (7)
       <br/><br/><br/><br/> 
       RESULTADO : /Europa/pais/nombre/following-sibling::habitantes/          (8)
       parent::pais/descendant::capital 
       <br/><br/><br/><br/> 
       RESULTADO : /Europa/pais/capital                                        (9)
       <br/> 
       RESULTADO : /Europa/pais/parent::Europa                                 (10)
       <br/> 
       RESULTADO : /Europa/pais/capital                                        (9)
       <br/> 
       RESULTADO : /Europa/pais/parent::Europa                                 (10)
       <br/> 
       RESULTADO : /Europa/pais/capital                                        (9)
       <br/> 
       RESULTADO : /Europa/pais/parent::Europa                                 (10)
       <br/>
  </h3>
</body>
</html>
```



[![Vista del navegador](C:\laragon\www\uf2217\assets\Europa.png)](https://www.data2type.de/fileadmin/images/Europa.png)



En determinadas composiciones tipográficas se desea sangrar la primera línea de cada párrafo, con la exceción de las líneas que siguen directamente a los títulos sangrados a la izquierda. La primera de las plantillas presentadas a continuación define la composición de los párrafos en general, mientras que la segunda lo hace para aquellos párrafos se encuentran directamente tras el encabezamiento. El elemento para los párrafos se denomina <para> y para los títulos <title>.

```markup
<xsl:template match="para">
   <fo:block text-indent="6mm"><xsl:apply-templates/></fo:block>
</xsl:template>
<xsl:template match="para[preceding-sibling::*[1][self::title]]">
   <fo:block text-indent="0mm"><xsl:apply-templates/></fo:block>
</xsl:template>
```

Como apoyo ofrecemos aquí otros ejemplos de rutas:

- child::Europa devuelve los elementos hijo de <Europa>.
- child::node() devuelve los nodos hijo del nodo de contexto.
- attribute::unidad es la sintaxis completa de la expresión abreviada @unidad y devuelve el contenido del atributo unidad del nodo de contexto.
- descendant::Europa devuelve los descendientes del elemento <Europa> .
- self::Europa devuelve el elemento <Europa> en caso de que él mismo sea el nodo de contexto.
- / devuelve el elemento raíz.
- //*/@* devuelve todos los atributos de todos los elementos.
- /child::comment() devuelve todos los nodos comentario que sean hijos del nodo raíz.

## Localización de distintos tipos de nodos

Hasta ahora nos hemos ocupado sobre todo con los nodos elemento. No obstante, existen otros tipos de nodo que pueden ser seleccionados para su posterior análisis y procesamiento. La siguiente tabla muestra ejemplos de cómo se realiza tal selección.

| nombre/text()                      | En caso de que se quiera acceder al nodo de texto del elemento nombre se deberá usar la prueba de nodo text(). |
| ---------------------------------- | ------------------------------------------------------------ |
| direccion/comment()                | En caso de que se quiera acceder al nodo de comentario del elemento direccion se deberá usar la prueba de nodo coment(). |
| localidad/processing-instruction() | En caso de que se quiera acceder al nodo de instrucción de procesamiento del elemento localidad se deberá usar la prueba de nodo processing-instruction(). |
| dirección/node()                   | Si se quiere acceder a todos los tipos de nodos (con excepción de los atributos) se deberá usar la prueba de nodo node(). |

## Filtrar conjuntos de nodos a través de predicados

Las expresiones [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) sirven para la selección de nodos en un árbol [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/). Gracias al filtrado de expresiones a través de predicados, es posible usar expresiones XPath para seleccionar grupos de nodos que respondan a criterios más complejos, definiendo el acceso a los nodos de una manera mucho más precisa. Los predicados son expresiones que devuelven un resultado booleano (verdadero o falso), de manera que se puede filtrar de nuevo el resultado del nodo seleccionado a través de la expresión XPath. En caso de que un determinado nodo dentro de un conjunto de nodos se corresponda con el predicado de la expresión (que se cumpla la condición del mismo), éste pasará a formar parte del resultado. Por el contrario, si la condición no se cumple, se excluirá el nodo del resultado. De esta forma es posible afinar la busqueda dentro de un determinado conjunto inicial de nodos a través de las restricciones realizadas mediante predicados.

![Filtrar conjuntos de nodos](C:\laragon\www\uf2217\assets\XPath_img_13ES.png)

La expresión //direccion selecciona todos los nodos elemento "direccion" del documento. En el segundo paso se reduce esta selección mediante un predicado. Sólo aquellos elementos que tengan un elemento hijo "localidad" y que el valor del mismo sea "Stuttgart" permanecerán en la selección. Los demás serán excluidos.

Es posible, además de la comparación de cadenas, restringir la selección mediante la comparación de otros valores en la expresión de un predicado. Por ejemplo:

| Comparación de cadena                 | direccion[nombre="Pepe López"]                 |
| ------------------------------------- | ---------------------------------------------- |
| Comparación numérica (mayor)          | disco[@calificacion > 3]                       |
| Comparación numérica (menor o igual)  | //cancion[@año <= 1990]                        |
| Combinación de "mayor" y "no igual a" | disco[@calificacion < 2]/cancion[@año != 2000] |

Además de la comparación de valores, es posible establecer la coexistencia de otros elementos como criterio para analizar un conjunto de nodos.

| /listadedirecciones[direccion]      | Comprueba si existe el elemento hijo "dirección".            |
| ----------------------------------- | ------------------------------------------------------------ |
| /listadedirecciones/direccion[@cat] | Comprueba si existe un atributo "cat" dentro de "direccion". |

Atención: Un predicado sólo comprueba si la condición es veradera o falsa. Se trata de una conversión implícita a un valor booleano.



## Operadores booleanos en predicados

Los predicados pueden contener los operadores booleanos "and" y "or".

| //titulo[@estilo="pop" and @calificacion=4] | Selecciona todos los elementos "titulo" que posean un atributo "estilo" con el valor "pop" y además un atributo "calificacion" con el valor 4. |
| ------------------------------------------- | ------------------------------------------------------------ |
| //titulo[@estilo="pop" or @calificacion> 2] | Selecciona todos los elementos "titulo" que posean un atributo "estilo" con el valor "pop" o un atributo "calificacion" cuyo valor sea mayor que 2. |

## Predicados en cascada

Además del filtrado mediante operadores booleanos, es posible restringir la selección mediante una disposición en serie de predicados. Los predicados en cascada funcionan como una superposición de filtros. En primer lugar se filtra un conjunto de nodos, que será a su vez el conjunto de partida para el segundo predicado, etc.

```markup
//seccion[parrafo][@tipo='advertencia']
```

En primer lugar se seleccionan todos los elementos seccion. El primer predicado reduce la selección a aquellos elementos que tengan un elemento hijo "parrafo". El conjunto resultante se filtra de nuevo mediante el segundo predicado, de manera que sólo quedaran los elementos que tengan un atributo "tipo" con el valor "advertencia".



## Unión de conjuntos de nodos

Hasta ahora se ha definido en cada expresión sólo un conjunto de nodos. No obstante, se dan con frecuencia aplicaciones en las que se deben unir varios conjuntos de nodos. En el ejemplo ofrecido a continuación se selecciónan todos los títulos dentro del estilo pop y todas las compañías discográficas.

```markup
//titulo[@estilo="pop"] | //discografica
```

## Funciones XPath

Las funciones ofrecen operaciones avanzadas adicionales en la consulta de conjuntos de nodos, así como en el análisis de cadena de nodos de texto y valores de atributos. Las funciones [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) se pueden usar en expresiones XPath y en predicados, tal como se muestra en el siguiente ejemplo:

```markup
count(//cancion)
//disco[count(cancion)>10]
```

Las funciones pueden contener un argumento y devuelven siempre un valor. En el primer ejemplo la función "count" tiene como argumento un conjunto de nodos y devuelve como valor de salida un conjunto de nodos.

Ejemplos de funciones de conjuntos de nodos:

| local-name(..)                                    | Devuelve el nombre del elemento padre como cadena.           |
| ------------------------------------------------- | ------------------------------------------------------------ |
| //cancion[position()=5] (Sintaxis abreviada [5] ) | Devuelve todas las canciones que ocupen la quinta posición en cada disco. |
| //cancion[position()=last()]                      | Devuelve las canciones que ocupen la última posición en cada disco. |

Ejemplos de funciones de cadena:

| //disco[string-length(titulo) > 20 ] | Selecciona todos los discos cuyo título tenga más de 20 caracteres. |
| ------------------------------------ | ------------------------------------------------------------ |
| //disco[starts-with(interprete,'M')] | Selecciona todos los discos en los que el nombre del intérprete comience con la letra "M". |

Un ejemplo de una función muy útil y usada con mucha frecuencia es "not()". Esta función niega una expresión booleana. A continuación se ofrece un ejemplo del empleo de esta función:

| //disco[not(cancion)] | Selecciona todos los discos que no tengan un elemento "cancion". |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |



---

_.ref:_

https://es.wikipedia.org/wiki/XPath

https://www.data2type.de/es/xml-xslt-xslfo/xpath/introduccion-a-xpath/tipos-de-nodos-y-ejes

https://www.data2type.de/es/xml-xslt-xslfo/xpath/introduccion-a-xpath

http://www.sidar.org/recur/desdi/traduc/es/xml/xpath.html

http://www.sidar.org/#goto_a11yhoy