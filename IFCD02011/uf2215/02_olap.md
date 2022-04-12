#### PROGRAMA DE EMPREGO

# FORMAWEB IV

|                       |                                                              |
| --------------------- | ------------------------------------------------------------ |
| **CURSO:**            | PROGRAMA DE EMPREGO<br>FORMAWEB IV                           |
| **MÓDULO**            | MF0966_3. Consulta e manipulación de información contida en xestores de datos |
| **UNIDADE FORMATIVA** | UF2215: Ferramentas dos SXBD. Pasarelas e medios de conexión.             |
| **NºEXP:**            | 36/00004/2021                                                |


[TOC]

## Introdución a OLAP

OLAP significa basicamente Procesamento analítico en liña, o que significa que se pode usar para extraer ou recuperar datos de forma selectiva para poder analizalos desde diferentes puntos de vista. É de gran valor en [Business Intelligence](https://www-educba-com.translate.goog/what-is-business-intelligence/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) e pódese usar na análise de previsións de vendas, informes financeiros.

**Exemplo:**

Un exemplo disto pode ser que se lle solicite ao usuario datos e análise deses datos do número de balóns de fútbol vendidos nunha determinada rexión, digamos Jharkhand no mes de setembro e comparar o mesmo co número de balóns de fútbol vendidos no mes de maio e poden ver unha comparación doutros artigos deportivos vendidos en Jharkhand para o mesmo mes.

### Como funciona OLAP?

OLAP funciona extraendo datos de varias fontes e almacenando os [mesmos en almacéns de datos](https://www-educba-com.translate.goog/what-is-data-warehouse/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) desde onde se limpa e despois se almacenan en cubos OLAP e o usuario obtén os datos dos cubos OLAP contra as consultas executadas por el. O novo termo aquí é cubos OLAP. Nos cubos, os datos clasifícanse en dimensións (rexión xeográfica, período de tempo) derivadas das dimensións dos almacéns de datos que son cubertos por membros (nome, identificación), etc.

## Visión xeral de OLAP

Os distintos tipos de procesamento analítico en liña (OLAP) pódense describir con tres grandes categorías, que se distinguen en función da técnica utilizada para a ordenación e almacenamento dos datos e elementos relacionados na base de datos, é dicir, relacional, multidimensional ou híbrido. (Combinación tanto relacional como multidimensional), desde onde os datos poden ser recuperados e implicados en cálculos analíticos compostos, xeración de informes, selección de datos, exame preditivo e exploración estatística, etc.

Cada organización e empresario nestes días necesitan datos para tomar decisións. Canto mellores se tomen esas eleccións, máis proveitosa e lucrativa será a organización. Hai información masiva que debe ser almacenada e seguida de forma coherente no día a día. Para xestionar esta crecente información, son necesarias estratexias novas e modernas de análise de rexistros e OLAP serve para ese propósito con precisión. Tamén se chama procesamento analítico en liña para que os clientes realicen unha análise e procesamento rápido e potente de datos de numerosas bases de datos ao mesmo tempo. Ademais, permite aos analistas e xestores extraer e representar información comercial desde varios focos.

Antes de mergullarnos en varios tipos de OLAP, imos comprender rapidamente un par de termos e as súas definicións.

- Os agregados aludiron como información predeterminada. As agregacións normalmente calcúlanse previamente e mantéñense nas táboas agregadas.
- A táboa de dimensións inclúe principalmente campos textuais e descricións.
- A táboa de feitos utilízase para almacenar valores de certeza ou calidades cuantificables.
- Os modos de almacenamento son formas de almacenar fisicamente os datos en cubos e dimensións.

### Tipos de OLAP

Existen diferentes tipos de OLAP baseados nos modos de almacenamento que se utilizan para o descubrimento de datos con cálculos analíticos complexos, visualización de rexistros ilimitada e escenarios preditivos "e se".

#### 1. OLAP multidimensional (MOLAP)

que pode ser coñecido en liñas xerais como o tipo clásico OLAP. Este servidor utiliza unha base de datos multidimensional (MDDB) para almacenar e analizar información. MDDB pode almacenar con habilidade resumos, proporcionando un método para facer preguntas rápidas e recuperar información da base de datos para procesala. O sistema de xestión de bases de datos multidimensional e os usuarios visualizan os datos almacenados como un cubo 3D. Estes bloques de datos gárdanse na memoria chamada CubeCache.

A información móvese desde unha fonte de información [á base de datos multidimensional](https://www-educba.com/multidimensional-database) que se sitúa entre o cliente e o servidor, e despois diso, a base de datos é agregada. MOLAP almacena os resumos de datos en ficheiros binarios e manténos lonxe da base de datos relacional. É imperativo comprender que MOLAP fai ademais unha copia duplicada da información de feitos e dimensións nun ficheiro binario único.

Ofrece indexación rápida para agregacións precalculadas, o que fai que sexa máis rápido para os cálculos. Almacena e traballa de forma eficaz con información numérica.

En todo caso, as limitacións para a utilización de MOLAP incorporan:

Menos versatilidade xa que só pode xestionar unha medida restrinxida de información, a velocidade de MOLAP é máis rápida para índices informativos pequenos ou medios pero normal para índices informativos máis grandes, o almacenamento MOLAP tamén pode incorporar exceso de información.

**Aplicacións MOLAP:** Essbase, Express Server, Yellowfin, Clear Analytics, SAP Business Intelligence

#### 2. ROLAP, Procesamento Analítico Relacional On-Line

O termo ROLAP indica que o servidor OLAP implica almacenamento de natureza relacional. Utilizan un sistema de xestión de bases de datos relacionais para manter e controlar os datos. Estes son os servidores que existen entre a base de datos e o usuario. Os sistemas ROLAP traballan sobre a información que reside nunha base de datos relacional.

ROLAP constrúe vistas indexadas para almacenar os resumos de datos nesas vistas na base de datos relacional. Ademais, deixa tanto, feito como dimensión, a información na táboa relacional.

Os servidores ROLAP admiten grandes cantidades de información que os servidores MOLAP. Supervisa de forma produtiva tanto a información numérica como a textual. Permite aos clientes afondar ata o nivel máis mínimo dunha estrutura de xerarquía

O servidor DSS de Microstrategy adopta o enfoque ROLAP

O principal argumento contra os RDB é que consultar unha base de datos masiva con SQL para obter información adoita producir consultas complexas. Posteriormente, as aplicacións ROLAP mostran un rendemento máis lento e poden non ser perfectas para a realización de determinados cálculos.

#### 3. HOLAP, OLAP híbrido

É unha mestura de MOLAP e ROLAP. Ao utilizar os almacéns de información [ROLAP e MOLAP](https://www-educba.com/rolap-vs-molap) , Hybrid OLAP ofrece as calidades de ambas técnicas. HOLAP almacena resumos de datos nos ficheiros binarios ou nos cubos precalculados. Deixa as cantidades de información de feito e dimensión na base de datos relacional.

O enfoque HOLAP pódese executar habitualmente se existe algunha das circunstancias que o acompañan:

Se hai unha cantidade masiva de datos, se hai conxestión de rendemento nun servidor ou se está a facer uso de fontes de información gardadas que se resumen.

Os servidores HOLAP almacenan información da forma máis funcional posible. O compoñente HOLAP ofrece flexibilidade para deseñar, acceder e manter os grupos de datos HOLAP. [HOLAP](https://www-educba.com/holap) integra almacenamento de información multidimensional e relacional que se pode utilizar para resolver problemas de escalabilidade e rendemento.

Ademais dos tres tipos mencionados anteriormente, que xeralmente se identifican e utilizan, tamén temos un par de tipos máis de OLAP que non son tan frecuentes aínda que sen dúbida merecen a pena referencialos e comprender.

#### 4. WOLAP

Un OLAP web que se coñece como OLAP habilitado para a web utilízase a través do navegador de Internet. Pódese utilizar moi ben no caso de que estea pensando en algo nun plan de gasto realmente mínimo, xa que só require unha conexión web e un navegador de internet para acceder á información. En contraste cos diferentes tipos de OLAP, a funcionalidade e o rendemento de WOLAP están socavados.

#### 5. DOLAP

Desktop On-Line Analytical Processing (DOLAP) é unha tecnoloxía OLAP dun só nivel baseada en escritorio. A funcionalidade é limitada en contraste con outras aplicacións OLAP. Ten un valor máis rendible e é beneficioso para os clientes móbiles que xeralmente non poden conectarse ao almacén de datos.

#### 6. SOLAP

O amplo uso da información xeorreferenciada engadiu a necesidade de actualizar OLAP con ferramentas de análise espacial. Implementáronse dispositivos Spatial OLAP (SOLAP) para abordar problemas no campo da Xeo-Business Intelligence. As ferramentas SOLAP axudan a realizar análises espaciales da información. Estes dispositivos combinan a análise OLAP con marcos SIX para a visualización espacial. Non obstante, hai buscas para mellorar os coñecementos tecnolóxicos para mellorar a optimización de consultas complicadas e visualización de datos.

### Resumo – Tipos de OLAP

É fundamental para nós comprender que tipo de almacenamento OLAP se pode utilizar mellor para facer eleccións de alta calidade cos datos proporcionados. A cantidade de datos analizados convértese nun elemento esencial para decidir o tipo de base de datos OLAP.

En resumo, os produtos OLAP relacionais poden tratar con datos de maior tamaño mellor que os produtos OLAP multidimensionais. Se a cantidade de información non require unha base de datos relacional, un produto multidimensional será igual de útil. No caso de que as necesidades che permitan escoller a mestura de ROLAP e MOLAP, tes HOLAP para vir cara a cal é, sen dúbida, o tipo OLAP máis flexible e potente que hai. Ademais, existen tipos OLAP financeiros como os tipos DOLAP e WOLAP que se usan con limitacións nun ambiente restrinxido. Para a exploración sinxela e rápida da información habitada nunha base de datos espacial, dispoñemos do tipo SOLAP que axudaría a analizar a información existente como imaxes e vectores.

### Clasificación das ferramentas OLAP

Así, as ferramentas OLAP axúdannos a analizar datos multidimensionalmente na [minería de datos](https://www-educba-com.translate.goog/what-is-data-mining/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) . As ferramentas OLAP pódense clasificar como segue:

#### 1. MOLAP

Significa Procesamento analítico en liña multidimensional. Almacena datos en matrices multidimensionais e require un cálculo previo e almacenamento de información no cubo.

Algunhas das ferramentas para iso son:

- **IBM Cognos:** ofrece ferramentas para a elaboración de informes, análise, seguimento de eventos e métricas.
- **SAP NetWeaver BW:** coñécese como SAP NetWeaver Business Warehouse. Do mesmo xeito que IBM Cognos, tamén ofrece informes, análises e interpretación de datos empresariais. Funciona con RDBMS estándar da industria e [DBMS](https://www-educba-com.translate.goog/introduction-to-dbms/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) en memoria HANA de SAP .
- **Microsoft Analysis Services:** as organizacións usan Microsoft Analysis Services para dar sentido aos datos que se espallan en varias bases de datos ou que están distribuídos de forma discreta.
- **MicroStrategy Intelligence Server** : MicroStrategy Intelligence Server axuda á empresa a estandarizarse nunha única plataforma aberta que, a cambio, reducirá o seu custo de mantemento e operación.
- **Servidor Mondrian OLAP:** é unha ferramenta OLAP de código aberto e a súa USP está escrita en Java. Outra característica desta ferramenta é que admite [linguaxe XML](https://www-educba-com.translate.goog/what-is-xml/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) , SQL e outras fontes de datos.
- **Ic Cube:** do mesmo xeito que a ferramenta OLAP anterior, esta tamén está escrita en Java e tamén é unha ferramenta OLAP multidimensional en memoria.
- **Servidor Infor BI OLAP:** é unha base de datos OLAP en tempo real en memoria para análise, planificación e modelado multidimensional. Tamén se usa para a planificación financeira, operativa e informes.
- **Servidor Jedox OLAP** : é un servidor OLAP en memoria multidimensional, orientado a células e máis importante.
- **Opción Oracle Database OLAP:** como o nome indica, esta ferramenta OLAP utilízase para introducir OLAP no entorno de base de datos de Oracle. O principal obxectivo que serve é que poida dirixir as consultas SQL a cubos OLAP que a cambio acelerarán o proceso.
- **Servidor SAS OLAP:** do mesmo xeito que o servidor OLAP IcCube, ofrece unha instalación de almacenamento de datos multidimensional. Este servidor tamén se pode usar para obter acceso rápido a datos resumidos previamente.
- **IBM T1:** este servidor OLAP tamén proporciona almacenamento de datos multidimensional que se representa en cubos OLAP e os cálculos realízanse en tempo real.

#### 2. ROLAP

A "R" en ROLAP significa Relacional. Así, a forma completa de ROLAP pasa a ser Procesamento analítico relacional en liña. A característica salientable de ROLAP é que os datos se almacenan en bases de datos relacionais. Algúns dos principais ROLAP son os seguintes:

1. IBM Cognos
2. SAP NetWeaver BW
3. Servizos de análise de Microsoft
4. Essbase
5. Servidor Jedox OLAP
6. Servidor SAS OLAP
7. Servidor MicroStrategy Intelligence
8. Opción Oracle Database OLAP

#### 3. HOLAP

É a sigla de Procesamento analítico en liña híbrido. Así, HOLAP supera as deficiencias de [MOLAP](https://www-educba-com.translate.goog/molap/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) e ROLAP combinando as súas capacidades. Agora como se combina? Combina datos dividindo os datos da base de datos entre almacenamento relacional e especializado. Algúns dos principais HOLAP son os seguintes:

1. IBM Cognos
2. SAP NetWeaver BW
3. Servidor Mondrian OLAP
4. Servizos de análise de Microsoft
5. Essbase
6. Servidor Jedox OLAP
7. Servidor SAS OLAP
8. Servidor MicroStrategy Intelligence
9. Opción Oracle Database OLAP

Agora imos repasar as vantaxes que teñen as ferramentas OLAP no dominio da Business Intelligence.

### Vantaxes das ferramentas OLAP

- Axúdanos a analizar e modificar informes a un ritmo moito máis rápido xa que os datos úsanse desde a memoria desde [cubos de datos](https://www-educba-com.translate.goog/what-is-data-cube/?_x_tr_sl=auto&_x_tr_tl=gl&_x_tr_hl=gl) en lugar do almacén de datos.
- As ferramentas OLAP como MicroStrategy teñen un uso compartido de datos de Cube intelixente e seguro que permite que os datos se compartan de forma segura.
- Outro beneficio é a coherencia da información e dos cálculos. Significa que a velocidade coa que se comparten os datos nos servidores OLAP non interfire cos informes e que os informes sempre seguen sendo consistentes.
- A presentación multidimensional mediante ferramentas OLAP axuda a comprender mellor as relacións que non estaban presentes anteriormente.
- Outro escenario popular son os escenarios "E se" do software OLAP. Son eminentemente máis posibles grazas ao procesamento multidimensional das ferramentas OLAP.
- Podemos aplicar restricións de seguridade a usuarios e obxectos mediante ferramentas OLAP.
- Crea unha plataforma única para a planificación, a previsión, a elaboración de informes e a análise.

### Inconvenientes do OLAP tradicional

O OLAP tradicional tiña os seus inconvenientes. Un par deles é o seguinte. Desvantaxes do OLAP tradicional:

- O modelado previo é imprescindible nas ferramentas OLAP tradicionais, o que supón un proceso lento.
- Gran dependencia das TIC: neste caso, un usuario é unha persoa de negocios pero debe ter bos coñecementos de TI. As ferramentas OLAP tradicionais requiren unha gran implicación de técnicos de TI e persoas que teñan boa experiencia empresarial xunto coas TI.

---

MRZ 2022

FORMAWEB IV