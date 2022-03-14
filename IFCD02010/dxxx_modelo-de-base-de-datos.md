##### UF1845 ACCESO A DATOS EN APLICACIÓNS WEB NA CONTORNA SERVIDOR

###### LIMIAR

*ref*: *https://ayudaleyprotecciondatos.es/bases-de-datos/*

​	   [Database - Wikipedia](https://en.wikipedia.org/wiki/Database)

###### UD1 MODELOS DE DATOS

# O modelo de base de datos: definición e tipos



Cando falamos de crear unha base de datos, non podemos esquecernos **do modelo de base de datos** ; este concepto determina en moitos casos o tipo de base de datos que imos utilizar. En que consisten os modelos de bases de datos e que tipos existen?

![Modelos de base datos](./assets/01_modelo-base-de-datos.jpg)

[TOC]

## **Que é un modelo de base de datos?** 

Un modelo de base de datos é a **estrutura lóxica que adopta a base de datos, incluíndo as relacións e restricións que determinan como se almacenan, organizan e se accede aos datos**. Así mesmo, un modelo de base de datos tamén define que tipo de operacións se poden realizar cos datos, é dicir, determina tamén como se manipulan os datos e proporciona a base sobre a que se deseñará a linguaxe de consulta. 

En xeral, practicamente tódolos modelos de bases de datos pódense representar a través dun diagrama de base de datos (veremos algúns). 

## **Tipos de modelos de bases de datos** 

Do mesmo xeito que hai diferentes bases ou orixes de datos, polo tanto diferentes tipos de bases de datos, tamén existen diferentes tipos de modelos de bases de datos. A cuestión é logo saber que modelo elixir para a nosa base de datos. Esa elección normalmente vai a depender do sistema de xestión de bases de datos que vaiamos a empregar, xa que debe ser compatible co modelo de datos (normalmente, os [DBMS](https://es.wikipedia.org/wiki/Sistema_de_gesti%C3%B3n_de_bases_de_datos) desenvólvense para empregar un modelo de base de datos en particular, aínda que hainos que son compatibles con varios modelos). 

### **Modelo de base de datos relacional**

O **modelo de base relacional** é un dos máis comúns. Este modelo é o que utilizan as bases de datos relacionais e ordena os datos en táboas (relacións) formadas por filas e columnas. 

Cada columna contén un atributo da entidade (*nome, enderezo, data de nacemento...*); aos atributos dunha relación se lles chama *dominio*. Escollendo un atributo concreto ou unha combinación de varios temos unha chave primaria, á que se pode referenciar noutras táboas, nas que será unha chave externa. 

En cada fila (tupla) se inclúen datos sobre unha instancia específica da entidade (por exemplo, un cliente específico). 

Ademais, o modelo tamén representa o tipo de relacións entre as táboas, que poden ser un-a-un, un-a-moitos ou moitos-a-moitos. 

Podes ver unha estrutura de **modelo de base de datos relacional** na imaxe: 

![Esquema do modelo de base de datos relacional](./assets/02_modelo-base-de-datos.jpg)*Esquema de modelo de base de datos relacional*. 

### **Modelo xerárquico** 

Se imos empregar unha base de datos xerárquica, o modelo de datos que utilizaremos será o xerárquico, que se caracteriza por presentar os datos nunha estrutura de árbore invertida, onde cada rexistro ten un único nodo raíz, do que xorden outros nodos (rexistros); os nodos dun mesmo nivel son nodos pais, cada nodo pai ten o mesmo nodo raíz e pode ter nodos fillos, pero os nodos fillos só poden ter un nodo pai. Actualmente este modelo se usa ben pouco. 

Neste modelo, os rexistros dun mesmo nivel se clasifican nunha orde específica. 

A súa estrutura sería como o seguinte exemplo: 

![Esquema do modelo de base de datos xerárquica](https://ayudaleyprotecciondatos.es/wp-content/uploads/2020/09/Modelo-base-de-datos-jerarquico.png)*Esquema de modelo de base de datos xerárquica.* 

### **Modelo de rede**

O **modelo de rede de base de datos** parte do modelo xerárquico, pero aquí permítense relacións un a moitos ou moitos a moitos entre rexistros vinculados, tendo varios rexistros principais. O modelo constrúese a través de conxuntos de rexistros relacionados; cada un destes conxuntos consta dun rexistro do propietario ou principal e dun ou máis rexistros de membros ou fillos. Ademais, un rexistro pode ser un membro ou un fillo en diferentes conxuntos. Noutras palabras, neste modelo, permítese que os nodos fillos teñan máis dun nodo pai, polo que se poden representar relacións máis complexas. 

Aquí podes ver un exemplo deste [datos de rede ](https://ayudaleyprotecciondatos.es/bases-de-datos/red/). 

![Esquema do modelo de base de datos de rede](https://ayudaleyprotecciondatos.es/wp-content/uploads/2020/09/Modelo-base-de-datos-en-red.png)

*Esquema do modelo de base de datos de rede* 

### **Modelo orientado a obxectos**

O [de base de datos orientada a obxectos ](https://ayudaleyprotecciondatos.es/bases-de-datos/orientas-a-objetos/)define a base de datos como unha colección de obxectos utilizados na programación orientada a obxectos (é dicir, usando linguaxes como C++ ou Java, por exemplo). Este modelo de base de datos tamén usa táboas, pero non se limita a elas e permite almacenar información moi detallada sobre cada obxecto. 

Os obxectos están dotados dun conxunto de características propias, que á súa vez os diferencian de obxectos semellantes. Pódense agrupar obxectos similares nunha clase e cada obxecto da clase é unha instancia. As clases intercambian datos entre si mediante métodos (mensaxes). 

![Esquema do modelo de base de datos orientado a obxectos](https://ayudaleyprotecciondatos.es/wp-content/uploads/2020/09/Modelo-base-de-datos-orientado-a-objetos.png)*Esquema do modelo de base de datos orientado a obxectos* 

### **Modelo relacional obxecto**

O modelo relacional obxecto combina os modelos de base de datos relacional e orientado a obxectos nun modelo híbrido, de xeito que funciona dun xeito similar ao modelo relacional, pero incorpora funcións do modelo orientado a obxectos, como os propios obxectos, clases, etc. etc herdanza e polimorfismo.  Ademais, permite unha mellor escalabilidade e pódese almacenar un gran volume de datos dentro das clases. 

### **Modelo entidade-relación**

O modelo entidade-relación é basicamente o paso previo a un modelo de base de datos relacional, xa que se trata dun diagrama feito a través duns elementos básicos e a súa relación entre eles: 

- Entidades (estes son os obxectos que están representados na base de datos). 
- Atributos (son o contido da entidade, as súas características). Aos atributos asígnaselles unha clave para distinguilos doutros rexistros. 
- Relación (a ligazón que define a dependencia entre varias entidades). 
- Cardinalidade (é a participación entre entidades, que pode ser un-a-un, un-a-moitos ou moitos-a-moitos). 

No diagrama, as entidades represéntanse mediante un rectángulo, as relacións mediante un diamante e os atributos mediante un óvalo. Vémolo nun exemplo: 

![Relación de entidades de base de datos de modelo de esquema](https://ayudaleyprotecciondatos.es/wp-content/uploads/2020/09/Modelo-entidad-relacion.png)Relación de entidades de base de datos de modelo de esquema 

### **Modelo de ficheiro invertido** 

O modelo de ficheiro invertido, tamén chamado índice invertido, contén datos que se usan como claves nunha táboa de busca, os valores da táboa utilízanse como punteiros para a localización de cada instancia. Actualmente utilízase como índice para as bases de datos modernas, xa que son táboas de consulta nas que se introduce un contido mínimo. 

### **Modelo plano**

No modelo de base de datos plana, os datos estrutúranse en dúas dimensións (das cales existe a estrutura plana), na que todos os obxectos dunha columna específica teñen valores do mesmo tipo e todos os obxectos da mesma fila están relacionados. entre si.eles. 

Por exemplo, nunha base de datos que recolle só nome de usuario e contrasinal, cada fila recollerá o nome de usuario e o contrasinal correspondentes a cada usuario. 

Este **modelo de base de datos tabular** é o precursor do modelo relacional. 

![Esquema do modelo de base de datos plana](https://ayudaleyprotecciondatos.es/wp-content/uploads/2020/09/modelo-base-de-datos-plano.png)

*Esquema de modelo de base de datos plana* 

### **Modelo multidimensional**

O modelo de base de datos multidimensional está pensado para a creación de aplicacións específicas OLAP (Procesamento analítico en liña). Este modelo de base de datos pódese visualizar como un cubo de datos no que se representan diferentes dimensións dos datos dispoñibles; as dimensións dos cubos corresponden ás da táboa e o valor almacenado en cada cela é igual ao valor da métrica. 

Este modelo combina o modelo relacional co xerárquico e permite unha extracción selectiva e eficiente de datos. Non obstante, ten un inconveniente, e é que non se pode modificar a súa estrutura, o que obriga a deseñalos dende cero cando hai que facer cambios. 

### **Modelo semiestructurado**

Cando os datos non encaixan no formato de táboas, filas e columnas, senón que se organizan mediante etiquetas coas que se poden agrupar e crear xerarquías (como é o caso dos datos dunha páxina web), estamos a falar de datos de semiestructuración. 

Para computar estes datos nunha base de datos podemos recorrer ao modelo semiestruturado. Neste modelo non hai separación entre datos e esquema e é útil para describir sistemas ou describir interaccións entre bases de datos que non se adhiran ao mesmo esquema. 

### **Modelo de contexto** 

O modelo de contexto pódese utilizar cando se precisa incorporar elementos doutros modelos de bases de datos. Pode adoptar elementos de modelos orientados a obxectos, semiestruturados e de rede. 

### **Modelo asociativo** 

No modelo asociativo, os datos divídense en entidade e asociación, de xeito que unha entidade é todo o que existe de forma independente e unha asociación é algo que só existe en relación a outra cousa. Así, os datos estrutúranse en dous grupos: 

- Elementos, onde cada un ten un identificador único, un nome e un tipo. 
- Ligazóns, onde cada un ten un identificador único e identificadores únicos dunha fonte, verbo ou obxecto. A información almacenada está relacionada coa fonte e cada un dos tres identificadores pode facer referencia a unha ligazón ou a un elemento. 

### **Modelos de bases de datos NoSQL** 

Xa vimos un modelo de bases de datos NoSQL, tamén chamado bases de datos [non relacionais ](https://ayudaleyprotecciondatos.es/bases-de-datos/no-relacional/), o modelo de base de datos orientada a obxectos, pero hai outros: 

- **Modelo gráfico de base de datos** , similar ao modelo de rede, pero máis flexible, xa que permite conectar calquera nodo a calquera outro. 
- **Modelo multivalor** , que nace do modelo relacional, pero no que os atributos poden conter unha lista de datos en lugar dun único punto de datos. 
- **Modelo de documento** , usado para almacenar e xestionar documentos ou datos semiestruturados, en lugar de datos atómicos (como fan as bases de datos relacionais). 

## **Vantaxes e inconvenientes dos modelos de datos** 

Á hora de falar das vantaxes e desvantaxes dos modelos de datos, temos que pensar en cada un dos modelos que vimos, xa que cada un ten unha serie de vantaxes e inconvenientes que debemos ter en conta á hora de elixir que tipo de base de datos iremos. deseñar e crear. Por exemplo, para un **modelo de base de datos para un inventario** podemos querer usar un modelo relacional en lugar dun non relacional. 

Pero en lugar de ir modelo por modelo, imos agrupar as vantaxes e desvantaxes en torno aos modelos de bases de datos SQL (como as relacionais) e os modelos de bases de datos NoSQL (como os orientados a obxectos). 

**Vantaxes dos modelos SQL:** 

- Portabilidade entre plataformas. 
- Madurez. Levan moito tempo e o seu uso é xeneralizado, o que xerou moita información e ferramentas ao seu redor. 
- Atomicidade (se unha operación non cumpre os criterios para ser executada, non se executa). 
- Estándares definidos pola linguaxe SQL, que crea criterios de uniformidade da información. 
- Redacción sinxela que facilita a comprensión das operacións. 

**Desvantaxes do modelo SQL:** 

- Teñen dificultades para medrar cando aumenta o volume de datos a almacenar. 
- Se hai que facer cambios na base de datos, debe modificarse toda a estrutura. 
- Complexidade na instalación, xa que estes modelos están condicionados polo sistema operativo no que deben funcionar. 
- Interface complexa. 
- As funcións pódense implementar dun xeito propietario, o que pode bloquear o provedor. 

**Vantaxes dos modelos NoSQL:** 

- Poden xestionar e manexar grandes volumes de datos, polo que poden usarse para aplicacións de Big Data. 
- Facilita a administración de bases de datos, xa que ten capacidades de distribución de datos e reparación automática. 
- Son versátiles, xa que permiten aumentar o volume de datos, ademais de introducir cambios sen necesidade de modificar a estrutura. 
- Son moi escalables. 
- Son económicos grazas á súa adaptabilidade e flexibilidade. 

**Desvantaxes do modelo SQL:** 

- Pouca madurez e uso minoritario. 
- Algúns destes modelos non teñen atomicidade. 
- O seu uso relativamente recente ten como consecuencia a falta de normalización na lingua que empregan e a falta de información sobre as ferramentas que empregan e as súas características. 
- Moitas destas bases de datos carecen dunha interface gráfica. 

## **Como realizar o modelado de datos?** 

O primeiro paso antes de deseñar unha base de datos é modelar os datos que imos almacenar nela. A modelización de datos pode adoptar diferentes enfoques (conceptual, empresarial, lóxico ou físico) e consiste na realización dunha serie de tarefas previas: 

- Identificar tipos de entidades 
- Identificar atributos 
- Aplicar convencións de nomenclatura 
- identificar relacións 
- Aplicar modelos de modelos de datos 
- Asignar claves 
- Normalizar para reducir a redundancia de datos 
- Desnormalizar para mellorar o rendemento 

___

_.ref: _*https://en.wikipedia.org/wiki/Data_model*

​	   *https://www.tecnologias-informacion.com/modeladodatos.html*

​	   *https://ayudaleyprotecciondatos.es/bases-de-datos/modelos/*

---



###### UD2 SISTEMAS DE XESTIÓN DE BASES DE DATOS (SGBD)

## Sistemas de Xestión de Bases de Datos | Tipos e clasificación

Un sistema de xestión de bases de datos (SGBD ou DBMS, nas súas siglas en inglés) non é máis que un sistema informático de mantemento de datos.

Os usuarios do sistema dispoñen das facilidades para realizar diversos tipos de operacións sobre o devandito sistema, ben para a manipulación dos datos da base de datos ou para a administración da estrutura da base de datos. Os sistemas de xestión de bases de datos (DBMS) clasifícanse segundo as súas estruturas ou tipos de datos.

Hai varios [tipos de bases de datos](https://www.tecnologias-informacion.com/basesdedatos.html) que se poden usar nun mainframe: lista invertida, xerárquica, de rede ou relacional.

Os sistemas de xestión de bases de datos pódense clasificar en función de varios criterios, como o modelo de datos, os números de usuarios e a disposición da base de datos, todos eles descritos a continuación.

## Baseado no modelo de datos

O modelo de datos máis popular actualmente en uso é o modelo de datos relacional. Este modelo admite DBMS populares como Oracle, MS SQL Server, DB2 e MySQL. Outros modelos tradicionais, como os modelos de datos xerárquicos e os modelos de datos de rede, aínda se utilizan na industria principalmente en plataformas mainframe.

Non obstante, non son de uso común debido á súa complexidade. Todos estes coñécense como modelos tradicionais porque precederon ao modelo relacional.

Nos últimos anos introducíronse modelos de datos orientados a obxectos máis novos. Este modelo é un sistema de xestión de bases de datos no que a información se representa en forma de obxectos como se usa na programación orientada a obxectos.

As bases de datos orientadas a obxectos son diferentes das bases de datos relacionais, que están orientadas a táboas. Os sistemas de xestión de bases de datos orientadas a obxectos (OODBMS) combinan as capacidades da base de datos coas capacidades da linguaxe de programación orientada a obxectos.

Os modelos orientados a obxectos non se implementaron como se esperaba, polo que non son moi utilizados. Algúns exemplos de DBMS orientados a obxectos son O2, ObjectStore ou Jasmine.

## Baseado no número de usuarios

Un DBMS pódese clasificar en función do número de usuarios que admite. Pode ser un sistema de base de datos dun só usuario, que admite un usuario á vez, ou un sistema de base de datos multiusuario, que admite varios usuarios ao mesmo tempo.

## Baseado na distribución da base de datos

Existen catro sistemas principais de distribución para os sistemas de bases de datos que, á súa vez, poden utilizarse para clasificar o DBMS.

### Sistemas centralizados

Cun sistema de base de datos centralizado, o DBMS e a base de datos almacénanse nunha única localización que tamén é utilizada por moitos outros sistemas. 

![img](./assets/centralizada.jpeg)

### Sistema de base de datos distribuída

Nun sistema de base de datos distribuída, a base de datos real e o software DBMS distribúense desde varios sitios que están conectados por unha rede de ordenadores, como se mostra na figura.

![img](./assets/distribuida.jpg)

### Sistemas homoxéneos de bases de datos distribuídas

Os sistemas de bases de datos distribuídas homoxéneas usan o mesmo software DBMS de varios sitios. O intercambio de datos entre estes distintos sitios pódese xestionar facilmente. 

### Sistemas de bases de datos distribuídos heteroxéneos

Nun sistema de base de datos distribuído heteroxéneo, diferentes sitios poden usar diferentes programas de DBMS, pero hai un software común adicional para soportar o intercambio de datos entre estes sitios. 

As bases de datos son os cabalos de batalla ocultos dos sistemas informáticos de moitas organizacións, que posúen intelixencia empresarial crítica e realizan centos de miles de transaccións cada día.

En moitos sentidos, a base de datos converteuse nunha mercadoría. Os produtos difiren en prezo, rendemento, facilidade de administración da base de datos e funcionalidade.

Existe unha gran variedade de sistemas de xestión de bases de datos (DBMS), incluíndo paquetes de bases de datos de código aberto e paquetes. Os principais provedores inclúen Fujitsu, Hewlett-Packard, Hitachi, IBM, Microsoft, NCR Teradata, Oracle, Progress, SAS Institute e Sybase.

Os principais provedores de bases de datos en Europa son Oracle, cunha cota de mercado do 40,8%, IBM cun 29,4% e Microsoft cun 14,9%. Isto dá ás tres empresas máis do 85% do mercado, e todas elas gozaron de crecementos de ingresos nos últimos anos.



_.ref:_ *https://www.wikiwand.com/es/Sistema_de_gesti%C3%B3n_de_bases_de_datos*

​		*https://unade.edu.mx/que-es-la-gestion-de-base-de-datos/*

​		[Os xestores de bases de datos máis usados](https://revistadigital.inesem.es/informatica-y-tics/los-gestores-de-bases-de-datos-mas-usados/)

---



###### UD3 LINGUAXES XESTIÓN DE BASES DE DATOS

## Linguaxes de bases de datos
As linguaxes de bases de datos son linguaxes con propósitos especiais, que permiten unha ou máis das seguintes tarefas, ás veces distinguidas como sublinguaxes:

- Linguaxe de control de datos ([Data control language](https://en.wikipedia.org/wiki/Data_control_language) DCL): controla o acceso aos datos;
- Linguaxe de definición de datos ([Data definition language](https://en.wikipedia.org/wiki/Data_definition_language) DDL): define tipos de datos como a creación, modificación ou eliminación de táboas e as relacións entre elas;
- Linguaxe de manipulación de datos ([Data manipulation language](https://en.wikipedia.org/wiki/Data_manipulation_language) DML): realiza tarefas como inserir, actualizar ou eliminar ocorrencias de datos;
- Linguaxe de consulta de datos ([Data query language](https://en.wikipedia.org/wiki/Data_query_language) DQL): permite buscar información e calcular información derivada.



As linguaxes de bases de datos son específicas dun modelo de datos particular. Exemplos destas linguaxes son:

- **SQL** combina os roles de definición de datos, manipulación de datos e consulta nun único idioma. Foi unha das primeiras linguaxes comerciais para o modelo relacional, aínda que se afasta nalgúns aspectos do [modelo relacional descrito por Codd](https://en.wikipedia.org/wiki/Codd%27s_12_rules) (por exemplo, pódense ordenar as filas e columnas dunha táboa). SQL converteuse nun estándar do American National Standards Institute (ANSI) en 1986 e da International Organization for Standardization (ISO) en 1987. Desde entón, os estándares melloráronse regularmente e son compatibles (con distintos graos de conformidade) por todos os principais produtos comerciais. SGBD relacionais.
- **[OQL](https://en.wikipedia.org/wiki/Object_Query_Language)** é un estándar de linguaxe de modelos de obxectos (do Object Data Management Group). Influíu no deseño dalgunhas das linguaxes de consulta máis novas como JDOQL e [EJB QL](https://en.wikipedia.org/wiki/EJB_QL).
- **[XQuery](https://en.wikipedia.org/wiki/XQuery)** é unha linguaxe de consulta XML estándar implementada por sistemas de bases de datos XML como [MarkLogic](https://en.wikipedia.org/wiki/MarkLogic) e [eXist](https://en.wikipedia.org/wiki/EXist), por bases de datos relacionais con capacidade XML como Oracle e DB2, e tamén por procesadores XML en memoria como [Saxon](https://en.wikipedia.org/wiki/Saxon_XSLT).
- **[SQL/XML](https://en.wikipedia.org/wiki/SQL/XML)** combina XQuery con SQL

Unha linguaxe de base de datos tamén pode incorporar características como:

- Configuración específica do DBMS e xestión do motor de almacenamento.
- Cálculos para modificar os resultados da consulta, como o reconto, a suma, a media, a clasificación, a agrupación e a referencia cruzada.
- Aplicación de restricións (por exemplo, nunha base de datos de automóbiles, só se permite un tipo de motor por coche).
- Versión da interface de programación da aplicación da linguaxe de consulta, para comodidade do programador.

_.ref:_ *https://ayudaleyprotecciondatos.es/bases-de-datos/#El_lenguaje_de_las_bases_de_datos_SQL*  &rarr; :eye: Moi interesantes o resto de  **Entradas relacionadas** que se enlazan co artigo!

[*Linguaxes de programación para os administradores de bases de datos*](https://discoverthenew.ituser.es/devops/2021/01/5-lenguajes-de-programacion-que-los-administradores-de-bases-de-datos-deben-aprender)

---



###### UD4 LINGUAXES DE MARCAS DE USO COMÚN NO LADO SERVIDOR

*Intro*: https://www.ionos.es/digitalguide/paginas-web/desarrollo-web/lenguajes-del-lado-servidor-o-del-cliente-diferencias/

_.ref:_ *[Lenguaje de marcado - Wikipedia, la enciclopedia libre](https://es.wikipedia.org/wiki/Lenguaje_de_marcado)*

​       *[Extensible Markup Language - Wikipedia, la enciclopedia libre](https://es.wikipedia.org/wiki/Extensible_Markup_Language)*

