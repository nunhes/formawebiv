# XPath

---

**XPath** (*XML Path Language*) é unha linguaxe que permite construír expresións que recorren e procesan un documento XML. A idea é parecida ás [expresións regulares](https://es.wikipedia.org/wiki/Expresións_regulares) para seleccionar partes dun texto sin atributos (*plain text*). XPath permite buscar e seleccionar tendo en conta a estrutura xerárquica da XML. XPath foi creado para o seu uso no estándar [XSLT](https://es.wikipedia.org/wiki/XSLT), no que se usa para seleccionar e examinar a estrutura do documento de entrada da transformación. XPath foi definido polo consorcio [W3C](https://es.wikipedia.org/wiki/W3C).

Daquela, XPath é a linguaxe utilizada para navegar por documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/). Permite localizar calquera nodo na estrutura de arbore XML, dende o elemento raíz ata a última ramificación do mesmo. Coas funcións adicionais da versión actualizada XPath 2.0 pode satisfacer case tódolos escenarios e consultas.



----

## Introdución á técnica de acceso a estruturas XML

[XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) é unha linguaxe de acceso a documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/) e forma parte da especificación XSL. Permite navegar por documentos XML e acceder a determinadas partes do mesmo. A demais, XPath dispón dunha biblioteca de funcións coa que é posible realizar distintas operacións. Aquí nos limitaremos ás funcións que máis usadas. 

<small>*Para a comprobación de expresións XPath se recomenda o programa online gratuíto [XPath tester](http://www.xpathtester.com/). As expresións XPath poden ser bastante complexas na práctica, o que as fai propensas a erros. Na maioría dos casos, estes erros fan que non se atope o destino e non se xere un resultado, ou ben non se xere o resultado correcto. En *XPath tester* se amosa o resultado de expresións XPath en documentos XML, o que permite comprobar si se xera o resultado esperado.*</small>

### Indicacións para a comprobación con *XPath tester*

 Visita a páxina web [www.xpathtester.com](http://www.xpathtester.com/).

- Copie o contido de ``Europa.xml`` na xanela XML.
- Introduce no eido de entrada XPath a expresión XPath desexada, por exemplo, ``//habitantes``. ![XPath tester](C:\laragon\www\uf2217\assets\xpathtester1.png)

- Fai clic no botón ``Test!``. O resultado da selección aparecerá na xanela XML:

  ![XPath tester](C:\laragon\www\uf2217\assets\xpathtester2.png)

## Tipos de nodos

As partes dun documento [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/) se denominan **nodos**. Existen 7 tipos de nodos diferentes:

- **Raíz**: O nodo raíz o nodo documento (root node) no debe confundirse có elemento raíz. Este é máis ben o nodo padre virtual do elemento raíz.
- **Elemento** (element node)
- **Atributo** (attribute node)
- **Texto** (text node)
- **Espazo de nomes** (namespace node)
- **Instrución de procesamento** (processing instruction node)
- **Comentario** (comment node)

Cada un destes nodos pode ser seleccionado con [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) para o seu procesamento posterior en XSL.

## Os eixos

A navegación dentro dun documento XML a través de XPath ten lugar desde un nodo de contexto, que nas seguintes imaxes se representa como ``SELF``. O nodo de contexto é sempre o punto de partida no que se atopa o procesador [XSLT](https://www.data2type.de/es/xml-xslt-xslfo/xslt/). Os nomes dos eixos definen as relacións de parentesco respecto ao mesmo. Nas imaxes se amosan 11 dos 13 eixos dispoñibles. Xunto aos eixos que presentamos a continuación, que permiten a navegación nun documento, é posible seleccionar atributos dun nodo ou nodos do espazo de nomes a través dos eixos *attribute* ou *namespace*.

O eixe ``self`` contén o nodo de contexto.![nodo actual](C:\laragon\www\uf2217\assets\XPath_img_3.jpg)

O eixo ``child`` contén os nodos fillo do nodo de contexto.

![fillos](C:\laragon\www\uf2217\assets\XPath_img_4.jpg)



O eixo ``descendant`` contén os descendentes do nodo de contexto.



[![descendientes](C:\laragon\www\uf2217\assets\XPath_img_5.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_5.jpg)



O eixo ``descendant-or-self`` contén o nodo de contexto e seus descendentes.



[![nodo de contexto e descendientes](C:\laragon\www\uf2217\assets\XPath_img_6.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_6.jpg)



O eixo ``parent`` contén o pai do nodo de contexto.



[![padre](C:\laragon\www\uf2217\assets\XPath_img_7.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_7.jpg)



O eixo ``ancestor`` contén os ancestros do nodo de contexto.



[![ancestros](C:\laragon\www\uf2217\assets\XPath_img_8.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_8.jpg)



O eixo ``ancestor-or-self`` contén o nodo de contexto e seus descendentes.



[![nodo de contexto e ancestros](C:\laragon\www\uf2217\assets\XPath_img_9.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_9.jpg)



O eixo ``preceding`` contén tódolos nodos que aparecen antes do nodo de contexto, excluíndo os ancestros. O eixo ``following`` contén tódolos nodos que aparecen despois do nodo de contexto, excluíndo os descendentes.



[![nodos anteriores sin ancestros](C:\laragon\www\uf2217\assets\XPath_img_10.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_10.jpg)



O eixo ``preceding-sibling`` contén os irmáns precedentes do nodo de contexto. O eixo ``following-sibling`` contén os irmáns situados detrás do nodo de contexto.



[![irmáns anteriores/posteriores](C:\laragon\www\uf2217\assets\XPath_img_11.jpg)](https://www.data2type.de/fileadmin/images/XPath_img_11.jpg)



## Localización

A localización é a expresión que permite ao procesador seleccionar nodos o un conxunto de nodos. Esta localización se conoce como camino o ruta de localización e pode presentar diversas formas:

- con sintaxe abreviada o completa
- como ruta de localización relativa o absoluta.

### Sintaxe abreviada ou completa

En [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) existen dúas formas de sintaxe, que na práctica se poden utilizar de maneira combinada. A sintaxe abreviada se usa normalmente cando se trata de nodos e eixos que son seleccionados con  moita frecuencia, mentres que a sintaxe completa se utiliza en caso de nodos e eixos a os que se accede con menor frecuencia. Nos seguintes apartados se utilizará a sintaxe completa, recorrendo á sintaxe abreviada cando se trate de expresións máis frecuentes.

**Un exemplo de sintaxe completa:**

```markup
/child::libro/child::autor/child::nombre/attribut::apellido
```

**En sintaxe abreviada:**

```markup
/libro/autor/nombre/@apellido
```

Na sintaxe abreviada se prescinde do nome do eixo child:: e o atributo se introduce antepoñendo o carácter @. Nos próximos exemplos se ofrecerán máis detalles sobre a sintaxe abreviada.

#### Equivalencias entre sintaxe completa e abreviada

| Sintaxis completa           | Sintaxis abreviada               |
| --------------------------- | -------------------------------- |
| child::                     | Eje por defecto. Se pode omitir. |
| attribute::                 | @                                |
| descendant-or-self::node()/ | //                               |
| self::node()                | .                                |
| parent::node()              | ..                               |

### Rutas relativas e absolutas

A ruta de localización XPath pode ser relativa o absoluta. Una ruta absoluta comeza polo nodo raíz, que é o nodo situado directamente sobre o elemento raíz. Esta distinción é necesaria, xa que desde o elemento raíz no sería posible acceder, por exemplo, a comentarios o instrucións que se atopan fora do mesmo.
As rutas de localización constan de pasos de localización separados por /.

Un exemplo:

```markup
/child::Europa/child::pais/child::nombre
```

Neste caso se trata dunha ruta absoluta que parte do nodo raíz. O nodo raíz se indica mediante unha barra diagonal. Desde aí se selecciona o elemento raíz <Europa>. A expresión xerará un resultado si o elemento raíz ten un nodo fillo <pais> e este a súa vez contén un nodo fillo <nombre>. Os eixos se definen mediante o nome do eixo seguido de dous signos de dous puntos. No caso do eixo ``child``, pode omitirse a expresión ``child::``. Así, a ruta de localización ``Europa/pais/nombre`` equivale á ruta do exemplo con sintaxe abreviada. Polo contrario, as rutas de localización relativas necesitan un nodo de contexto. A ruta avaliarase desde esta posición.

**Exemplo:**

```markup
child::pais/child::nombre
```

De igual forma que na ruta absoluta, en este caso se generará un resultado si o nodo de contexto ten un nodo fillo <pais>, que a su vez posee un nodo fillo <nombre>.

A descripción aquí presentada das rutas relativas é incompleta. Poderá atopar máis información sobre rutas relativas en literatura especializada sobre XPath.

### Exemplos de XPath no contexto dunha folla de estilo XSLT

**O exemplo: ``Europa.xml``**

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

A continuación se amosa un exemplo de [XSLT](https://www.data2type.de/es/xml-xslt-xslfo/xslt/) con expresións XPath:

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

(1) O carácter / indica o nodo raíz.

(2) O elemento <xsl:template> se refire ao elemento raíz ``<Europa>``. Nos seguintes elementos <xsl:if> se trata en cada caso do nodo de contexto. Isto significa que todas as rutas de localización seguintes partirán desde este punto. No primeiro exemplo a condición son os pasos de localización ``pais/nombre``. Posto que existe un nodo fillo de ``<Europa>`` có elemento ``<pais>``, que a súa vez posúe un nodo fillo có elemento ``<nombre>``, se copiará o contido de <xsl:if> no resultado. No resultado xerado aparecerá a ruta absoluta ``/Europa/pais/nombre``.

(3) Outro exemplo que mostra a posición do nodo de contexto.

(4) Outro exemplo que mostra a posición do nodo de contexto.

(5) Neste caso no se xerará ningún resultado, xa que, partindo do nodo de contexto ``<Europa>``, non existe ningún nodo fillo có elemento ``<habitantes>``. Nesta expresión houbera sido suficiente escribir "``habitantes``", que se correspondería coa sintaxe abreviada de "``child::habitantes``".

(6) Aquí se xera de novo un resultado, xa que o elemento ``<Europa>`` posúe un descendente ``<habitantes>``.

(7) Neste punto o procesador busca nun nodo irmán (``following-sibling::``) un elemento ``<habitantes>`` situado tras o elemento ``<nombre>``. Ambos teñen como padre ao elemento ``<pais>``. Posto que o elemento ``<habitantes>`` está situado tras ``<nombre>``, se xera un resultado.

(8) A través deste patrón de busca se mostra como é posible aumentar a complexidade das expresións. Aquí se busca un elemento ``<pais>`` que é fillo do nodo de contexto ``<Europa>``. O elemento ``<pais>`` terá a súa vez un irmán posterior ``<habitantes>``. Ata aquí a consulta se corresponde coas anteriores, polo que sabemos que se cumpren estas condicións. O elemento ``<habitantes>`` deberá ter a demais un descendente ``<capital>``. Como pode comprobarse no resultado, se cumpren todas as condicións.

(9) A nova plantilla fai que se cambie o nodo de contexto. Os patróns de busca agora terán como nodo contextual o elemento ``<pais>``. Aquí se realiza a consulta, si o elemento ``<pais>`` ten un elemento fillo ``<capital>``.

(10) Aquí se busca o elemento pai ``<Europa>`` do nodo de contexto ``<pais>``.

**A continuación se mostra o resultado obtido:**

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



![Vista do navegador](C:\laragon\www\uf2217\assets\Europa.png)En determinadas composicións tipográficas se desexas sangrar a primeira liña de cada parágrafo, coa excepción das liñas que seguen directamente a os títulos sangrados á esquerda. A primeira das plantillas presentadas a continuación define a composición dos parágrafos en xeral, mentres que a segunda o fai para aqueles parágrafos se atopan directamente tras o encabezamento. O elemento para os parágrafos se denomina ``<para>`` e para os títulos ``<title>``.

```xml
<xsl:template match="para">
   <fo:block text-indent="6mm"><xsl:apply-templates/></fo:block>
</xsl:template>
<xsl:template match="para[preceding-sibling::*[1][self::title]]">
   <fo:block text-indent="0mm"><xsl:apply-templates/></fo:block>
</xsl:template>
```

Ver aquí outros exemplos de rutas:

- ``child::Europa`` devolve os elementos fillo de ``<Europa>``.
- ``child::node()`` devolve os nodos fillo do nodo de contexto.
- ``attribute::unidad`` é a sintaxe completa da expresión abreviada ``@unidad`` e devolve o contido do atributo ``unidad`` do nodo de contexto.
- ``descendant::Europa`` devolve os descendientes do elemento <Europa> .
- ``self::Europa`` devolve o elemento <Europa> en caso de que el mesmo sexa o nodo de contexto.
- ``/ ``  devolve o elemento raíz.
- ``//*/@*``  devolve todos os atributos de todos os elementos.
- ``/child::comment()`` devolve todos os nodos comentario que sexan fillos do nodo raíz.

## Localización de distintos tipos de nodos

Hasta agora falouse sobre todo dos nodos elemento. No obstante, existen outros tipos de nodo que poden ser seleccionados para súa posterior análise e procesamento. A seguinte táboa mostra exemplos de como se realiza esa selección.

| Argumento                              | Resultado                                                    |
| -------------------------------------- | ------------------------------------------------------------ |
| **nombre/text()**                      | No caso de querer acceder ao nodo de texto do elemento nome deberase usar a proba de nodo text(). |
| **direccion/comment()**                | No caso de querer acceder ao nodo de comentario do elemento ``direccion`` deberase usar a proba de nodo ``coment()``. |
| **localidad/processing-instruction()** | No caso de querer acceder ao nodo de instrucción de procesamiento do elemento ``localidad`` deberase usar a proba de nodo ``processing-instruction()``. |
| **dirección/node()**                   | Si se quere acceder a todos os tipos de nodos (con excepción dos atributos) deberase usar a proba de nodo ``node()``. |

## Filtrar conxuntos de nodos a través de predicados

As expresións [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) serven para a selección de nodos nun árbore [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/). Gracias ao filtrado de expresións a través de predicados, é posible usar expresións XPath para seleccionar grupos de nodos que respondan a criterios máis complexos, definindo o acceso a os nodos dunha maneira mucho máis precisa. Os predicados son expresións que devolven un resultado booleano (verdadeiro o falso), de maneira que se pode filtrar de novo o resultado do nodo seleccionado a través da expresión XPath. No caso de que un determinado nodo dentro dun conxunto de nodos se corresponda có predicado da expresión (que se cumpla a condición do mesmo), éste pasará a formar parte do resultado. Polo contrario, si a condición no se cumple, se excluirá o nodo do resultado. De esta forma é posible afinar a busca dentro dun determinado conxunto inicial de nodos a través das restriccións realizadas mediante predicados.

![Filtrar conxuntos de nodos](C:\laragon\www\uf2217\assets\XPath_img_13ES.png)

A expresión ``//direccion`` selecciona todos os nodos elemento "``direccion``" do documento. No segundo paso se reduce esta selección mediante un predicado. Só aqueles elementos que teñan un elemento fillo "``localidad``" e que o valor do mesmo sexa "Stuttgart" permanecerán na selección. Os demais serán excluídos.

É posible, a demais da comparación de cadeas, restrinxir a selección mediante a comparación de outros valores na expresión dun predicado. Por exemplo:

|                                        | Argumento                                          |
| -------------------------------------- | -------------------------------------------------- |
| Comparación de cadea                   | ``direccion[nombre="Pepe López"]``                 |
| Comparación numérica (maior)           | ``disco[@calificacion > 3]``                       |
| Comparación numérica (menor ou igual)  | ``//cancion[@año <= 1990]``                        |
| Combinación de "maior" e "non igual a" | ``disco[@calificacion < 2]/cancion[@año != 2000]`` |

A demais da comparación de valores, é posible establecer a coexistencia de outros elementos como criterio para analizar un conxunto de nodos.

| Argumento                              | Resultado                                                   |
| -------------------------------------- | ----------------------------------------------------------- |
| **/listadedireccións[direccion]**      | Comproba si existe o elemento fillo "dirección".            |
| **/listadedireccións/direccion[@cat]** | Comproba si existe un atributo "cat" dentro de "direccion". |

**Atención:** Un predicado só comproba si a condición é verdadeira o falsa. Se trata dunha conversión implícita a un valor booleano.



## Operadores booleanos en predicados

Os predicados poden conter os operadores booleanos "``and``" e "``or``".

| Argumento                                       | Resultado                                                    |
| ----------------------------------------------- | ------------------------------------------------------------ |
| **//titulo[@estilo="pop" and @calificacion=4]** | Selecciona todos os elementos "``titulo``" que posúan un atributo "``estilo``" có valor "``pop``" e a demais un atributo "``calificacion``" có valor 4. |
| **//titulo[@estilo="pop" or @calificacion> 2]** | Selecciona todos os elementos "``titulo``" que posúan un atributo "``estilo``" có valor "``pop``" ou un atributo "``calificacion``" cun valor maior que 2. |

## Predicados en cascada

A demais do filtrado mediante operadores booleanos, é posible restrinxir a selección mediante unha disposición en serie de predicados. Os predicados en cascada funcionan como unha superposición de filtros. En primeiro lugar se filtra un conxunto de nodos, que será a su vez o conxunto de partida para o segundo predicado, etc.

```markup
//seccion[parrafo][@tipo='advertencia']
```

En primeiro lugar se seleccionan todos os elementos ``seccion``. O primeiro predicado reduce a selección a aqueles elementos que teñan un elemento fillo "``parrafo``". O conxunto resultante se filtra de novo mediante o segundo predicado, de maneira que só quedaran os elementos que teñan un atributo "tipo" có valor "advertencia".



## Unión de conxuntos de nodos

Ata agora se definiron en cada expresión só un conxunto de nodos. No obstante, se dan con frecuencia aplicacións nas que se deben unir varios conxuntos de nodos. No exemplo ofrecido a continuación se selecciónan todos os títulos dentro do estilo pop e todas as compañías discográficas.

```xml
//titulo[@estilo="pop"] | //discografica
```

## Funcións XPath

As funcións ofrecen operacións avanzadas adicionais na consulta de conxuntos de nodos, así como no análise de cadea de nodos de texto e valores de atributos. As funcións [XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) se poden usar en expresións XPath e en predicados, tal como se mostra no seguinte exemplo:

```xml
count(//cancion)
//disco[count(cancion)>10]
```

As funcións poden conter un argumento e devolven sempre un valor. No primeiro exemplo a función "``count``" ten como argumento un conxunto de nodos e devolve como valor de saída un conxunto de nodos.

Exemplos de funcións de conxuntos de nodos:

| Argumento                                             | Resultado                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| **local-name(..)**                                    | Devolve o nome do elemento padre como cadea.                 |
| **//cancion[position()=5] (Sintaxis abreviada [5] )** | Devolve todas as cancións que ocupen a quinta posición en cada disco. |
| **//cancion[position()=last()]**                      | Devolve as cancións que ocupen a última posición en cada disco. |

Exemplos de funcións de cadea:

| Argumento                                | Resultado                                                    |
| ---------------------------------------- | ------------------------------------------------------------ |
| **//disco[string-length(titulo) > 20 ]** | Selecciona todos os discos cun título que teña máis de 20 caracteres. |
| **//disco[starts-with(interprete,'M')]** | Selecciona todos os discos nos que o nome do intérprete comece coa letra "M". |

Un exemplo dunha función moi útil e usada con  moita frecuencia é "not()". Esta función nega unha expresión booleana. A continuación se ofrece un exemplo do emprego desta función:

| Argumento                 | Resultado                                                    |
| ------------------------- | ------------------------------------------------------------ |
| **//disco[not(cancion)]** | Selecciona todos os discos que no teñan un elemento "cancion". |



---

_.ref:_

https://es.wikipedia.org/wiki/XPath

https://www.data2type.de/es/xml-xslt-xslfo/xpath/introduccion-a-xpath/tipos-de-nodos-y-ejes

https://www.data2type.de/es/xml-xslt-xslfo/xpath/introduccion-a-xpath

http://www.sidar.org/recur/desdi/traduc/es/xml/xpath.html

http://www.sidar.org/#goto_a11yhoy