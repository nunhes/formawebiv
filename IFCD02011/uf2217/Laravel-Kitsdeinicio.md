## Kit de inicio

Laravel ofrece algúns [kits](https://laravel.com/docs/starter-kits) de inicio para a súa posta en marcha. Estes kits de inicio proporcionan distintas funcións de autenticación para arrancar a túa aplicación.

- **Laravel**, preséntase coma o seu propio kit de inicio predeterminado sen ningún andamio de autenticación.
- **Breeze**, un punto de inicio para a túa aplicación, sinxelo e fácil de personalizar.
  - Iniciar sesión/pechar sesión
  - Xestión de contrasinais
  - Activos publicables
    - frontend con Blade, React ou Vue
  - Pila API opcional, sen modelo frontend
- **Jetstream**, un iniciador listo para a produción e rico en funcións para a súa aplicación.
  - Iniciar sesión/pechar sesión
  - Xestión de contrasinais
  - Xestión de perfiles
  - Verificación de correo electrónico
  - Autenticación de dous factores
  - Xestión de sesións
  - Soporte de API a través de Laravel Sanctum
  - Xestión de equipos(opcional)
  - Frontend con Inercia ou Livewire

## Autenticación

Dependendo do kit de inicio que escollas, pode que teñas que instalar algúns **paquetes adicionais**. Se non estás seguro de se os necesitas ou non, bótalle unha ollada á sección de [visión xeral do ecosistema de autenticación](https://laravel.com/docs/authentication#ecosystem-overview) da documentación oficial, que explica todo ben.

- [**Fortify**](https://laravel.com/docs/fortify) &rarr; Unha implantación só de backend para as funcións de autenticación de Laravel. Permíteche crear a túa propia interface de usuario personalizada para a autenticación, sen reimplantar toda a funcionalidade do backend. Non é necesario se escolliches Breeze ou Jetstream como kit de inicio.

- [**Sanctum**](https://laravel.com/docs/sanctum) &rarr; Un sistema de autenticación de peso para SPA (aplicacións dunha soa páxina), aplicacións móbiles e API simples baseadas en tokens. **Sempre incluído.**

- [**Passport**](https://laravel.com/docs/passport) &rarr; Unha implantación completa do servidor OAuth2 dispoñible para a túa aplicación Laravel en cuestión de minutos.

- [**Socialite**](https://laravel.com/docs/socialite) &rarr; Integracións con provedores de OAuth populares, para que os teus usuarios poidan iniciar sesión a través de Facebook, Twitter, Google e moito máis.

## Base de datos

Escolle unha das bases de [datos](https://laravel.com/docs/database) admitidas. 

- **MySQL:** a base de datos predeterminada para as aplicacións Laravel.
- **MariaDB**: o popular substituto de MySQL.
- **PostgreSQL**: Base de datos extensible e de código aberto.

Tamén podes empregar [SQLite](https://www.sqlite.org/) para crear rapidamente unha base de datos en memoria mentres executas probas, pois inclúese por defecto.

Para algunhas accións que impliquen migracións é necesario instalar o paquete `doctrine/dbal`. Se pensas, por exemplo, [modificar as columnas existentes](https://laravel.com/docs/migrations#modifying-columns) para p.ex. volvelas *null*, asegúrate de incluír o paquete [Doutrina DBAL](https://laravel.com/docs/migrations#prerequisites) &rarr; Permite a introspección avanzada de esquemas de bases de datos e a xestión de esquemas.

## Almacenamento de arquivos

Laravel integra o uso de [Flysystem](https://flysystem.thephpleague.com/) para abstraer calquera sistema de arquivos, coma o teu cartafol de almacenamento, servidores FTP remotos ou almacenamento na nube como Amazon S3 ou DigitalOcean Spaces.

Algúns sistemas de arquivos non son tan populares, polo que non se admiten sen un proceso de configuración ad hoc. Escolle os que necesites entre as seguintes opcións. Para simular un sistema de arquivos [tipo S3](https://laravel.com/docs/filesystem#amazon-s3-compatible-filesystems) , podes optar por incluír o servizo de navegación MinIO, que é API compatible con S3, pero que se executa localmente, polo que non precisa configurar o almacenamento na nube para as súas necesidades de desenvolvemento local.

- [**SFTP**](https://laravel.com/docs/filesystem#sftp-driver-configuration) &rarr; Aínda que se admite FTP desde o primeiro momento, cómpre marcar esta opción para poder utilizar o almacenamento SFTP.

**NUBE**

- [**MiniIO**](https://laravel.com/docs/sail#file-storage) &rarr; [^1]. Servizo de almacenamento de arquivos compatible coa API de Amazon S3. Útil se queres utilizar o almacenamento local "na nube", xa que será máis semellante ao teu ambiente de produción que a un sistema de arquivos local cando uses S3.
- [**Servizo de almacenamento simple de Amazon (S3)**](https://aws.amazon.com/s3) &rarr; Permite á túa aplicación almacenar arquivos en [S3 e sistemas de arquivos compatibles](https://laravel.com/docs/filesystem#amazon-s3-compatible-filesystems) , como Digital Ocean Spaces ou MinIO.

## Caché

Algunhas das tarefas de recuperación ou procesamento de datos realizadas pola túa aplicación poden consumir CPU ou tardar varios segundos en completarse. Cando este é o caso, é habitual almacenar en [caché](https://laravel.com/docs/cache) os datos recuperados durante un tempo para que poidan ser recuperados rapidamente en solicitudes posteriores dos mesmos.

O sistema de caché é bastante flexible, polo que podes escoller entre unha variedade de controladores. [Redis](https://laravel.com/docs/redis) úsase de forma predeterminada cando se configura unha nova aplicación Laravel e tamén se pode usar para outras cousas, como alimentar as túas colas en segundo plano.

**DRIVER** [Documentación](https://laravel.com/docs/cache#configuration)

- [**Redis**](https://laravel.com/docs/redis) &rarr; [^1]. Un avanzado almacén de clave-valor útil para almacenar na caché.

- [**Memcached**](https://laravel.com/docs/cache#memcached) &rarr; [^1]. Sistema de caché de obxectos de memoria distribuída de alto rendemento.

- [**DynamoDB**](https://laravel.com/docs/cache#dynamodb)Use unha táboa de DynamoDB como caché.

## Queue

Mentres creas a túa aplicación web, é posible que teñas algunhas tarefas, como analizar e almacenar un arquivo CSV cargado, que tardan demasiado en executarse durante unha solicitude web típica. Afortunadamente, Laravel permítelle crear facilmente traballos en cola que se poden procesar en segundo plano. Ao mover as tarefas que requiren moito tempo a unha cola, a túa aplicación pode responder ás solicitudes web cunha velocidade fulgurante e ofrecer unha mellor experiencia de usuario aos teus clientes.

[Laravel queues](https://laravel.com/docs/queues) fornecen unha API de filas unificada a través dunha variedade de backends de colas diferentes, como [Amazon SQS](https://aws.amazon.com/sqs) , [Redis](https://laravel.com/docs/redis) ou incluso unha base de datos relacional.

**DRIVER** [Documentación](https://laravel.com/docs/queues#introduction)

- [**Redis**](https://laravel.com/docs/redis) &rarr; [^1]. Unha tenda de clave-valor avanzada útil para almacenar na caché.

- [**Beanstalk**](https://beanstalkd.github.io/) &rarr; Unha cola de traballo sinxela e rápida.

- [**Amazon Simple Queue Service (SQS)**](https://aws.amazon.com/sqs) &rarr; Filas de mensaxes totalmente xestionadas para microservizos, sistemas distribuídos e aplicacións sen servidor.

Se decides usar Redis para as túas tarefas - *queue*-, ten sentido incluír tamén Laravel Horizon. Horizon permite supervisar facilmente as métricas clave do teu sistema de colas, coma o rendemento do traballo, o tempo de execución e os fallos dos traballos.

- [**Horizon**](https://laravel.com/docs/horizon) &rarr; Un fermoso panel de control e unha configuración baseada en código para as túas filas de Redis alimentadas por Laravel.

## Correo

Laravel ofrece soporte listo para usar para [enviar correo](https://laravel.com/docs/mail) a través `sendmail` e SMTP. Pódense instalar controladores adicionais para servizos populares como Postmark ou Mailgun. Como alternativa, pode [configurar facilmente](https://laravel.com/docs/mail#additional-symfony-transports) un dos [transportes de terceiros](https://symfony.com/doc/current/mailer.html#using-a-3rd-party-transport) compatibles con Symfony Mailer.

**DRIVER ADICIONAL** [Documentación](https://laravel.com/docs/mail#driver-prerequisites)

- [Mailgun](https://github.com/symfony/mailgun-mailer) &rarr; Integración de Mailgun para Symfony Mailer.

- [Selo de matasellos](https://github.com/symfony/postmark-mailer) &rarr; Integración de matasellos para Symfony Mailer.

- [Servizo de correo electrónico simple de Amazon (SES)](https://aws.amazon.com/de/ses/) &rarr; Un servizo de correo electrónico rendible, flexible e escalable que permite aos desenvolvedores enviar correo desde calquera aplicación.

[Mailhog](https://github.com/mailhog/MailHog) se inclúe por defecto para facilitar o desenvolvemento local. Intercepta os correos electrónicos enviados pola túa aplicación e móstraos nunha interface web sinxela.

- [Mailhog](https://laravel.com/docs/sail#previewing-emails) [^1] Intercepta e previsualiza os teus correos electrónicos localmente.

## Broadcasting

Os Websockets permiten actualizacións *en tempo* real dos eventos das túas aplicacións. Isto realízase no lado do cliente instalando [Laravel Echo](https://laravel.com/docs/broadcasting#client-side-installation) , pero o servidor necesita un compoñente de longa duración para enviar actualizacións aos clientes.

Laravel admite servizos como Pusher ou Ably, pero a comunidade tamén desenvolveu varios paquetes que che permiten aloxar o servidor websocket de forma gratuíta xunto coa túa aplicación.

**CANLE ADICIONAL**

- [**Pusher**](https://pusher.com/) &rarr; Comunicación en tempo real entre servidores, aplicacións e dispositivos

- [**Soketi**](https://soketi.app/) &rarr; Desenvolto pola comunidade. Substitución de Pusher gratuíta e autoaloxada desenvolta con Node.

- [**Ably**](https://ably.com/) &rarr; A plataforma para potenciar experiencias dixitais sincronizadas en tempo real.

## Busca

[Laravel Scout](https://laravel.com/docs/scout) ofrece unha solución sinxela e baseada en controladores para engadir busca de texto completo aos teus modelos Eloquent. Usando observadores modelo, Scout manterá automaticamente os teus índices de busca sincronizados cos teus rexistros de Eloquent.

Actualmente, Scout envíase con controladores Algolia e MeiliSearch. Escribir controladores personalizados é sinxelo, polo que tamén podes ampliar Scout coas túas propias implementacións de busca.

**DRIVER** [Documentación](https://laravel.com/docs/scout#driver-prerequisites)

- [**Personalizado**](https://laravel.com/docs/scout#custom-engines) &rarr; Está instalando ou construíndo a súa propia implementación de controladores.

- [**Base de datos**](https://laravel.com/docs/scout#database-engine) &rarr; Use as capacidades de texto completo da súa base de datos.

- [**MeiliSearch**](https://www.meilisearch.com/) &rarr; [^1]. Buscador sinxelo e sinxelo de usar.

- [**Algolia**](https://www.algolia.com/) &rarr; Potente API de busca aloxada para crear buscas e descubrimentos rápidos e relevantes.

## Ferramentas de desenvolvemento

Depurar a túa aplicación pode ser unha dor, pero Laravel ofrece algunhas ferramentas adicionais para facelo un pouco máis sinxelo. [Laravel Telescope](https://laravel.com/docs/telescope) ofrece un bonito panel de todos os eventos, solicitudes, traballos e todo o que acontece na túa aplicación.

Se te atopas entrando nos teus servidores remotos e realizando as mesmas tarefas unha e outra vez, deberías probar [Laravel Envoy](https://laravel.com/docs/envoy). Permíteche definir conxuntos de comandos localmente utilizando a sintaxe xa familiar de Blade.

- [**Telescope**](https://laravel.com/docs/telescope) &rarr; Un fermoso panel de control que proporciona información sobre as solicitudes que chegan á túa aplicación, excepcións, entradas de rexistro, consultas de bases de datos, traballos en cola, correo electrónico, notificacións, operacións de caché, tarefas programadas, volcados de variables e moito máis.

- [**Envoy**](https://laravel.com/docs/envoy) &rarr; Unha ferramenta para executar tarefas comúns que executas nos teus servidores remotos para a súa implantación, comandos de Artisan e moito máis.

## Probando - Testing

Laravel envíase con [PHPUnit](https://phpunit.de/) desde o inicio, pero algúns poden preferir usar a nova biblioteca de [Pest](https://pestphp.com/). Se activas esta opción, as probas incluídas co teu iniciador tamén usarán Pest.

Se as probas de funcións e unitarias non son suficientes, podes dar un paso máis e probar os teus sitios web cun navegador real usando [Selenium](https://www.selenium.dev/) e [Laravel Dusk](https://laravel.com/docs/dusk) .

- [**Dusk**](https://laravel.com/docs/dusk) &rarr; [^1] Unha API de proba e automatización do navegador expresiva e fácil de usar. Inclúe un servizo Sail para Selenium.
- [**Praga**](https://pestphp.com/) &rarr; [^2] Un marco de proba con interese pola sinxeleza.

## Pago e Facturación

Tratar co diñeiro, as tarxetas de crédito ou a facturación sempre dá medo. Afortunadamente, Laravel Cashier ofrece integracións propias para as populares plataformas de procesamento de pagos [Stripe](https://stripe.com/) , [Paddle](https://paddle.com/) e [Mollie](https://mollie.com/) .

Só ten que escoller unha implementación e configurar as súas credenciais. Engadiremos automaticamente capacidades de facturación ao teu modelo de usuario.

**CAIXEIRO**

- [**Stripe**](https://laravel.com/docs/billing) &rarr; Unha interface expresiva e fluída para os servizos de facturación de subscricións de Stripe.

- [**Paddle**](https://laravel.com/docs/cashier-paddle) &rarr; Unha interface expresiva e fluída para os servizos de facturación de subscricións de Paddle.

- [**Mollie**](https://www.cashiermollie.com/) &rarr; Unha interface expresiva e fluída para as subscricións que utilizan os servizos de facturación de Mollie

## Case listo

Dende a web de https://laravel.initializer.dev/ podes remitir un formulario coas condicións de inicio que queres darlle a túa aplicación con Laravel escollendo aqueles paquetes que cres van a formar parte do teu porceso de desenvovemento e produción. 

Cando remites o formulario premendo o botón vermello "Xerar", xerarase e descargarase un arquivo zip. Este arquivo contén unha versión lixeiramente axustada da aplicación Laravel predeterminada. O máis importante é que contén un script de shell que completa o proceso de inicialización e instala todos os compoñentes seleccionados. Entón, despois de descargar e descomprimir o arquivo, abra un terminal no cartafol do proxecto e execute

```
./initialize
```

Como alternativa, pode consultar o Readme xerado para obter máis instrucións. Se queres reutilizar ou compartir a túa configuración, preme o botón "Compartir" para xerar unha ligazón.

## Metadatos

Lembra poñer todo o coidado na configuración da túa a aplicación.

---

[^1]: Esta opción inclue o servizo Laravel Sail así podese desenvolver localmente nunha entorna moi similar a que empregarías emn produción

---

_.ref:_ https://laravel.initializer.dev/

