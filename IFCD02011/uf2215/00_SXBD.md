[TOC]

# Introdución ao sistema xestor de base de datos (SXBD)

Practicamente ningún ordenador ou aplicación web porían funcionar sen un **sistema de base de datos**. O **sistema de xestión de base de datos** subxacente a toda base de datos é tan importante como o propio **conxunto dos datos**, xa que non sería posible administralos sen el.



## Que é un *data management system* (DBMS)?

A propia base de datos e o sistema xestor de base de datos ou SXBD (en inglés DBMS *database management system*) conforman o que se denomina o sistema de base de datos (as veces, se utiliza simplemente o térmo *base de datos* para denominalo). En térmos xerais, un SXBD é un **software** que **sigue un modelo de sistema de base de datos** e, polo tanto, resulta decisivo á hora de configurala, administrala e utilizala. Só cando o sistema xestor de base de datos está instalado e configurado, os usuarios poden introducir e consultar os datos. Os **permisos de lectura e escritura**, así como as **funcións de administración** xeral, se establecen mediante as interfaces específicas da aplicación e a linguaxe de definición de datos correspondente. A máis coñecida destas linguaxes é SQL (*Structured Query Language*, linguaxe de consulta estruturada).

 :pencil: Os térmos *sistema xestor de base de datos* (SXBD) e *base de datos* soen utilizarse indistintamente cando se fala do software que se emprega para administrar bases de datos. Non obstante, a base de datos en sí solo consta dos **propios datos en forma estruturada**, mentras que o SXBD é o elemento básico para **materializar estas estruturas**.

## Compoñentes dun SXBD

Un sistema de xestión de base de datos consta de varias compoñentes, todas as cales contribúen ao bo funcionamento do software. Os elementos básicos que o conforman son tres: o dicionario de datos, a linguaxe de definición de datos e a linguaxe de manipulación de datos.

- **Dicionario de datos**: consiste nunha lista de metadatos que reflicten as características dos diversos tipos de datos incluídos na base de datos. A demais, estes metadatos informan sobre os permisos de uso de cada rexistro e a súa representación física. Desta maneira, o diccionario proporciona toda a información relevante sobre os datos almacenados.
- **Linguaxe de definición de datos**: a linguaxe de definición de datos, tamén chamado linguaxe de base de datos ou DDL (*data definition language*), sirve para estruturar o contido da base de datos. Gracias a este linguaxe, é posible crear, modificar e eliminar obxectos individuais, como referencias, relacións ou dereitos de usuario.
- **Linguaxe de manipulación de datos**: mediante a linguaxe de manipulación de datos ou DML (*data manipulation language*), pódense introducir novos rexistros na base de datos, así como eliminar, modificar e consultar os que yxa contén. Esta linguaxe tamén permite comprimir e extraer os datos.

## Tarefas, funcións e propiedades dun SXBD

O sistema de xestión de base de datos é o compoñente máis importante dun sistema de base de datos. Sin él, no sería posible administrar, controlar ou supervisar a base de datos. Este software tamén é responsable de xestionar todos os permisos de lectura e escritura. Un termo que soe utilizarse moito para resumir as funcións e propiedades das transaccións dos sistemas xestores de base de datos é **ACID**, siglas dos termos en inglés *atomicity*, *consistency*, *isolation* e *durability* (es decir: atomicidade, consistencia, illamento e permanencia). Estes catro conceptos engloban os requisitos máis importantes dun SXBD:

- A atomicidade ou **integridade** describe a propiedade de “todo ou nada” dos  SXBD, pola que todas as fases dunha transacción deben finalizarse por completo e na orde correcta para que esta sexa válida.
- A **consistencia** implica que as transaccións completadas non afecten a estabilidade da base de datos, o que require supervisalas constantemente.
- O **illamento** é a propiedade que asegura que as transaccións non obstaculicen ás demais, do que, polo xeral, se encargan algunhas funcións de bloqueo.
- A **permanencia** implica que tódolos datos queden almacenados permanentemente no SXBD, non só despois dunha transacción correcta, senón tamén e especialmente no caso dun erro ou caída do sistema. Os rexistros das transaccións, onde quedan anotados todos os procesos do SXBD, son fundamentais para garantir a permanencia.

Na seguinte táboa, se amosa outra clasificación das funciones e propiedades dos sistemas xestores de base de datos, que vai máis alo do modelo ACID.

| Función/propiedade               | Definición                                                   |      |      |
| :------------------------------- | :----------------------------------------------------------- | :--- | :--- |
| Almacenamento de datos           | A base de datos almacena texto, documentos, contrasinais e outros datos dixitais que poden consultarse. |      |      |
| Edición de datos                 | A maioría das bases de datos permiten editar directamente os datos almacenados, segundo os dereitos de acceso. |      |      |
| Eliminación de datos             | Os rexistros que conten a base de datos poden eliminarse por completo. Nalgúns casos, é posible recuperar os datos borrados, mentres que, noutros, a información se perde para sempre. |      |      |
| Administración de metadatos      | Polo xeral, na base de datos, a información se almacena con metadatos ou metaetiquetas que, por exemplo, axudan a organizala e facilitan a función de busca. Os dereitos de acceso tamén soen regularse mediante metadatos. A administración dos datos consiste en catro operacións fundamentais: ``create`` (crear), ``read/retrieve`` (leer/recuperar), ``update`` (actualizar) e ``delete`` (borrar). Este concepto, coñecido como **principio CRUD**, é o piar da xestión dos datos. |      |      |
| Seguridade dos  datos            | A base de datos debe ser segura para evitar o acceso de persoas non autorizadas. Para manter a seguridade dos datos, a demais de implementar un método de cifrado eficaz, hai que administrar a base de datos coidadosamente, sobre todo por parte do administrador principal. Ante todo, manter a seguridade se basea en tomar as precaucións técnicas necesarias para evitar que os datos se perdan ou sexan manipulados, o que representa un aspecto central da protección de datos. ["O RGPD e as bases de datos"](https://blog.ec4u.com/en/database-foundation-for-gdpr/). |      |      |
| Integridade dos  datos           | Por integridade nos referimos a que a información contida na base de datos se adhira a certas normas para garantir a súa coherencia, así como a definir a súa lóxica comercial. Só así se garante que o conxunto de a base de datos funcione de maneira coherente e constante. No modelo de base de datos relacional, se aplican catro destas normas: integridade de dominio, integridade de entidade, integridade referencial e coherencia lóxica. |      |      |
| Modo multiusuario                | As aplicacións da base de datos permiten acceder a ela desde varios dispositivos. No modo multiusuario é fundamental distribuír axeitadamente os dereitos e manter a seguridade dos  datos. Outro reto para as bases de datos con esta función é manter a coherencia dos datos cando moitos usuarios os consultan e editan, sin afectar demasiado ao rendemento. |      |      |
| Optimización de consulta         | No aspecto técnico, a base de datos debe optimizar o procesamento de cada consulta ao máximo para garantir un bo rendemento. Se a base de datos ten que “dar moitas voltas” para consultar os datos, o rendemento xeral do sistema se verá afectado. |      |      |
| *Triggers* e *stored procedures* | Destes procedementos se encargan unhas miniaplicacións almacenadas no SXBD, que se activan automaticamente (*trigger*) como consecuencia dalgunhas accións, co obxectivo de mellorar a integridade dos datos, entre outros. Os *triggers* e *stored procedures* son procesos típicos das bases de datos relacionais; o último tamén pode contribuír á seguridade do sistema si ao usuario só se lle permite realizar accións a través de procedementos predefinidos. |      |      |
| Transparencia do sistema         | A transparencia do sistema é especialmente importante para os sistemas distribuidos: ao impedir que o usuario distribúa e implemente os datos, o uso da base de datos distribuída é similar ao dunha base de datos centralizada. Mediante diferentes niveles de transparencia do sistema, se mostran ou ocultan os procesos nun segundo plano. O obxectivo principal, non obstante, é simplificar o uso o máximo posible. |      |      |

:pencil: **Si administras a túa propia base de datos, é fundamental que saibas protexer a seguridade dos datos de maneira integral.**

## Tipos de SXBD

O oxectivo de instalar un sistema xestor de base de datos é administrar os rexistros da mellor maneira posible. Existen varios modelos para iso, que difiren basicamente na maneira na que **se estruturan os datos**. Polo tanto, decidirse por un DBMS sempre implica decantarse por un **modelo de base de datos** concreto. Existen os seguintes modelos de bases de datos:

- Relacional
- Xerárquica
- De rede
- Orientada a obxectos
- Orientada a documentos

O máis común e popular é o [modelo de base de datos relacional](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/bases-de-datos-relacionales/), no que os datos se estruturan en **filas de táboa**. A vantaxe deste modelo radica na posibilidade de crear diferentes relacións entre as filas e presentalas en columnas. O procedemento é diferente ao do **modelo de base de datos xerárquico**, onde os diferentes datos se organizan en relacións pai-fillo, nunha **estrutura similar á dunha árbore**.

Outros enfoques para organizar os datos son o **modelo de base de datos de rede**, onde os datos, como o nome indica, se estruturan en forma de rede, ou o [modelo de bases de datos orientada a obxectos](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/base-de-datos-orientada-a-obxectos/), no que non só importa a relación entre os rexistros de datos, senón tamén o concepto da **herdanza**, que significa que os obxectos poden transferir algúns dos seus atributos a outros obxectos, o que se regula a través do SXBD.

Pola súa parte, o modelo de base de datos [orientado a documentos](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/bases-de-datos-documentales/) permite almacenar os rexistros de datos en diferentes documentos.

## SXBD: resumen de vantaxes e inconvenientes

Os SXBD, o piar de tódalas bases de datos, presentan varias vantaxes e puntos fortes, aínda que, como calquera outro software, tamén teñen algúns inconvenientes:

**Avantaxes dos  SXBD:**:

- Xestión fácil de grandes conxuntos de datos
- Acceso sinxelo e eficaz aos datos almacenados
- Gran flexibilidade
- Integridade e consistencia dos  datos
- Control de acceso do usuario (seguridade e protección de datos)
- Alta dispoñibilidade

**Inconvenientes dos SXDB**:

- Inversión inicial relativamente elevada (incluídos custes de hardware adicionais)
- Bastante menos eficaz para o software especial
- Se requiren empregados cualificados (administradores de bases de datos)
- Maior vulnerabilidade polo feito de centralizar os datos

## SXBD: sistemas máis populares

De entre os moitos sistemas xestores de bases de datos que existen, estes son os 15 máis populares e utilizados:

- Microsoft Access (relacional)
- Microsoft SQL Server (relacional)
- [MySQL](https://www.ionos.es/digitalguide/servidores/know-how/guia-para-aprender-a-utilizar-mysql/) (relacional)
- [Oracle Database](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/oracle-database/) (relacional)
- OrientDB (orientado a documentos)
- [CouchDB](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/presentacion-de-couchdb/) (orientado a documentos)
- Db2 de IBM (relacional)
- IMS de IBM (xerárquico)
- IBM Informix (relacional)
- MariaDB (relacional)
- Sybase ASE (relacional)
- [MongoDB](https://www.ionos.es/digitalguide/paginas-web/desarrollo-web/mongodb-presentacion-y-comparacion-con-mysql/) (orientado a documentos)
- [PostgreSQL](https://www.ionos.es/digitalguide/servidores/know-how/postgresql/) (combina relacional e orientado a obxectos)
- Firebird (relacional)
- InterSystems Caché (combina relacional e orientado a obxectos)
- InterSystems IRIS (combina relacional e orientado a obxectos)



---

MRZ 2022



ref: https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/sistema-gestor-de-base-de-datos-sgbd/