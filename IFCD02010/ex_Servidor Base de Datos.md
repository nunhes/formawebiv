# Servidor Base de Datos

A utilización de bases de datos resulta un dos elementps clave de moitas aplicacións, e resulta unha das ferramentas de maior implantación nas empresas, tanto on-line como off-line. As aplicacións web e de escritorio aproveitan as bases de datos para escribir, manter e recuperar información de xeito áxil.

Para operar con bases de datos é preciso dispor un **servidor de base de datos**.

## Qué é un Servidor de Base de Datos?

*Dúas cousas!*

Un servidor de base de datos, tamén coñecido como [database server](https://en.wikipedia.org/wiki/Database_server) ou, no caso de bases de datos relacionales, RDBMS (Relational DataBase Management Systems), é un **tipo de software de servidor que permiten a organización da información mediante o uso de táboas, índices e rexistros**.

A nivel de hardware, un servidor de base de datos **é un equipo informático especializado en servir consultas a clientes remotos** ou locais **que solicitan información ou modifican os rexistros e/ou táboas dalgunha das bases de datos presentes no sistema** (en moitos casos dende un servidor web ou dende un servidor de aplicacións).

As bases de datos dun sistema, sirven para xestionar e administrar información, en formas e cantidades distintas. E isto é aproveitado por empresas, universidades, institucións, bancos ou gobernos, que almacenan datos de cidadans - clientes e non :smiling_imp:-: direccións, teléfonos, correos electrónicos, gatos, ingresos, preferencias, gustos, etc. As bases de datos se aloxan e xestionan con/en servidores de bases de datos.

Os servidores de bases de datos son parte das primeiras infraestruturas informáticas que se crearon. Xurdiron na década de [1960](https://www.quickbase.com/articles/timeline-of-database-history) como modo de dar solucións as grandes empresas para o tratamento e administración de grandes cantidades de datos.

Co tempo eses datos comenzaron a compartirse cos denominados **clientes de base de datos**.

## Funcións dun Servidor de Base de Datos

A función fundamental dun servidor de base de datos é dar servicio a outras aplicacións web ou equipos. A día de hoxe esa relación de servicio se atén as especificacións do [modelo cliente servidor](https://en.wikipedia.org/wiki/Client–server_model).

Empregando un cliente de base de datos, pódese acceder á información que se garda nas distintas bases de datos dun sistema. Unha vez o cliente obten o acceso - normalmente empregando unha combinación que identifica o host de almacenaxe e xestión, o nome da base de datos e a identificación propia mediante un nome de usuario e un contrasinal -, se lle permitirá realizar diferentes tarefas. Tarefas que dependerán do nivel de privilexios que lle correspondan segundo as súas credenciais.

Ao(s) usuario(s) co maior grao de privilexios se os coñece como *'administrador'*. Teñen absoluto control sobre as bases de datos ás que se conectan. Outros usuarios non teñen tantos privilexios, e só poderán, p.ex., facer consultas de lectura - ler ou visualizar datos-. *Ver [SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html) no manual de MySQL.*

A dispoñibilidade destes sistemas é clave. E depende directamente tanto do hardware como do software. A combinación axeitada é fundamental, xa que un dos puntos clave do(s) sistema(s) de bases de datos - software e hardware- é a concorrencia. Na súa maioría os motores de bases de datos actuais permiten a simultaneidade das consultas. Isto significa que calquera usuario pode estar a ingresar ou modificar datos nunha determinada táboa, mentras outro(s) fan consultas ou len datos con distintos clientes desde dispositivos distintos e desde diferentes sitios do planeta. A capacidade de concorrencia dun sistema determina o limite de consultas simultaneas que soporta. *Ver [DDoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)*

O servidor de bases de datos matén a conexión até que termina a consulta do cliente de base de datos.

## Algúns usos habituais dos servidores de bases de datos

Hai moitos e moi diferentes usos que se lle poden pedir aos servidores de base de datos. Pero se vémola historia dende a súa invención estes son algúns dos usos máis habituais:

- **Administración de rexistros de persoas**: o software para rexistros médicos, as fichas de clientes en clínicas de todo tipo, ... son algún dos datos que se administran con bases de datos.
- **Administración de documentos**: a organización de todo tipo de documentos - de texto, de administración ou economía, de documentación técnica, con gráficos ou datos dixitalizados,... son almacenados e adminstrados por institucións e empresas grazas as bases de datos.
- **Administración contable e impositiva**: unha das primeiras e máis lonxeva aplicación e uso de base de datos son a administración de contas, os estudos contables, a optimización no tratamento de facturas, impostos, gastos, ingresos...
- **Indexación de sitios web**: as empresas que operan en Internet - Google é o máis chamativo pero no o unico- empregan inmensas bases de datos para indexar e xestionar moitos dos aspectos cos que visualizamos os sitios web: desde os resultados do teu buscador preferido ate a persalización de moitos dos portais que visitas e aplicacións que consumes.
- **Contido dinámico**: coa chegada de tecnoloxías do lado do servidor, como PHP, e os avances en programación e infraestrutura web, as bases de datos comezaron a ser empregadas para múltitude de usos: servir datos de foros, compoñer complexos sistemas de xestión de contidos -CMS-, administración de usuarios -CRM, ERP,...-, e máis.

## Algúns exemplos de servidores de bases de datos

Xa se comentou que no lado hardware un servidor de bases de datos é tan só unha máquina configurada para acometer un derterminado tipo de tarefas. Tarefas que virán determinadas pola infraestrutura software da que se dote a dita máquina.

Segundo o software xestor implantado falaríamos de:

### Servidor MySQL - ou *MySQL server*-

[MySQL](https://dev.mysql.com/downloads/mysql/) é dende fai décadas o líder in-discutido do software de bases de datos. Empregado masivamente no desenvolvemento web e tamén no desenvolvemento de aplicacións. Moito do seu exito veu da facilidade que sempre demostrou para o seu emprego con linguaxes de guión do lado servidor coma [PHP](http://php.net/), [Ruby](https://www.ruby-lang.org/es/) ou [Python](https://www.python.org).

MySQL é un software servidor de bases de datos de tipo relacional. Para moitos un paradigma das bases de datos.

Algunha das súas caracteristicas máis destacadas:

- Facilidade para a execución de tarefas simultáneas, tanto de lectura como de escritura. 
- Ser un software libre baixo licenza GNU/GPL.
- Demostrada rapidez de acceso aos datos
- Soporte para distintoss moores de almacenamento, como poden ser [MyISAM](https://en.wikipedia.org/wiki/MyISAM) ou [INNODB](https://en.wikipedia.org/wiki/InnoDB).

Permite uso de índices, múltiples transacciones, [balanceo de carga](https://en.wikipedia.org/wiki/Load_balancing_(computing)), clustering, backups en quente, etc.

### Servidor PostgreSQL - ou *PostgreSQL server*-

[PostgreSQL](https://www.postgresql.org/) é outro software servidor de bases de datos de tipo relacional, open source e orientado a obxectos distribuido baixo súa propia licencia: PostgreSQL.

Despois de MYSQL é unha das opcións máis populares, sobre todo en entornos empresariais e gubernamentais, onde a seguridade dos datos é primordial.

As súas caracteristicas máis comentadas: ofrecer unha grande estabilidade, ser un sistema maduro e robusto, e proporcionar velocidades moi optimas para a administración e tratamento dos datos.

Outra das razóns pola que resulta ben popular, en especial entre bancos e institucións financieiras, é polo seu optimizado modo de manexar grandes volúmes de datos aínda con altos indices de concorrencia - simultaneidade de consultas-.

### Servidor MSQL - ou *Microsoft SQL Server*-

[Microsoft SQL Server](https://www.microsoft.com/es-es/sql-server/sql-server-2019) é o servidor de base de datos SQL relacional de Microsoft. Moi difundido sobre todo entre os usuarios do SO e as plataformas Windows Server, xa que ofrece compatibilidade nativa coa linguaxe de programación ASP/ASP.NET, así coma con toda a suite de desenvolvemento de aplicacións dos sistemas operativos Windows.

Con soporte para procedementos almacenados, transaccións, administración mediante interfaz gráfica (GUI), uso de comandos DML e DDL, uso de servidor remoto,... dispón tamñen dunha interface de liña de comandos denominada ``osql`` ou ``SQLCMD``.

### Servidor MongoDB - ou *MongoDB server*-

[MongoDB](https://www.mongodb.com/) é un motor de base de datos NoSQL orientado a documentos.

Se trata tamén dun software libre, pero a diferencia de MySQL, PostgreSQL e outros motores de bases de datos relacionais, non garda datos en táboas, senon en estruturas [BSON](https://stackoverflow.com/questions/12438280/what-is-bson-and-exactly-how-is-it-different-from-json)  dinámicas(moi similares as estruturas JSON), algo que facilita o acceso aos datos.

Software multiplataforma, pódese executar sen problemas en Windows, Linux, MacOS ou Solaris.

Outras funcións destacadas son: a indexación, a replicación de datos, o balanceo intelixente de carga, a capacidade de almacenar arquivos, o agregado de datos (similar ao GROUP BY de SQL), a configuración de privilexios para os distintos usuarios e, por suposto, a encriptación por SSL/TLS.

Especialmente útil cando se necesita inmediatez no acceso aos datos e soporte de recuperación instantánea fronte aos fallos.

## Arquitectura hardware e de rede para un servidor de base de datos

O mundo dos servidores de bases de datos non é alleo as evolucións do medio. Para asegurarte un rendemento óptimo o teu servidor de base de datos:

- Emprega discos SSD, máis rápidos e de mellor rendemento tanto en lectura coma en escritura.
- Optimiza e vixia o rendemento da túa infraestrutura.
- Sempre podes agregar un [RAID 10](https://www.ionos.es/digitalguide/servidores/seguridad/raid-10/) (*Redundant Array of Independent Disks*), obterás máis velocidade e protección fronte fallos de hardware.
- Emprega unha CPU actual - Core i9, Intel E5 ou Xeon Gold.
- Non subestimes unha boa cantidade de RAM. Pensa que para atender a toda a demanda ningunha base de datos debería usarse con menos de 8GB, e sempre e mellor que sobre, a que falte.
- As operacións de balanceo ou replicación de datos en cluster ofrecen seguridade e tamén rápidez, pero soen demandar interfaces de 1Gbps por rede privada para non deteriorar o rendemento e o tempo de resposta.

## Que servidor de base de datos vas precisar?

Tanto se a túa aplicación é de escritorio, como si se executa na nube ou nun servidor web, dentro de un hosting dedicado; é moi posible que acabes tendo que recorrer a unha base de datos.

Do lado software: para a maioría das bases de datos pequenas, medianas ou non demasiado extensas, motores como **MySQL** ou **[MariaDB](https://mariadb.org/)** son solucións estandarizadas de demostrada eficacia. MySQL ofrece un rendemento ben bo, é flexible e resulta certamente fácil de implementar. Outras solucións baseadas no estandar **NoSQL**, como **MongoDB**, tamén demostran a súa eficacia cando hai moita escritura de datos ou se require dispoñibilidade inmediata, e tamén cando o número de datos almacenados en disco medra de xeito rápido.

Do lado hardware tamén hai moitas variables que deberás ter en conta cando vaias a elixir un servidor de base de datos - e o seu software motor-. Algunhas das que poden determinar a túa elección serán:

- O tamaño da(s) base(s) de datos.
- A cantidade de rexistros por táboa.
- O porcentaxe estimado de operacións de escritura e/ou lectura.
- O sistema operativo do servidor, e a(s) linguaxe(s) dispoñibles na plataforma.
- A eficacia fronte a concorrencia ou simultaneidade de consultas.
- E a dispoñibilidade (alta!) e eficiencia do balanceo de carga.



FEB 2022