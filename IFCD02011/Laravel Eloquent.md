## Laravel Eloquent

Laravel ben empaquetado con ***Eloquent* Object Relational Mapper (ORM)**, que proporciona un xeito moi sinxelo de comunicarse cunha base de datos. Unha axuda de Laravel para facer o desenvolvemento máis rápido. Eloquent ofrece unha solución axeitada á maioría dos problemas atopados, e funciona con aplicacións web personalizadas xa que pode atender a varias bases de datos e realizar operacións comúns de bases de datos. 

## Como funciona Eloquent? 

Os desenvolvedores poden traballar en Eloquent con varias bases de datos de forma eficiente usando unha implementación ActiveMethod. É un *patrón arquitectónico* onde o **modelo** creado na estrutura Model-View-Controller (MVC) corresponde a unha **táboa** da base de datos. A vantaxe é que os modelos realicen operacións comúns de bases de datos sen codificar longas consultas SQL. Os modelos permiten a consulta de datos nas túas táboas, así como a inserción de novos rexistros nas táboas. Simplifícase o proceso de sincronización de varias bases de datos que se executan en diferentes sistemas. Non é necesario escribir consultas SQL en absoluto. Todo o que tes que facer é **definir táboas de bases de datos e relacións entre elas**, e Eloquent fará o resto do traballo. 

### Configuración de Laravel 

Para apreciar plenamente a utilidade de Eloquent ORM, é imprescindible comprender o ecosistema.  Estes son os pasos para comezar: 

1. Instala Laravel desde getcomposer.org 
2. Crea migracións usando a consola Artisan 
3. Crea modelos elocuentes 
4. Sementa a base de datos 

Artisan Console é o nome da interface de liña de comandos empaquetada con Laravel. Ofrece unha serie de comandos útiles para ser usados durante o desenvolvemento da túa aplicación. Está dirixido polo poderoso compoñente Symfony Console. 

Para ver unha lista de todos os comandos Artisan dispoñibles, podes usar o comando list: 

```bash
php artisan list
```

Todos os comandos veñen cunha descrición concisa dos seus argumentos e opcións. Isto móstrase nunha pantalla de "axuda". Para ver unha pantalla de axuda, simplemente precede o nome do comando con "axuda" como se mostra: 

```bash
php artisan help migrate 
```

### Migración 

A migración é un proceso de xestión da base de datos con guións PHP en lugar de consultas SQL. Que tamén ofrece unha forma de engadir control de versións á base de datos.  Antes da migración debe existir a base de datos e estar en funcionamento. Asumindo que a base de datos está funcionando, para comezar coas migracións, cómpre configurar a(s) migración(s) en Laravel. Para crear unha migración, só tes que executar o seguinte comando: 

```bash
php artisan make:migration create_student_records 
```

Isto crea o arquivo de migración. No teu editor de texto, abre o arquivo que acabadas de crear no cartafol ``migration``: 

```php
<?php
use IlluminateSupportFacadesSchema;
use IlluminateDatabaseSchemaBlueprint;
use IlluminateDatabaseMigrationsMigration;

class CreateStudentRecordsTable extends Migration
{
    /**
    * Run the migrations.
    *
    * @return void
    */
    public function up()
    {
        Schema::create('student__records', function (Blueprint $table) {
            $table->increments('id');
            $table->timestamps();
        });
    }

    /**
    * Reverse the migrations.
    *
    * @return void
    */
    public function down()
    {
        Schema::dropIfExists('student__records');
    }
}
```

O código mostra unha clase co mesmo nome `create_student_records` e ten dous métodos: `up` e `down`. O método `up` deberá encargarse dos cambios na base de datos; polo que sempre que migres a túa base de datos, executarase o código que estea no método ``up``. Por outro lado, o método ``down`` deberá reverter os cambios na base de datos; polo que sempre que retroceda a migración, o método ``down`` deberá desfacer o que fixo o método ``up``. Dentro do método ``up`` está o creador de esquemas que se usa para crear e manipular táboas. 

Que pasará se desfas algunhas das túas migracións? Todo o que tes que facer é executar o comando: 

```bash
php artisan migrate:rollback 
```

Isto retraerá a última migración que se estaba a implementar. Ademais, pode restablecer completamente a base de datos executando: 

```bash
php artisan migrate:reset
```

Isto desfará todas as túas migracións. 

### Definición de modelos elocuentes 

Despois de rematar coa migración da base de datos, o seguinte proceso é a sementeira. Eloquent entra en escena xa que sementar é inserir rexistros na nosa base de datos. Polo tanto, terás que crear os teus modelos antes de sementar a base de datos. **Cada táboa da base de datos ten un modelo correspondente que se usa para interactuar con esa táboa**. Os modelos permítenche consultar datos nas túas táboas, así como inserir novos rexistros na táboa. A forma máis sinxela de crear unha instancia de modelo é usar o seguinte comando: 

```bash
php artisan make:model Student
```

A continuación móstrase un exemplo dun modelo de ``Student``, que se pode usar para recuperar e almacenar información da táboa de base de datos do noso alumno: 

```php
<?php
namespace App;
use IlluminateDatabaseEloquentModel;

class Student extends Model
{
    //
} 
```

Cando xeras un modelo e ao mesmo tempo queres xerar unha migración de base de datos, podes empregar no teu comando Artisan o marcador  ``–migration`` ou ``-m`` : 

```bash
php artisan make:model Student --migration

php artisan make:model Student -m
```

### Alcouves ou sementeiros

Os alcouves ou ``seeders``, son un tipo de clase que se ocupa de encher a base de datos. O bo dos ``seeders`` é que se poden executar para actualizar a base de datos mediante un simple comando, axudan a erradicar erros tipográficos, reducen as tarefas repetitivas de actualización e manexo de datos,...

A idea básica detrás dos alcouves é axudar ao problema dos "datos sucios". Os sementeiros xerais son un conxunto especial de clases que nos permiten encher a nosa base de datos unha e outra vez cos mesmos datos exactos.  Imos implementar o seguinte comando: 

```bash
php artisan make:seeder StudentsRecordSeeder
```

No editor de texto, baixo o cartafol `seeds`, abre o arquivo acabado de crear co nome de: ``StudentsRecordSeeder.php``. Como podes ver, esta é só unha clase moi sinxela cun só método chamado ``run()``. 

```php
<?php
use IlluminateDatabaseSeeder;

class StudentsRecordSeeder extends Seeder
{
    /**
    * Run the database seeds
    * @return void
    */

    public function run()
    {
        //
    }
}
```

O código é só un envoltorio arredor dunha clase de comandos da consola, feito especificamente para axudar coa tarefa de sementeira. Modifica o código e despois gárdao. 

```php
public function run()
{
    echo 'Sementando!';
}
```

E volvendo á terminal, executa: 

```bash
php artisan db:seed --class=StudentsRecordSeeder
```

Isto é só chamar a fachada de base de datos, pero ten en conta que aquí non hai interacción real con base de datos. Agora podes encher a táboa con algunhas entradas e executar: 

```bash
php artisan db:seed --class=class=StudentsRecordSeeder 
```

Aquí podes seguir eliminando, engadindo, editando entradas mentres traballas e despois restablecelas cun simple comando. 

### CRUD con  Eloquent

As operacións CRUD baixo o mapeador relacional de obxectos (ORM) Eloquent facilitan aos desenvolvedores de Laravel traballar con varias bases de datos. Realiza operacións de creación, recuperación, actualización e eliminación (CRUD), así como mapea modelos de obxectos a táboas de bases de datos.  Manexa toda a interacción da base de datos necesaria para as operacións CRUD. 

#### Creación de rexistros 

Podes usar o método ``::create`` para inserir un novo rexistro na base de datos. 

```php
student_record::create(array(
    'first_name' => 'John',
    'last_name'  => 'Doe',
    'student_rank' => 1
));
```

Ademais do simple método de creación que se mostra arriba, tamén se pode crear un novo obxecto e asignarlle diferentes atributos. Despois, podes chamar á función ``save()`` e executar o código. Métodos como ``firstOrCreate()`` ou ``firstOrNew()`` son outras opcións para crear rexistros. Estes permitirán atopar un alumno con certos atributos; se non se atopa ese alumno, crearao na base de datos ou creará unha instancia nova. 

#### Recuperando rexistros 

Usando Eloquent ORM, obter e atopar rexistros da base de datos é manexable e sinxelo. As consultas son simplemente construídas e ofrecen un fluxo suave. Para crear instrucións ``::where``, empregará os métodos ``get()`` e ``first()``. O método ``first()`` devolverá só un rexistro, mentres que o método ``get() `` devolverá unha matriz de rexistros que podes recorrer. Ademais, o método ``find()`` pódese usar cunha matriz de claves primarias, que devolverá unha colección de rexistros coincidentes. Aquí tes algúns exemplos: 

```php
$student = Students::all();
```

Este código recibe todos os estudantes. Mentres que o código a continuación, atopa un alumno específico polo seu ID: 

```php
$student = Students::find(1);
```

Ademais, como se mostra a continuación, o código describe como atopar un alumno en función dun atributo específico. 

```php
$JohnDoe = Students::where('name', '=', 'John Doe')->first();
```

Para o método get(), este código mostra como atopar un alumno cun nivel de clasificación superior a 5. 

```php
$rankStudents = Student::where('student_rank', '>', 5)->get();
```

#### Actualizando rexistros 

Actualizar rexistros usando Eloquent é ben sinxelo. Para actualizar un rexistro, só tes que buscar o rexistro que queres actualizar, cambiar os atributos e gardar. Por exemplo, para cambiar o nivel de clasificación do alumno de John Doe a 5, primeiro busca o alumno e despois executa o método de gardar. 

```php
$JohnDoe = Bear::where('name', '=', 'John Doe')->first();
$JohnDoe->danger_level = 5;
$JohnDoe->save(); 
```

O método de gardar tamén se pode usar para actualizar modelos que xa existen na base de datos. 

#### Eliminando rexistros 

Eloquent presume do seu sinxelo proceso de actualización de rexistros, o mesmo que do proceso de eliminación. Hai dúas opcións: gravar unha extracción e executar o método de eliminación, ou simplemente usar o método de destrución. Para buscar e eliminar un rexistro, simplemente executa os seguintes comandos: 

```php
$student = Students::find(1);
$student->delete();
```

Para eliminar un rexistro e varios rexistros, execútanse os comandos: 

```php
Students::destroy(1);
Students::destroy(1, 2, 3);
```

Ter en conta que os parámetros de destrución son só claves primarias a diferenza do método de eliminación que pode aceptar calquera columna da base de datos. 

Para buscar e eliminar todos os estudantes cun nivel de clasificación superior a 10. 

```php
Students::where('student_rank', '>', 10)->delete();
```



Escribindo unha aplicación web en PHP, os desenvolvedores teñen a opción de escoller entre unha rica lista de frameworks PHP. A demanda en curso combinada con varias estatísticas de uso publicadas por comunidades suxiren que Laravel é actualmente máis popular que outros frameworks PHP. Non obstante, os desenvolvedores web experimentados nunca elixen un marco PHP en función da súa popularidade ou bombo. Hai pros e contras a considerar. Moitos desenvolvedores tenden a restar importancia á popularidade de PHP, pero ten en conta que debes escoller un marco PHP que se axuste a todos os requisitos do proxecto. Tamén como programador, é importante utilizar un marco PHP, xa que Laravel axúdache a reducir o custo de desenvolvemento de aplicacións web. 

As robustas funcións e ferramentas proporcionadas por Eloquent dentro de Laravel facilitan aos desenvolvedores a creación de aplicacións web personalizadas segundo os requisitos especificados.  Eloquent ofrece un xeito eficiente de comunicarse cunha base de datos. As consultas SQL da túa aplicación á base de datos son moi críticas. Por exemplo, unha empresa pode ter un estándar sobre o tempo de execución da consulta SQL. Se unha consulta supera os 50 ms e, segundo o seu estándar, se considera unha consulta lenta, un programador debe realizar a optimización da consulta o antes posible. O tempo é moi crítico neste escenario, polo que un programador necesita axuda para atopar onde e que causa a consulta lenta. Así, Retrace pode axudar realmente aos desenvolvedores respondendo as preguntas onde e que. 

![img](https://stackify.com/wp-content/uploads/2018/09/word-image-93.png)
 ![img](https://stackify.com/wp-content/uploads/2018/09/word-image-94.png)

As consultas lentas pódense rastrexar en milisegundos na columna Took (ms) e cada duración vai acompañada das solicitudes web. Así, cando se detecta unha consulta lenta, os seus atributos correspondentes indícanse directamente. 

### Conclusión 

PHP é unha linguaxe poderosa. Laravel considérase un marco PHP ben coñecido e robusto. Laravel con Eloquent ofrece unha tecnoloxía competitiva para aplicacións web.

----

### Máis información 

Stackify [blog ](https://stackify.com/blog/)ofrece artigos que che axudarán a optimizar o PHP e o rendemento que poden ser útiles nas túas aplicacións PHP. 

- [Os 8 principais provedores de PaaS para implementar aplicacións PHP ](https://stackify.com/paas-providers-php/)
- [Principais sitios e recursos de titoriais de Laravel ](https://stackify.com/laravel-tutorial-sites-resources/)
- [18 Ferramentas PHP para desenvolvedores de todos os niveis ](https://stackify.com/php-tools-developers/)

---

