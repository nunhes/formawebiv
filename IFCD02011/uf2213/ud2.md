---
marp: true
code: true
auto-scaling: true
inlineSVG: true
header: 'FORMAWEB IV' 
footer: 'i.berndz 2022'
---
![bg](https://marp.app/assets/hero-background.svg)

#### UF2213
# Introducción as BBDD   &equiv;

---

Unha **base de datos** é *'unha colección de datos interrelacionados, que teñen unha definición e unha descrición compartida e que están estructurados dun xeito particular'*.

##### Unha base de datos a forman:
 - os **datos**,
 - e o **diccionario de datos**.

---

Os **datos** son unha representación de feitos, conceptos ou instruccións.
Dita representación debe ter unha estrutura determinada, apta para a comunicación, a interpretación e a presentación de ditos datos de formas distintas.

Os datos así tratados permiten acceder á información, clasificala,tratála de diferentes maneiras e mantela almacenada e a disposición de quen poida utilizala con distintos cometidos.

---

Os datos se poden clasificar en:
 - **Microdatos**: datos simples, dificiles de descompoñer, como p.ex., un nome, o atributo dun obxecto(cor, prezo, talla, altura,...)
 - **Macrodatos**: son unha aglomeración de datos, coma p.ex. as táboas.

 ---

 ##### O **diccionario de datos** pódese definir coma un conxunto de metadatos que contén datos sobre os datos: unha *metabase* ou unha base datos que describe a outra(s) base(s) de datos.

 ---

 Nun diccionario de datos podemos atopar:
  - Os esquemas externos, conceptuais e internos.
  - As descricións dos rexistros, campos e relacións a cada nivel.
  - Os procedementos de autorización de accesos e validación de datos.
  - As correspondencias externa/conceptual e conceptual/interna
  - Referencias cruzadas
    - proporciona a relación de referencias cruzadas de cada tabla do esquema da base de datos aos seus nomes no sistema e aos nome de obxecto.

---

O diccionario de datos é empregado polo sistema xestor de bases de datos - SGBD- e tamén polos administradores de bases de datos xa que lles facilita o mantemento.

Aos usuarios, programadores e analistas de sistemas, o diccionario de datos lles sirve para coñecer con todo detalle a base de datos.

---

## SXBD/SGDB/DBMS

---

O **sistema xestor de bases de datos** é o software ou conxunto de programs que sirven para xestionar as bases de datos.

As súas funcións principais son:
 - **crear, actualizar, consultar e protexer** as bases de datos.

A creación, mantemento, xestión ou administración da(s) base(s) de datos a desenvolve(n) o(s) administrador(es) de bases de datos, operando o SXBD.


##### O SXBD é un conxunto coordinado de programas, procedementos e linguaxes, que proporciona os medios necesarios para describir, recuperar e manipular os datos incorporados nunha base de datos, ao tempo que asegura a súa confidencialidade e seguridade.

---

As **principais funcións dun SXBD** son:

– Facilitarlle ao administrador a descrición dos elementos de datos que integran a base de datos, a súa estrutura e as relacións que existen entre eles, así coma os controis a efectuar antes de realizar o acceso á base de datos. Esta función se leva a termo por medio de linguaxes de definición de datos (LDD).

– Facilitar a manipulación dos datos, permitindo aos usuarios da base de datos engadir, buscar, suprimir ou modificar os datos contidos nela. Esta función se leva a termo por medio de linguaxes de manipulación de datos (LMD).

### &middot;&middot;&middot;

---

– Protexer a seguridade e confidencialidade da base de datos; por exemplo, controlando o acceso dos usuarios á base de datos mediante un contrasinal e limitando o acceso aos datos mediante un sistema de privilexios.

– Garantir a fiabilidade e integridade dos datos, por ejemplo impedindo a introducción de datas con erros, valores non permitidos, valores incoherentes, relacións inconsistentes, etc.

### &middot;&middot;&middot;

---

– Asegurar a *compartición* dos datos, por exemplo permitindo que varios usuarios poidan utilizar os mesmos datos sen que se produzan problemas durante o acceso simultáneo.

– Facilitar estatísticas sobre a explotación e uso da base de datos, onde se poida observar o seu rendemento.

– Proporcionar un mecanismo que garanta a finalización exitosa de todas as actualizacións, isto é, que sempre que se faga unha transacción esta se realice completamente ou que non se realice ninguna acción.

---

#### Una transacción é 'un conxunto de accións que cambian o contido da bd'.

As transaccións aportan un extra de fiabilidad ás bases de datos. Si temos que realizar unha serie de modificacións nunha base de datos, e estas se deben executar á vez, as transaccións garanten que nunca imos quedar a medio camiño de súa execución.

Aportando asemade a acción "Desfacer".

---

### FERRAMENTAS DO SXBD

---

Un SXBD debe proporcionar as ferramentas que permitan administrar a base de datos de xeito correcto.

Algunhas ferramentas actuaran a nivel externo - as producidas polo administrador da base de datos-, e outras operaran a nivel interno - aquelas que proporciona o distribuidor SXBD-.

---

Algunhas destas ferramentas son:
– ferramentas para importar e exportar datos.
– ferramentas para monitorizar o uso e o funcionamento da bd.
– programas de análise estatístico para examinar o rendemneto e uso da bd.
– ferramentas para reorganización de índices.
– ferramentas para aproveitar o espazo de almacenamento físico e a consolidación do
espacio liberado cando se borra un rexistro e para que poida ser reutilizado cando sexa necesario.

---

Os SXBD xestionan a estructura física dos datos e o seu almacenamento. 
Isto pode provocar que os usuarios cheguen a ver máis datos dos que realmente queren ou necesitan, pois ven a base de datos completa máis a estrutura na que se administran os datos que conten.

Para evitalo, ou alo menos moderar o impacto negativo desta situación, os SXBD proporcionan un mecanismo de **vistas** que
permite que cada usuario teña a súa propia visión da base de datos.

---

### VISTAS

---

 As vistas son *táboas nas que os datos derivan dunha base de datos principal*. Eses datos se obteñen da base de datos para visualizalos dentro dun modelo virtual, pero non hai ningún arquivo almacenado que represente dito modelo.

 As vistas permiten ver a base de datos coma se fora un subconxunto de si mesma, e reduce a complexidade da presentación de datos permitindo que cada usuario vexa só a parte da base de datos que necesita.

 ---

Outras avantaxas das vistas son:

– Proporcionan seguridad, xa que permiten excluir datos para que certos usuarios non os vexan.

– Proporcionan un mecanismo para que os usuarios vexan os datos no formato que desexen.

– Una vista representa unha imaxe consistente e permanente da base de datos, incluso se a base de datos cambia a súa
estrutura.

---
# :eye:

- Non todolos SXDB son iguais ou dispoñen das mesmas ferramentas.
- Cada SGBD está composto por paquetes de software complexos e sofisticados, con miles de líñas de código e unha documentación extensa, que proporcionan un sistema que permite xestionar calquera tipo de información coa maior fiabilidade posible ante cualquera fallo tanto do hardware coma do propio software.

---



## MÓDULOS

---

Aínda que non se deba xeralizar, xa que varían moito dun SXBD a outro, os principais compoñentes dun SXBD son:

– O **SO**: proporciona servizos básicos ao SXBD, que está construido sobre él.

– O **procesador de consultas**: é o componente principal do SXBD. Se encarga de transformar cada consulta nun conxunto de instruccións de baixo nivel dirixidas ao SXBD.

### &middot;&middot;&middot;

---

–O **xestor da base de datos**: é o intermediario entre os programas de aplicación e as consultas dos usuarios, Acepta consultas e examina os esquemas externo e conceptual para determinar qué rexistros son os necesarios trala petición do usuario. Entón ao xestor da base de datos realiza unha chamada ao xestor de
arquivos para executar a petición.

– O **xestor de arquivos**: manexa os arquivos almacenados no disco duro, onde se atopa a base de datos. Este xestor estabrece e manten a lista de estruturas e índices definidos no esquema interno. Si se utilizan arquivos dispersos, chama á función de dispersión para xerar a dirección dos rexistros. Pero o xestor de arquivos non realiza directamente a entrada e salida de datos. O que fau é pasarlle a petición aos métodos de acceso do SO que se encargan de ler ou escribir os datos no buffer do sistema.

### &middot;&middot;&middot;

---

– O **preprocesador do LMQ**: convirte as sentencias do LMD embebidas nos programas de aplicación, en chamadas a funcións estándar escritas na linguaxe anfitrión.
O preprocesador do LMD debe traballar co procesador de consultas para xerar o código apropiado.

–O **compilador do LDD**: convirte as sentencias do LDD nun conxunto de táboas que conteñen metadatos, estas táboas se
almacenan no diccionario de datos.

–O **xestor do diccionario**: controla os accesos ao diccionario de datos e se encarga de mantelo.

:pen: A maioría dos compoñentes dos SXBD teñen acceso ao diccionario de datos.

---

A súa vez o módulo **xestor da base de datos** ten os seus propios módulos. Que son:

– **Control de autorización**: comproba que o usuario ten os permisos necesarios para levar a termo a operación que solicita.

– **Procesador de comandos**: unha vez que o sistema comprobou os permisos do usuario, se lle pasa o control ao procesador de comandos.

– **Control da integridade**: cando unha operación cambia os datos da base de datos, este módulo debe comprobar que a operación a realizar satisface tódalas restriccións de integridade necesarias.

---

– **Optimizador de consultas**: determina a estratexia óptima para a execución das consultas.

– **Xestor de transaccións**: realiza o procesamento das transaccións.

– **Planificador**: é o responsable de asegurar que as operacións que se realizan concurrentemente sobre a base de datos se procesan sin conflictos.

– **Xestor de recuperación**: garante que a base de datos permanece nun estado consistente no caso de que se produza algún fallo.

– **Xestor de buffers**: este módulo é o responsable de transferir os datos entre a memoria principal e os dispositivos de almacenamento secundario. A este módulo tamén se o denomina **xestor de datos**.

---

### LINGUAXES E INTERFACES PARA CADA TIPO DE USUARIO
---

##### Para xestionar e consultar a(s) base(s) de datos, os SXBD inclúen unha serie de linguaxes e interfaces para cada tipo de usuario: administradores da base de datos, deseñadores, programadores de aplicacións e usuarios finais.

---

É habitual que incluan as seguintes:

  – **linguaxe de manipulación de datos** (**LMD**): permite ao usuario acceder aos datos proporcionados polos subesquemas. Dentro das linguaxes de manipulación podemos facer dous grupos:

---

- **linguaxes de implementación**: usados polos programadores para escribir os programas que acceden aos datos, para consultalos ou actualizalos. Soen ser linguaxes de programación convencionais - inda é habitual usar COBOL- ou linguaxes de cuarta xeración. A esta linguaxe se lle denomina '**linguaxe anfitrión**'.

- **linguaxes de consulta**: utilizados principalmente para realizar consultas na base de datos sen necesidade de crear un programa, polo xeral, estas linguaxes tamén admiten manipulación de datos, a demais soén admitir tanto un uso procedural coma non procedural.

- **linguaxe de descrición de datos (LDD)**: permite especificar os subesquemas, o esquema conceptual e o esquema interno da base de datos, e as correspondencias que conlevan.

---

*As linguaxes procedimentais e non procedimentais son os modelos de cálculo na maior parte da programación actual. A principal diferencia entre estes modelos é que mentres as linguaxes procedimentais están dirixidas por comandos as linguaxes non procedimentais está orientados ás funcións*.

*A demais, as linguaxes de programación de procedementos realizan o cálculo como unha secuencia de declaracións que manipulan os datos almacenados ata que se logra o resultado desexado. Pola contra, a linguaxe non procedimental representa os programas como relacións entre expresións matemáticas que se basean en dependencias.*

---

*Por exemplo, un uso procedural sería a utilización das sentencias embebidas dentro da linguaxe anfitrión correspondente, neste caso se lle denomina '**linguaxe hóspede**', este modo só o soén empregar os programadores.*


---


*Un uso non procedural sería mediante sentencias que facilitan as consultas puntuais de forma interactiva, sen necesidade de programar unha solución, este modo soén usalo os usuarios non informáticos.*

---


|   	|  Procedural  |	Non procedural  |
| --- | --- | --- |
| Impulsado  |  Por comandos  |  Por funcións  | 
| Funciona a través de  |  Estado da maquina  |  Funcións  |
| Semántica  |  Bastante complexa  |  Sinxela  |
| Regreso de funcións  |  Só se permiten tipos e valores de datos restrinxidos  |  Calquera tipo de datos ou valor  |
| Linguaxes de programación baseados ​​no modelo  |  C, C ++, ALGOL, FORTRAN, Smalltalk, etc.  |  [LISP](https://gl.wikipedia.org/wiki/Lisp) e ML  |
| Eficiencia global  |  Mellor 	|   Bo   |   
| Tamaño do programa	|  Grande   |  	Pequeno  |

[*Fonte*](https://es.living-in-belgium.com/difference-between-procedural-and-non-procedural-language-41)

---

*As bases de datos relacionais empregan LMD non procedurais, como SQL (Structured Query Language) ou QBE (Query By Example)*.

*As linguaxes procedurais e non procedurais se poden distinguir polo feito de que a linguaxe procedurais fai fincape no procedemento que debe seguirse para completar tarefas específicas. Pola contra, a linguaxe non procedural dirixe a atención cara o cumprimento das tarefas que deben realizarse no canto de cómo se van a realizar*.

---

O SXBD posee un **compilador de LDD** coa función de procesar as sentencias da linguaxe para identificar as descricións dos distintos elementos dos esquemas e almacenar a descrición do esquema no diccionario de datos.

---

Estas linguaxes son:
- Linguaxe para a **descrición de subesquemas** (SDDL, *Subschema Data Description Language*): para especificar a vista particular de cada aplicación ou cada usuario.

- Linguaxe para a **descrición do esquema** (DDL, *Data Description Language*): para definir as características da vista conceptual, detallando entidades, atributos e relacións, sen facer referencia á forma nin ao método de almacenamento. Se poden especificar controis de integridade: regras que deben cumprir os datos introducidos para que sexan considerados válidos.

- Linguaxe para a descrición física de almacenamiento de datos (DSDL, *Data storage Description Language*): para describir o esquema interno, especificando estrutura de almacenamento interno, modos de organización e acceso, optimizar algúns parámetros físicos como espazo en disco ou tempo medio de acceso, etc.

---

##### En moitos SXBD non se manten unha separación dos niveis, polo que o administrador da base de datos e os deseñadores utilizan o mesmo linguaxe para definir os esquemas.

---

## USUARIOS DE BBDD

---

Denominase usuario a toda aquela persoa que usa unha base de datos.

Segundo a súa capacidade de intervención autorizada podemos distinguir:
 - **usuarios informáticos** ou usuarios especialistas en bases de datos. Desenvolvedores, analistas e programadores, e administradores encargados de xerar aplicacións que aproveitan as bases de datos que xestionan ou administran.
 - **usuarios non informáticos** ou usuarios finais que usan as bases de datos para desenvolver o seu traballo cotián pero non teñen porque coñecer como se crean, manteñen e administran. Estes usuarios normalmente dispoñen dunha interface que os desenvolvedores crearon para operar os datos en función dos seus obxectos e información de interese. A eles vai dirixida a programación da base de datos.

 ---