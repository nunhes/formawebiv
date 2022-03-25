## **Como definir unha base de datos**

A **definición de bases de datos** é « *aquel conxunto de datos almacenados e estruturados segundo as súas características ou tipoloxía para ser utilizados ou consultados posteriormente.* ".

Ata hai relativamente poucos anos, as bases de datos eran analóxicas, é dicir, contiñan información en papel ou textos impresos. Porén, coa chegada da era dixital e do Big Data, o uso de bases de **datos informatizadas** volveuse imprescindible .

Grazas ás bases de datos en formato dixital, púidose solucionar moitos dos problemas que xurdiron como consecuencia da enorme cantidade de información que se manexa na actualidade. Por exemplo, aforran espazo, aceleran as consultas e pódese almacenar moita máis información.

Os programas que o fixeron posible chámanse **sistemas de xestión de bases de datos (SGBD)** ou, en inglés, Database Management System (DBMS). Este tipo de programas facilitan moito o **almacenamento de datos** e a súa posterior consulta. Inicialmente eran empregados principalmente por grandes empresas ou administracións públicas, pero hoxe en día tamén son utilizados por todo tipo de usuarios ou empresas (por exemplo, para crear un rexistro de usuarios da páxina web).

**As consultas** utilízanse para obter a información almacenada nas bases de datos . Unha consulta é unha solicitude ao xestor da base de datos para acceder, eliminar ou modificar a información presente na base de datos. Para iso utilízase unha linguaxe específica (o máis habitual é SQL, do que falaremos máis adiante).

## **Características da base de datos**

As principais **características dunha base de datos** son as seguintes:

- Os datos almacenados teñen independencia física e lóxica.
- Eles garanten a integridade dos datos.
- Son sistemas de almacenamento que axudan a reducir ao mínimo a redundancia.
- É habitual que varios usuarios accedan a eles.
- Permiten consultas complexas de distintos tipos de datos.
- O acceso aos datos é seguro
- Os datos pódense facer copias de seguranza e recuperarse
- Accédese á información a través dunha linguaxe específica.

## **Obxectivos da base de datos**

Poderíase pensar que o propósito dunha base de datos é almacenar información. E a verdade é que tes razón. Non obstante, esa é unha visión moi restrinxida das súas funcións, xa que cobren moitos outros propósitos.

### **Traballar con consultas complexas e non predefinidas**

Un dos obxectivos básicos dunha base de datos é permitir consultas complexas e non predefinidas que afecten a máis dun tipo de entidade.

- *Queremos coñecer o número de clientes dunha tenda en liña que teñan máis de 30 anos e que realizaron máis de 5 pedidos no último ano.
- *Para cada un destes clientes, quere saber o nome, apelidos, enderezo e enderezo de correo electrónico.

### **Ofrecer flexibilidade e independencia**

As bases de datos tamén deben deseñarse para ser flexibles ante o cambio. Os datos e procesos dos usuarios deben ser o máis independentes posibles entre si, para que se poidan realizar actualizacións, variacións ou cambios tecnolóxicos sen necesidade de modificar aplicacións xa escritas.

### **Evitar a redundancia**

A redundancia podería definirse como a existencia de datos repetidos nunha base de datos. Normalmente, non quere ter datos redundantes. No caso de que un sistema de xestión de bases de datos permita definir datos redundantes, debería ser o propio sistema o encargado de actualizar a información en todos aqueles lugares onde se repita.

### **Garantir a integridade dos datos**

Outro dos obxectivos fundamentais dunha base de datos é manter a calidade e integridade dos datos en calquera circunstancia. Para iso defínense regras de integridade. Por exemplo, definir o número de identificación como un atributo clave, indicar que a data de nacemento debe ser unha data concreta ou que os clientes deben ter entre 18 e 99 anos.

### **Permitir concorrencia de usuarios**

Ademais, as bases de datos deben permitir o acceso simultáneo de varios usuarios. Isto pode causar problemas de interferencia cando varios usuarios modifican os datos ao mesmo tempo. As bases de datos solucionan o problema do acceso simultáneo mediante as chamadas transaccións de bases de datos.

### **Garantir a seguridade dos datos**

Por último, as bases de datos deben garantir a seguridade no acceso e mantemento da información. Por exemplo, en todo o relacionado coa confidencialidade dos datos, as autorizacións, os dereitos de acceso, ou o cumprimento da normativa vixente en materia de protección de datos.

## **Tipos de bases de datos**

Hai moitos tipos diferentes de bases de datos. O máis habitual é clasificalos segundo o [modelo](https://ayudaleyprotecciondatos.es/bases-de-datos/modelos) , o seu contido ou a variabilidade dos datos que inclúen. Pasamos a ver os tipos máis comúns de bases de datos.

### **Segundo o modelo**

A primeira clasificación das bases de datos é segundo o modelo empregado. Neste caso podemos atopar bases de datos relacionais, distribuídas, orientadas a obxectos, documentais, dedutivas, transaccionais, etc.

#### **relacional**

As bases de **datos** relacionais son unha das máis habituais pola súa flexibilidade e facilidade de uso. Neste modelo, non importa onde nin como se almacenen os datos. Pola contra, accédese á información mediante consultas que permiten un acceso rápido e flexible aos datos. Normalmente usan a linguaxe SQL.

#### **Distribuído**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/distribuida) distribuídas consisten en bases de datos establecidas en distintos lugares e conectadas por unha rede. Utilízanse en organizacións descentralizadas que precisan unirse a bases de datos de diferentes lugares (localidades, universidades, etc). Existen bases de datos distribuídas de forma homoxénea (utilizan o mesmo SGDB) ou heteroxénea (empregan sistemas multibase).

#### **NoSQL**

Son bases de datos que non usan a linguaxe SQL, ou que o utilizan só como soporte, pero non como consulta. Entre as linguaxes máis utilizadas polas [**bases de datos non relacionais**](https://ayudaleyprotecciondatos.es/bases-de-datos/no-relacional) están CQL ( *Contextual Query Language),* JSON ( *JavaScript Object Notation* ) e GQL ( *Graph Query Language).*

#### **orientado a obxectos**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/orientas-a-objetos) orientadas a obxectos céntranse en almacenar obxectos completos, incluíndo o seu estado e comportamento. Este tipo de bases de datos baséanse en conceptos básicos do tratamento informatizado de obxectos, como a herdanza, o encapsulamento ou o polimorfismo.

#### **multidimensional**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/multidimensionales) multidimensionais son similares ás bases de datos relacionais, pero úsanse a miúdo para o desenvolvemento de aplicacións moi específicas. A principal diferenza entre ambas é que nas táboas multidisciplinares, os atributos das **táboas** poden representar tanto dimensións como métricas.

#### **documentais**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/documentales) documentais están deseñadas para indexar textos completos e, polo tanto, deben estar preparadas para almacenar unha gran cantidade de información.

#### **dedutivas**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/deductivas) dedutivas ou lóxicas baséanse na lóxica matemática e son capaces de realizar deducións a partir de feitos ou regras establecidas, grazas a iso permiten establecer relacións indirectas entre distintos tipos de datos e solucionar algunhas das limitacións das bases de datos relacionais.

#### **transaccional**

[**As bases de datos transaccionais**](https://ayudaleyprotecciondatos.es/bases-de-datos/transaccionales) úsanse para enviar e recibir datos a alta velocidade. Neste tipo de bases de datos non se ten en conta a redundancia ou duplicación de datos, xa que a súa función é exclusivamente enviar e recibir información á maior velocidade posible.

#### **Xerárquico**

[**As bases de datos xerárquicas**](https://ayudaleyprotecciondatos.es/bases-de-datos/jerarquicas) organízanse en base a un nodo de información principal, ou nodo pai (raíz), do que xorden diferentes fillos (follas). É un sistema que organiza os datos xerarquicamente, en forma de árbore invertida.

#### **Rede**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/red) de rede son similares ás bases de datos xerárquicas, agás que pode haber varios nodos principais. Isto supuxo un importante avance no que respecta ás bases xerárquicas, sobre todo no que se refire á redundancia de datos.

### **Segundo o contido**

Outro método para clasificar as bases de datos é pola forma en que presentan o contido. Neste caso podemos atopar dous tipos, bibliográfico e de texto completo.

#### **Bibliográficos**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/bibliograficas) bibliográficas amosan información relevante sobre unha publicación rematada: título, autor, ano de publicación, editor, etc. Tamén poden presentar un pequeno fragmento do texto, pero nunca a publicación orixinal na súa totalidade, xa que senón estariamos a falar da tipoloxía que segue.

#### **Texto completo**

[**As bases de datos de texto**](https://ayudaleyprotecciondatos.es/bases-de-datos/texto-completo) completo almacenan e mostran todo o contido das publicacións. Por exemplo, todo o contido dos números publicados dunha determinada revista.

### **Segundo a variabilidade**

Outra das variables empregadas para a clasificación das bases de datos é a variabilidade da información que presentan. Así, podemos distinguir entre bases de datos estáticas ou dinámicas.

#### **Estática**

[**As bases de datos**](https://ayudaleyprotecciondatos.es/bases-de-datos/estaticas) estáticas almacenan datos fixos que non cambian co paso do tempo. Normalmente son datos históricos os que se poden estudar para ver a súa evolución no tempo e facer proxeccións ou tomar decisións en función de dita evolución.

#### **dinámica**

Pola súa banda, as [**bases de datos dinámicas**](https://ayudaleyprotecciondatos.es/bases-de-datos/dinamicas) almacenan información que cambia co paso do tempo. Os datos edítanse e actualízanse a medida que cambian. Por exemplo, unha base de datos cos prezos dunha tenda,

## **Onde telo na nube ou local?**

Hoxe en día existen diferentes métodos para xestionar bases de datos. O máis habitual é facelo a través dunha rede local ou na [contorna cloud](https://ayudaleyprotecciondatos.es/cloud-computing) (na nube). Vexamos as diferenzas entre ambos.

### **Nube**

O método DBaaS (base de datos como servizo) baséase na contratación de provedores de servizos para o almacenamento de datos. Neste caso, a información almacénase nos servidores do provedor, podendo acceder a ela a través de internet.

Entre as principais vantaxes das [**bases de datos na nube**](https://ayudaleyprotecciondatos.es/bases-de-datos/en-la-nube) está o aforro de espazo físico, a redución de custos ou a posibilidade de acceder aos datos desde calquera lugar ou dispositivo con acceso a internet.

### **Local**

Pola súa banda, unha **base de datos local** utiliza unha rede local (LAN), de xeito que a infraestrutura e xestión da dita base de datos realízase na propia organización. Só os ordenadores conectados á rede local poden acceder á información.

## **Vantaxes e inconvenientes das bases de datos**

A continuación vemos as principais vantaxes e inconvenientes de traballar con bases de datos.

### **Vantaxes**

As **vantaxes das bases de datos** son moitas e variadas, especialmente as informatizadas:

- **Reducen a redundancia**: as bases de datos informatizadas só almacenan unha copia dos mesmos datos, aforrando espazo de almacenamento e facilitando as consultas. Teña coidado, reducir a redundancia a cero non sempre é posible xa que ás veces é necesario crear relacións entre os datos.
- **Contribuír á coherencia dos datos**: a redución da redundancia tamén minimiza a posibilidade de que haxa inconsistencias dos datos. Ao almacenar cada dato só unha vez, tamén é posible modificalos dunha soa vez e poñelos a disposición dos usuarios inmediatamente.
- **Os datos pódense compartir**: as bases de datos permiten que a información almacenada sexa compartida por membros da organización ou por usuarios autorizados.
- **Favorecen a integridade dos datos**: a información almacenada ten maior validez e coherencia, grazas á aplicación das regras e restricións definidas no SGDB e que non poden ser violadas.
- **Aumentan a seguridade**: só o persoal autorizado pode acceder aos datos. Ademais, as bases de datos electrónicas adoitan incluír medidas de seguridade para evitar accesos non desexados ou interferencias ilexítimas.
- **Axilizan as consultas**: o acceso aos datos é máis rápido e eficiente grazas ao uso de linguaxes de consulta.
- **Incrementan a produtividade**: aforran tempo, tanto para os programadores como para os usuarios que realizan as consultas.
- **Simplifican o mantemento**: grazas á independencia entre datos e aplicacións, calquera cambio, modificación ou transferencia de datos pódese realizar dun xeito máis áxil e sinxelo.
- **Permiten o acceso simultáneo de varios usuarios**: nos sistemas de ficheiros isto pode provocar a perda de información ou a súa integridade, o que non ocorre cos sistemas de xestión de bases de datos.
- **Realizan copias** de seguridade: nos sistemas de ficheiros tradicionais o usuario tiña que facer copias de seguridade continuamente. En caso de perda de datos, tamén se perdeu toda a información engadida despois da última copia de seguridade. Non obstante, SGBS fai copias de seguranza dos datos automaticamente, minimizando así a perda accidental de datos.
- **Permiten o cumprimento de estándares**: é máis doado adaptar o almacenamento, o acceso e o intercambio de datos aos estándares da empresa, así como ás normativas nacionais e internacionais, por exemplo o [RGPD](https://ayudaleyprotecciondatos.es/guia-rgpd) ou a [LOPDGD.](https://ayudaleyprotecciondatos.es/lopdgdd)

### **Desvantaxes**

Non obstante, non todo é perfecto e tamén podemos falar dalgunhas **desvantaxes das bases de datos**:

- **Os SGDB poden ser complexos**: son programas que inclúen moitas funcionalidades que hai que comprender, ademais de coñecer a linguaxe de programación que utilizan.
- **Supoñen un custo engadido**: dependendo da cantidade de datos a almacenar, pode ser necesario adquirir máquinas potentes e un gran espazo de almacenamento.
- **Poden ser defectuosos**: os DBMS non son infalibles e son vulnerables a fallas de seguridade. Isto pode ser especialmente grave se toda a información está centralizada no SGDB, o que podería poñer en risco todo o sistema. Por iso é tan importante ter sempre copias de seguridade.

## **Principais motores de bases de datos**

Actualmente existen numerosos **xestores de bases** de datos , que permiten almacenar e acceder á información dun xeito áxil e flexible. A continuación vemos cales son algunhas das máis utilizadas.

### **mysql**

MySQL é o xestor de bases de datos máis utilizado no mundo. É un sistema multiusuario e multiproceso que se utiliza na maioría das páxinas web e aplicacións de software libre actuais.
Entre as principais vantaxes do xestor de bases de [datos MySQL](https://ayudaleyprotecciondatos.es/bases-de-datos/mysql) están a súa facilidade de uso e o seu bo rendemento. Ademais, é moi sinxelo de instalar e configurar e permite soporte multiplataforma. Por outra banda, ten algúns problemas de escalabilidade, é dicir, non é tan eficaz á hora de manexar grandes volumes de datos.

### **SQLite**

É unha biblioteca C que che permite realizar transaccións de datos. A súa principal vantaxe é que non precisa utilizar un servidor nin configuracións, polo que ocupa moito menos espazo que outros xestores. Ademais, ofrece un bo rendemento e cumpre os criterios de atomicidade, consistencia, illamento e durabilidade.

### **MongoDB**

É o xestor de bases de datos NoSQL máis utilizado na actualidade. É un sistema baseado en ficheiros que usa a linguaxe BSON. A súa popularidade é tal que é utilizada por empresas coñecidas como Google, Facebook ou Cisco.

### **MariaDB**

É un xestor de bases de datos moi semellante a MySQL. De feito, naceu como unha evolución deste programa, tras a compra de MySQL por parte de Oracle. Ten a maioría das funcións de MySQL pero inclúe algunhas extensións adicionais. Ademais, é de código aberto e 100% compatible con MySQL.

## **A linguaxe das bases de datos: SQL**

A **linguaxe de consulta de bases** de datos máis utilizada é **SQL** , *Structured Query Language* ou Structured Query Language.

Basicamente, é unha linguaxe deseñada para xestionar e recuperar información en xestores de bases de datos (relacionais). Para iso, fai uso do **cálculo relacional** e da **álxebra** . Grazas a iso, permite a inserción de datos nos xestores, realizar actualizacións, consultas ou modificacións, así como eliminar datos ou controlar o acceso á información.

A semente da linguaxe SQL plantouse no ano 1970, cando EFCodd propuxo un sistema de almacenamento baseado no módulo relacional e no cálculo de predicados. En base a isto, a empresa IBM desenvolveu a linguaxe **SEQUEL** , que máis tarde foi ampliada e mellorada para ser utilizada polo xestor de **bases de datos System R** , en 1977.

Esta linguaxe, SEQUEL, foi evolucionada e perfeccionada para dar lugar ao que hoxe coñecemos como **linguaxe SQL** . Na década de 1980 converteuse na linguaxe empregada pola maioría das bases de datos relacionais, ata que en 1986 foi finalmente recoñecido e estandarizado polo ANSI (American National Standards Institute).

Entre as principais **características da linguaxe SQL** están as seguintes:

- Permite crear, modificar e eliminar esquemas de relación.
- Utiliza álxebra e cálculo relacional para realizar consultas.
- Contén regras baseadas en comandos para garantir a integridade dos datos.
- As instrucións pódense incluír en diferentes linguaxes de programación como C++, Pascal, Java, PHP, etc.

Por outra banda, a linguaxe SQL está preparada para manexar diferentes tipos de datos:

- Int: son datos de valor enteiro, asinados ou sen asinar.
- Varchar: cadeas de palabras formadas por caracteres alfanuméricos (tamén permite caracteres especiais).
- Tempo: hora
- data: data

## **exemplos**

Existen numerosos **exemplos de bases de datos obsoletas** que hoxe en día foron substituídas por bases de [datos informatizadas baseadas na linguaxe SQL](https://ayudaleyprotecciondatos.es/bases-de-datos/sql) . Vexamos algúns exemplos de bases de datos comúns:

- **Guías telefónicas**: un exemplo serían as páxinas amarelas. Hoxe están practicamente en desuso. Estas guías contiñan unha lista de números de teléfono, ordenados por sectores, ou polo nome do seu propietario (ordre alfabético). Antes eran bastante completas, pero a cambio eran pesadas, ocupaban moito espazo e non permitían o acceso inmediato á información.
- **Bibliotecas**: as bibliotecas adoitan ter o seu propio sistema para almacenar e clasificar libros. Estes sistemas deben incluír funcións que permitan rexistrar todos os títulos dispoñibles, así como coñecer o número de exemplares de cada un, ou se están en préstamo, tanto en circulación como en salas.
- **Rexistros médicos**: os datos do paciente actualízanse cada vez que chegan ao hospital. Inclúen datos como a data das últimas visitas, patoloxías, tratamentos recibidos, etc. Trátase de información considerada sensible, polo que o acceso a estes datos está moi restrinxido e é exclusivo do persoal médico que vai atender ao paciente.
- **Tendas en liña**: en calquera comercio electrónico, trátanse datos sobre clientes, produtos, prezos, transaccións realizadas e un longo etcétera. Para iso é fundamental o uso dun xestor de bases de datos.

## **Canto custa unha base de datos?**

Ás veces, cando se compra certo software, o provedor xa inclúe o servizo de base de datos. Este servizo pódese pagar na súa totalidade ou no modo de pago por uso ou de software como servizo (SaaS).

Noutras ocasións, a empresa xa dispón dos seus propios servidores e quere ter unha base de datos propia e non “alugada”. Nese caso, terá que poñerse en contacto co provedor da base de datos para obter un sistema de xestión independente do software.

Dependendo dos dous escenarios anteriores, o **prezo da base de datos** será diferente. Pero tamén hai moitos outros factores que poden influír no custo dunha base de datos.

- Tipo de base de datos
- Persoalización
- Capacidade de almacenamento
- Número de instancias, streaming de almacenamento
- Notificacións por correo electrónico
- Moitas outras funcionalidades

Do mesmo xeito, cada empresa impón as súas propias taxas, polo que non existe un prezo estándar para as bases de datos.

Para que vos fagades unha idea, os **prezos da base de datos Azure para uso xeral** oscilan entre os 329 euros mensuais por 10,2 GB de capacidade, ata os 13.369 euros mensuais por 396 GB de capacidade. Neste caso, Azure podería ofrecer unha capacidade de almacenamento de ata 4 TB, co que o prezo se dispararía aínda máis.





---

MRZ 2022

*ref.: https://ayudaleyprotecciondatos.es/bases-de-datos/*

*Aquí atoparas moita info xeralista sobre bases de datos - definición, usos, cobertura, historia,...- non son artigos técnicos pero poden axudar a crearnos unha idea máis clara de porque e para que se usan as bases de datos.*