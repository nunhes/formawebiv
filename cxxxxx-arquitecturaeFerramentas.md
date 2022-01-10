[TOC]

# Arquitecturas e ferramentas de programación no lado servidor

## Introducción

Cando unha páxina web se descarga no teu ordenador, o seu contido define que é o que se debe amosar en pantalla. Este contido está programado nunha **linguaxe  de marcado**, formado por etiquetas, que pode ser **HTML** ou **XHTML**.

As etiquetas que foman parte do código da páxina indican o obxectivo de cada unha das partes que a compoñen. Así, dentro destas linguaxes hai etiquetas para indicar que un texto é un encabezado, que forma parte dunha táboa, ou que simplemente é un paragrafo de texto.

A demáis, se a páxina está ben estruturada, a información que se lle subministra ao navegador inclúe o estilo co que se debe mostrar cada unha das partes da páxina, a través dunha **folla de estilos o CSS** (*Cascading Style Sheet*), incluída ou vinculada ao arquivo visitado. CSS é unha linguaxe utilizada para definir as características de presentación dun documento escrito en linguaxe HTML, XHTML ou XML). A folla de estilos se atopa indicada na páxina web e o navegador a descarga xunto con ésta.

Estes dous arquivos se descargan no teu ordenador desde un servidor web como respuesta a unha petición. Os pasos desta interacción son os seguintes:

1. O teu ordenador solicita a un servidor web unha páxina, que soe ter extensión .html, .htm o .xhtml
2. O servidor busca esa páxina nun almacén de páxinas
3. Se o servidor atopa esa páxina, a recupera.
4. E por último, o servidor envía a páxina ao navegador para que éste poida amosar o seu contido
5. Se non se atopa a páxina, se enviará unha páxina de erro


Este é un exemplo típico dunha **comunicación cliente-servidor**. O cliente é o que fai a petición e inicia a comunicación, e o servidor é o que recibe a petición e a atende. O navegador que usas para navegar é, neste caso, o cliente web.



![Esquema de funcionamiento de unha páxina web](https://jairogarciarincon.com/img/clases/1013.jpg)

*Fonte: informmundo.blogspot.com.es*

*Pregunta*:  É posible ver unha páxina web sen que interveña un servidor?



## Xeración dinámica de páxinas web

As páxinas das que falamos até agora son **páxinas web estáticas**, o seu contido é sempre o mesmo. Son útiles para mostrar unha información concreta, e mostrarán esa mesma información cada vez que un cliente as solicite.

Pero tamén existen as **páxinas web dinámicas**. Neste tipo de páxinas o contido pode cambiar en función de diversas circunstancias, como poden ser o navegador que estás usando, o usuario co que teñas identificado, ou as accións que efectues.

Neste tipo de páxinas, para a comunicación entre o cliente e o servidor se soe empregar unha **interface de entrada común ou CGI (\*Common Gateway Interface\*)** que, *segundo a Wikipedia*, é unha importante tecnoloxía da World Wide Web que permite a un cliente (navegador web) solicitar datos dun programa executado nun servidor web. CGI especifica un estándar para transferir datos entre o cliente e o programa e é un mecanismo de comunicación entre o servidor web e unha aplicación externa cuxo resultado final da execución son obxectos *MIME (Multipurpose Internet Mail Extensions)*, isto é, texto, arquivos, audio, vídeo, etc.

Dentro das páxinas web dinámicas podemos distinguir dous tipos:

1. Aquelas que inclúen código que se executa no navegador, normalmente en linguaxe **JavaScript** que se descarga xunto coa páxina. Cando o navegador amosa a páxina en pantalla, executa o código que a acompaña. Este código pode incorporar funcións que poden ir desde amosar animacións hasta cambiar totalmente a apariencia e o contido da páxina.
2. Aquelas que no lado do servidor executan códigos de guión - **.php, .asp, .jsp, .cgi** ou **.aspx**-, e que xeran os contidos que se van a servir dunha **forma dinámica**. A partir de certas instruccións e/ou da execución de programas e funcións no servidor, se construen documentos que han chegar ao cliente como un documento html que non existe coma tal en ningures.



O esquema de funcionamiento dunha páxina web dinámica é o seguinte:

1. O cliente web (navegador) do ordenador solicita a un servidor web unha páxina.
2. O servidor busca esa páxina e a recupera.
3. No caso de que se trate dunha páxina web dinámica, o servidor web contacta co módulo responsable de executar o código e  envíallo.
4. Como parte do proceso de execución, pode ser necesario obter información dalgún repositorio, xeralmente unha base de datos,aínda que pode ser algún outro tipo de arquivo (JSON, XML, ...).
5. O resultado da execución será unha páxina en formato HTML, similar a calquera outra páxina web non dinámica.
6. O servidor web envía o resultado obtido ao navegador, que a procesa e amosa en pantalla.




### Aplicacións web

As aplicacións web emplean páxinas web dinámicas para crear aplicacións que se executen nun servidor web e se mostren nun navegador. Un exemplo son os clientes de correo, que che permiten consultar as mensaxes de correo recibidos e enviar os teus propios correos utilizando un navegador.

Hoxe en día existen aplicacións web para multitude de tareas como procesadores de texto, xestión de tarefas, ou edición e almacenamento de imaxes. Estas aplicacións teñen certas avantaxes e certos inconvenientes si as comparas coas aplicacións tradicionais que se executan sobre o sistema operativo da propia máquina.



**Avantaxes**

- **Non é necesario instalalas nos equipos nos que se vaian a utilizar**. Se instalan e se executan solamente nun equipo, no servidor, e isto é suficiente para que se poidan utilizar de forma simultánea desde moitos equipos e clientes.

- Como só se atopan instaladas nun equipo, **é máis sinxelo xestionalas** (facer copias de seguridade dos seus datos, corrixir erros, actualizalas).

- **Se poden utilizar en todos aqueles sistemas que dispoñan dun navegador web**, independentemente das súas características (non é necesario un equipo potente) ou do seu sistema operativo.

- **Se poden utilizar desde calquera lugar no que dispoñamos de conexión** co servidor. En moitos casos isto fai posible que se poida acceder ás aplicacións desde sistemas non convencionais, como por exemplo teléfonos móbiles.

  

**Inconvenientes**

- **A interface de usuario das aplicacións web é a páxina que se amosa no navegador**. Isto restrinxe as características da interface ás dunha páxina web.
- **Se depende dunha conexión** co servidor para poder empregalas. Se falla a conexión, no poderemos acceder á aplicación web.
- **A información que se mostra no navegador debe transmitirse desde o servidor**. Isto fai que certo tipo de aplicacións non sexan axeitadas para a seu despregue como aplicación web (por exemplo, as aplicacións que manexan moito contido multimedia, como a edición de vídeo,...).

Hoxe en día moitas aplicacións web utilizan as avantaxes que lles ofrece a xeración de páxinas dinámicas. A gran maioría do seu contido está almacenado nunha base de datos. Aplicacións como Wordpress, Drupal, Joomla!, Magento, Prestashop,... e outras, ofrecen dúas partes ben diferenciadas:

- **Unha parte externa ou de \**front-end\**, conformada polo conxunto de páxinas que poden ver a maioría de usuarios.**

- **Unha parte interna ou \**back-end\**, que é outro conxunto de páxinas dinámicas que utilizan só as persoas autorizadas para a produción de contido e a administración da aplicación web: organizar contido, configurara as funcionalidades e a apariencia, etc.**

  

### Execución do código na entorna cliente e na entorna servidor

Cando o teu navegador solicita a un servidor web unha páxina, é posible que antes de enviárcha se teña que executar, por sí mesmo ou por delegación, algún programa para obtela. Ese programa é o que xera, en parte ou na súa totalidade, a páxina web que chega ao teu equipo. Nestos casos, **o código se executa na entorna do servidor** web.

A demáis, cando unha páxina web chega ao teu navegador, é tamén posible que inclúa algún programa ou fragmentos de código (normalmente en  linguaxe JavaScript) que se deban executar unha vez cargada a páxina no navegador.  **Ese código se executará na entorna cliente** e, a demáis de poder modificar o contido da páxina, tamén pode levar a cabo accións como a animación de textos ou obxectos da páxina ou a comprobación dos datos que introduces nun formulario.

Esta división é así porque o código que se executa no cliente web (no teu navegador) non ten, mellor dito tradicionalmente non tiña, acceso aos datos que se almacenan no servidor. É dicir, cando no teu navegador querías acceder un novo correo, o código Javascript que se executaba no navegador non podía obter da base de datos o novo contido. A solución era crear unha nova páxina no servidor coa información que se pedía e enviala de novo ao navegador.

Máis, desde fai uns anos existen técnicas de desenvolvemento web como **AJAX** e *frameworks* progresivos tales como **React**, **Angular** ou **Vue**, que nos posibilitan realizar programas nos que o código JavaScript que se executa no navegador poida comunicarse cun servidor de forma asíncrona e obter información coa que, por exemplo, modificar a páxina web actual ou enviar un correo sen necesidade de recargar a páxina.




## Tecnoloxías e arquitecturas

Os compoñentes principais cos que debes contar para executar aplicacións web nun servidor son os seguintes:

- **Un servidor web** para recibir as peticións dos clientes web (normalmente navegadores) e enviarlles a páxina que soliciten (unha vez xerada, xa que falamos de páxinas dinámicas). O servidor web debe coñecer o procedemento a seguir para xerar a páxina web: que módulo se encargará da execución do código e cómo se debe comunicar con el.
- **O módulo encargado de executar o código** ou programa e xerar a páxina web resultante. Este módulo debe integrarse dalgunha forma co servidor web, e dependerá da linguaxe e tecnoloxía que utilicemos para programar la aplicación web.
- **Unha aplicación de base de datos**, que normalmente tamén será un servidor. Este módulo non é estrictamente necesario pero na práctica se utiliza en todas as aplicacións web que utilizan grandes cantidades de datos co fin de xestionar o seu almacenamento.
- **A linguaxe de programación** que utilizarás para desenvolver as aplicacións.



A demáis dos compoñentes a utilizar, tamén é importante decidir como vas a organizar o código da aplicación. Moitas das arquitecturas que se usan na programación de aplicacións web axudan a *estructurar o código das aplicacións en capas ou niveles*.

O motivo de dividir en capas o desnvolvemento ou diseño dunha aplicación é que se poidan separar as funcións lóxicas da mesma, e incluso que sexa posible executar cada unha nun servidor distinto (no caso de que se considere necesario).

Nunha aplicación se poden distinguir, de forma xeral, funcións de **visualización** (encargadas de darlle formato aos datos para presentálos aos usuarios finais), operacións de **lóxica** (emprego dos datos para executar un proceso e obter un resultado), persistencia (ou mantemento dos datos almacenados de forma organizada) e **acceso** (para obter, introducir e administrar os datos no espazo de almacenamento).

Este patrón de arquitectura de software se coñece como [MVC - Modelo Vista Controlador](https://es.wikipedia.org/wiki/Modelo–vista–controlador). "... un patrón de [arquitectura de software](https://es.wikipedia.org/wiki/Arquitectura_de_software), que separa os [datos](https://es.wikipedia.org/wiki/Datos) e principalmente o que é a [lóxica de negocio](https://es.wikipedia.org/wiki/Lógica_de_negocio) dunha aplicación da súa representación e o módulo encargado de xestionar os eventos e as comunicacións. (*Fonte: Wikipedia*). Aínda que se creou para aplicacións de escritorio, acabou convertido na base da maioría dos *frameworks* de desenvolvemento web actuais.



### Arquitecturas

A primeira elección que terás que  facer antes de comenzar a programar unha aplicación web é a arquitectura que vas a utilizar. As máis populares:

- **Java EE (\*Enterprise Edition\*)**, que antes tamén se coñecía como J2EE. É unha plataforma orientada á programación de aplicacións en linguaxe Java. Pode funcionar con distintos xestores de bases de datos, e inclúe varias librarías e especificacións para o desenvolvemento de aplicacións de forma modular. Apoiada por grandes empresas como Sun e Oracle, que manteñen Java, ou IBM. Unha das súas avantaxes é a multitude de librarías existentes nesa linguaxe e a gran base de programadores que o coñecen. Dentro desta arquitectura existen distintas tecnoloxías como as **páxinas JSP e os \*servlets\***, ambos orientados á xeración dinámica de páxinas web, ou os **EJB**, compoñentes que normalmente aportan a lóxica da aplicación.
- **AMP**. Son as siglas de **Apache, MySQL e PHP**/Perl/Python. As dúas primeiras siglas fan referencia ao **servidor web** (Apache) e ao **servidor de base de datos** (MySQL). A última se corresponde coa **linguaxe de programación** que se emprega, que pode ser PHP, Perl ou Python. Dependendo do sistema operativo que se utilice para o servidor, se utilizan as siglas LAMP (para Linux), WAMP (para Windows) ou MAMP (para Mac). Tamén é posible usar outros compoñentes, como o xestor de bases de datos PostgreSQL no sitio de MySQL. Todos os compoñentes desta arquitectura son de código libre (*open source*). A súa gran avantaxe é a gran comunidade que a soporta e a multitude de aplicacións de código libre dispoñibles.
- **CGI/Perl**. É a combinación de dous compoñentes: **Perl**, unha potente linguaxe de código libre creado orixinalmente para a administración de servidores, e **CGI**, un estándar para permitir ao servidor web executar programas xenéricos, escritos en calquera linguaxe (tamén se poden utilizar por exemplo C ou Python), que devolven páxinas web (HTML) como resultado da súa execución. É a máis primitiva das arquitecturas que comparamos aquí.
- **ASP.Net** é a arquitectura comercial proposta por **Microsoft** para o desenvolvemento de aplicacións. É a parte da plataforma .Net destinada á xeración de páxinas web dinámicas. Proven da evolución da anterior tecnoloxía de Microsoft, ASP. A linguaxe de programación pode ser **Visual Basic, .Net ou C#**. A arquitectura utiliza o servidor web de Microsoft, **IIS**, e pode obter información de varios xestores de bases de datos entre os que se inclúe, como non, **Microsoft SQL Server**. Unha das maiores avantaxes da arquitectura .Net é que inclúe todo o necesario para o desenvolvemento e o despregue de aplicacións. Por exemplo, ten o seu propio entorno de desenvolvemento, **Visual Studio**, aínda que hai outras opcións dispoñibles. A maior desavantaxe é que se trata dunha plataforma comercial de código propietario.



**Para elixir a arquitectura correcta**, deberemos considerar entre outros os seguintes puntos:

- Que tamaño ten o proxecto?
- Que linguaxes de programación coñeces? Vale a pena o esforzo de aprender un novo?
- Vas a usar ferramentas de código aberto ou ferramentas propietarias? Cal é o coste de utilizar solucións comerciais?
- Vos a programar a aplicación ti só ou formaras parte dun grupo de programadores?
- Contas con algún servidor web ou xestor de base de datos dispoñible ou podes decidir libremente utilizar o que creas necesario?
- Que tipo de licenza vas a aplicar á aplicación que desenvolvas?




### Linguaxes de programación

Unha das diferenzas máis notables entre unha linguaxe de programación web e outra é a maneira na que se executan no servidor web. Se distinguen tres grandes grupos:

- **Linguaxes de guións (scripting)**: Son aquelas nos que os programas se executan directamente a partir do seu código fonte (conxunto de instruccións que compoñen un programa, e que non son executables directamente, senon que deben traducirse utilizando un compilador, intérprete ou similar antes de que poida ser executado pola máquina) orixinal. Se almacenan normalmente nun arquivo de texto plano e cando o servidor web necesita executar código programado nunha  linguaxe de guións, lle pasa a petición a un intérprete, que procesa as liñas do programa e xera como resultado unha páxina web. Pertencen a este grupo **Perl, Python, PHP e ASP** (o precursor de ASP.Net).
- **Linguaxes compilados a código nativo (Linguaxe máquina ou código que pode ser executado directamente polo procesador)**: Son aqueles nos que o código fonte se traduce a código binario, dependente do procesador, antes de ser executado. O servidor web almacena os programas en modo binario, que executa directamente cando se os invoca. O método principal para executar programas binarios desde un servidor web CGI. Utilizando CGI podemos facer que o servidor web execute código programado en calquera  linguaxe de propósito xeral como pode ser **C**.
- **Linguaxes compilados a código intermedio**: Son  linguaxes nos que o código fonte orixinal se traduce a un código intermedio, independente do procesador, antes de ser executado. É a forma na que se executan por exemplo as aplicacións programadas en Java, e o que fai que poidan executarse en varias plataformas distintas. Na programación web, operan desta forma as linguaxes das arquitecturas **Java EE (\*servlets\* e páxinas JSP) e ASP.Net**. Na plataforma ASP.Net e en moitas implementacións de Java EE, se utiliza un procedemento de compilación JIT. Este término fai referencia á forma na que se converte o código intermedio a código binario para ser executado polo procesador. Para acelerar a execución, o compilador pode traducir todo ou parte do código intermedio a código nativo cando se invoca a un programa. O código nativo obtido soe almacenarse para ser utilizado de novo cando sexa necesario.


Cada unha destas formas de execución do código polo servidor web ten as súas avantaxes e inconvenientes:

- As linguaxes de guión teñen a avantaxe de que **non é necesario traducir o código** fonte orixinal para ser executados, o que aumenta a súa portabilidade. Si se necesita realizar algunha modificación a un programa, se pode facer no momento. Polo contrario o proceso de interpretación ofrece un **peor rendemento** que as outras alternativas.
- As linguaxes compiladas a código nativo son as de **maior velocidade de execución**, pero teñen **problemas no relativo a súa integración** co servidor web. Son programas de propósito xeral que non están pensados para executarse na entorna dun servidor web. Por exemplo, **non se reutilizan os procesos** para atender a varias peticións: por cada petición que se faga ao servidor web, se debe executar un novo proceso. Ademáis os programas **non son portables** entre distintas plataformas.
- As linguaxes compiladas a código intermedio **ofrecen un equilibrio** entre as dúas opcións anteriores. O seu **rendemento é moi bo** e **poden portarse** entre distintas plataformas nas que exista unha implementación da arquitectura (como un contenedor de *servlets* ou un servidor de aplicacións Java EE).



### Integración con linguaxes de marcas

Cando a web comenzóu a evolucionar desde as páxinas web estáticas ás dinámicas, unha das primeras tecnoloxías que se utilizaron foi a execución de código utilizando CGI. Os guións CGI son programas estándar, que se executan polo sistema operativo, pero que xeran como saída o código HTML dunha páxina web. Por tanto, os guiones CGI deben conter, mezcradas dentro do seu código, sentencias encargadas de xerar a páxina web.

Hoxe en día, existen dúas formas de realizar esta integración:

- **Integrar as etiquetas HTML no código dos programas**: Os programas inclúen dentro do sei código sentencias de saída (``echo`` en PHP, por exemplo) que son as que inclúen o código HTML da páxina web que se obterá cando se executen. Desta forma se programan, por exemplo, os guións CGI e os *servlets*.
- **Integrar o código do programa en medio das etiquetas HTML**: Desta forma, o contido da páxina que non varía pódese introducir directamente no HTML, e a linguaxe de programación se utilizará para todo aquilo que poida variar de forma dinámica. Esta metodología de programación é máis segura na web fronte a ataques tipo XSS e é a que se emprega nas  linguaxes ASP, PHP e coas páxinas JSP de Java EE.



### Ferramentas

Á hora de programar unha aplicación web, debes ter en conta con que ferramentas contas que te poidan axudar dunha forma ou outra a realizar o traballo. A demáis das ferramentas que se teñan que utilizar no servidor unha vez que a aplicación se execute, como por exemplo o servidor de aplicacións ou o xestor de bases de datos, das que xa coñeces o seu obxectivo, existen outras que resultan de gran axuda no proceso previo, no desenvolvemento da aplicación.

Desde fai tempo, existen **entornos integrados de desenvolvemento (IDE)** que agrupan nun único programa moitas destas ferramentas. Algúns destes entornos de desenvolvemento son específicos dunha plataforma o dunha  linguaxe, como sucede por ejemplo con **Visual Studio**, o IDE de Microsoft para desenvolver aplicacións en  linguaxe C# oiu Visual Basic para a plataforma .Net. Outros coma **Eclipse, NetBeans ou Jetbrains** te permiten personalizar o entorno para traballar con diferentes  linguaxes e plataformas, como Java EE ou PHP.

Non é imprescindible utilizar un IDE para programar. En moitas ocasións podes votar man dun simple editor de texto para editar o código que necesites. Sin embargo, si o obxectivo é desenvolver unha aplicación web, as características que te aporta un entorno de desenvolvemento son moi convenientes. Entre estas características se atopan:

- **Resaltado de texto**: Mostra con distinta cor ou tipo de letra os diferentes elementos da linguaxe: sentencias, variables, comentarios, etc. Tamén xera indentado automático para diferenciar de forma clara os distintos bloques dun programa.
- **Completado automático**: Detecta qué estás escribindo e cando é posible amosa distintas opcións para completar o texto.
- **Navegación no código**: Permite buscar de forma sinxela elementos dentro do texto, por exemplo, definicións de variables.
- **Comprobación de erros ao editar**: Reconoce a sintaxe da linguaxe e revisa o código en busca de erros mentras se escribe.
- **Xeración automática de código**: Certas estruturas, como a que se utiliza para as clases, se repiten varias veces en un programa. A xeración automática de código pode encargarse de crear a estrutura básica, para que só haia que completala.
- **Execución e depuración**: Esta característica é unha das máis útiles. O IDE se puede encargar de executar un programa para poder probar o seu funcionamento. A demáis, cando algo non funciona, te permite depuralo con ferramentas como a execución paso a paso, o establecemento de puntos de ruptura ou a inspección do valor que almacenan as variables.
- **Xestión de versións**: En conxunción cun sistema de control de versións, a entornoa de desenvolvemento te pode axudar a gardar copias do estado do proxecto ao longo do tempo, para que si é necesario poidas revertir os cambios realizados.


Algúns dos IDE de código aberto máis utilizados na actualidade son **Eclipse, NetBeans e Jetbrains**. En xeral todos permiten o desenvolvemento de aplicacións informáticas en varias linguaxes de programación. Aínda que nas súas oríxes se centraron na programación con  linguaxe Java, hoxe en día admiten directamente ou coa axuda de módulos, varios  linguaxes entre os que se inclúen C, C++, PHP, Python e Ruby.



## Integración co servidor web

A comunicación entre un cliente web ou navegador e un servidor web se leva a cabo gracias ao protocolo HTTP.

O servidor web procesa estás peticións. Cada arquitectura, das que acabamos de ver, ten a súa forma de integrarse co servidor para executar o código da aplicación.

A tecnoloxía máis antigua é CGI. CGI é un protocolo estándar que existe en moitas plataformas. A gran mayoría de servidores web dispoñen deste recurso. Define que debe facer o servidor web para delegar nun programa externo a xeración dunha páxina web. Eses programas externos se coñecen como guións CGI, independentemente da linguaxe na que estén programados (aínda que se soen programar en linguaxes de guión como Perl).

O principal problema de CGI é que cada vez que se executa un guion CGI, o sistema operativo debe crear un novo proceso. Isto implica un maior consumo de recursos e menor velocidad de execución. Existen algunhas solucións que aceleran a ejecución, como **FastCGI**, e tamén outros métodos para executar guións na entorna dun servidor web, por exemplo o módulo **mod_perl** para executar en Apache guións programados en Perl.

Aínda que tamén é posible executar código en linguaxe PHP utilizando CGI, os intérpretes PHP soen usar o módulo **mod_php** é a forma habitual que se utiliza para executar guións en PHP utilizando plataformas AMP, e o seu equivalente para a linguaxe Python é **mod_python**.

A arquitectura Java EE é máis complexa. Para poder executar aplicacións Java EE nun servidor básicamente temos dúas opcións: **servidores de aplicacións**, que implementan todas as tecnoloxías dispoñibles en Java EE, e **contenedores de \*servlets\* (Tomcat é o máis coñecido)**, clases que amplían a capacidade do servidor e que soportan só parte da especificación. Dependendo da magnitude da nosa aplicación e das tecnoloxías que utilice, teremos que instalar unha solución ou outra.

A arquitectura ASP.Net utiliza o **servidor IIS de Microsoft**, que xa integra soporte en forma de módulos para manexar peticións de páxinas dinámicas ASP e ASP.Net. A utilidade de administración do servidor web inclúe funcións de administración das aplicacións web instaladas no mesmo.

## Anexo

Para poder executar código PHP - ou outras linguaxes de guión do lado do servidor-, é necesario un intérprete de comandos capaz de compilar dito código, así como un navegador web para poder visualizar o resultado. 

Ver: https://geekflare.com/es/lamp-lemp-mean-xampp-stack-intro/

Para o desenvolvemento dependemos dunha conexión permanente e de calidade ou podemos replicar/simular unha entorna de servidor no noso computador. Existen programas específicos para isto:

- [Xampp](https://www.apachefriends.org/es/index.html)
- [Laragon](https://laragon.org)
- e [máis](https://progsoft.net/es/software/ampps)

#### Instalar de XAMPP

1. Accede a [Apache Friends](https://www.apachefriends.org/es/index.html) e selecciona a opción adecuada para o teu sistema operativo (p.ex., Windows):



![Página de Apache Friends](./assets/Página de Apache Friends-0s00.png)Fuente: Elaboración propia



2. Instala a aplicación. Só necesitarás as opcións marcadas na seguinte figura. Pero tamén pode probar o resto de opcións.



![Componentes de XAMPP](./assets/Componentes de XAMPP-ND95.png)



3. Recibirás unha alerta de seguridade do firewall de *Windows*, é suficiente con que esté marcada a opción de redes privadas:



![Alerta de seguridad de Windows](./assets/Alerta de seguridad de Windows-0cZC.png)



4. Unha vez finalizada a instalación, se abrirá o *Control Panel* de XAMPP. O módulo **Apache**, é o único que vas a necesitar para as páxinas estáticas -html,css,js-.  Se vas a traballar con páxinas dinámicas precisaras tamén o módulo MySql para a xestión e acceso ás bases de datos.

5. Si tiveras problemas para inicialo, é posible que estés utilizando algún outro software de virtualización que estea reservando o porto **http 80**. Nese caso, accede desde o *Control Panel* a *Config > Apache (httpd.conf)*, busca a línea **Listen 80** e substitúea por **Listen 8080** (p.ex., ou calquera outro porto que non te cause problemas ao iniciar **Apache**).



![Modificación httpd.conf](./assets/Modificación httpd.conf-J1Lt.png)

6. Si o problema os tes co porto **https 443**, accede desde o *Control Panel* a *Config > Apache (httpd-ssl.conf)*, busca a liña **Listen 443** e substitúea por **Listen 444** (ou calquera outro porto que non cause problemas aoiniciar **Apache**).



![Modificación httpd-ssl.conf](./assets/Modificación httpd-ssl.conf-Mzaz.png)



Unha vez instalado XAMPP, lembra iniciar o *Control Panel* e os módulos **Apache** e MySql cada vez que vaias a programar. A demáis, todos teus proxectos debes crealos baixo a ruta **C:/xampp/htdocs**.



## 



__ref.:_ https://jairogarciarincon.com/clase/arquitecturas-y-herramientas-de-programacion-en-lado-servidor/

MÁIS SOBRE PHP E DESENVOLVEMENTO WEB

https://www.writephponline.com/

https://www.writephponline.com/tutorial/php/php-installation
