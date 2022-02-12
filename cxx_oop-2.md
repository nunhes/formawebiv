# Programación Orientada a Obxectos en PHP- Resumen

------

Podemos imaxinar o noso universo feito de diferentes obxectos coma o sol, a terra, a lúa, etc. Do mesmo xeito, podemos imaxinar o noso coche feito de diferentes obxectos como a roda, a dirección, o engrenaxe, etc. Do mesmo xeito, na programación orientada a obxectos dalgún xeito se asume que todo pode ser considerado un obxecto, daquela se pode implementar un software no que se empreguen diferentes obxectos.

## Conceptos orientados a obxectos

Antes de entrar en detalle, imos definir termos importantes relacionados coa programación orientada a obxectos.

- **Clase (*Class*)** - Este é un tipo de datos definido polo programador, que inclúe funcións locais e datos locais. Podes pensar nunha clase como nun modelo para facer moitas instancias do mesmo tipo (ou clase) de obxecto.
- **Obxecto (*Object*)**: Unha instancia individual da estrutura de datos definida por unha clase. Defines unha clase unha vez, e despois creas moitos obxectos que lle pertencen. Os obxectos tamén se coñecen como instancia.
- **Variable membro (*Member Variable*)** - Estas son as variables definidas dentro dunha clase. Estes datos serán invisibles para o exterior da clase e pódense acceder a través das funcións dos membros. Estas variables chámanse atributo do obxecto unha vez que se crea.
- **Función membro (*Member function*)** : son as funcións definidas dentro dunha clase e utilízanse para acceder aos datos do obxecto.
- **Herdanza (*Inheritance*)** - Cando unha clase se define herdando a función existente dunha clase pai, entón emprégase a herdanza. Aquí a clase filla herdará todas ou algunhas funcións e variables membro da clase pai.
- **Clase pai (*Parent class*)** : unha clase que é herdada por outra clase. Isto tamén se chama clase base ou superclase.
- **Clase fillo (*Child class*):** unha clase que herda doutra clase. Isto tamén se denomina subclase ou clase derivada.
- **Polimorfismo (*Polymorphism*)**: Este é un concepto orientado a obxectos onde a mesma función se pode usar para diferentes propósitos. Por exemplo, o nome da función poderá seguir sendo o mesmo pero poderá levar un número diferente de argumentos e facer tarefas diferentes.
- **Sobrecarga** (***Overloading***): é un tipo de polimorfismo no que algúns ou todos os operadores teñen implementacións diferentes dependendo dos tipos dos seus argumentos. Do mesmo xeito, as funcións tamén se poden sobrecargar con diferentes implementacións.
- **Abstracción de datos (*Data Abstraction*)**: Calquera representación de datos na que se oculten (abstraídos) os detalles da implementación.
- **Encapsulación (*Encapsulation*)**: refírese a un concepto no que encapsulamos todos os datos e as funcións membros xuntos para formar un obxecto.
- **Construtor (*Constructor*)**: refírese a un tipo especial de función que se chamará automaticamente sempre que haxa unha formación de obxecto a partir dunha clase.
- **Destrutor (*Destructor*)**: refírese a un tipo especial de función que se chamará automaticamente sempre que se elimine un obxecto ou quede fóra do alcance.

## Definición de clases con PHP

A forma xeral para definir unha nova clase en PHP é a seguinte:

```php
<?php
   class phpClass {
      var $var1;
      var $var2 = "constant string";
      
      function myfunc ($arg1, $arg2) {
         [..]
      }
      [..]
   }
?>
```

- A palabra reservada **class**, seguida do nome da clase que se quere definir.
- Un conxunto de chaves ``{ .... }`` que inclúen calquera número de declaracións de variables e definicións de funcións.
- As declaracións de variables comezan coa forma especial **var** , que vai seguida dun nome de variable ``$`` convencional; poden ter, ou non, unha asignación inicial a un valor constante.
- As definicións de función parécense moito ás funcións autónomas de PHP, pero son locais da clase e empregaranse para establecer e acceder aos datos do obxecto.

### Exemplo
Aquí tes un exemplo que define unha clase de tipo Libros −
```php
<?php
   class Libros {
      /* Member variables */
      var $price;
      var $title;
      
      /* Member functions */
      function setPrice($par){
         $this->price = $par;
      }
      
      function getPrice(){
         echo $this->price ."<br/>";
      }
      
      function setTitle($par){
         $this->title = $par;
      }
      
      function getTitle(){
         echo $this->title ." <br/>";
      }
   }
?>
```

A variable **$this** é unha variable especial e refírese ao mesmo obxecto de seu.

## Creando obxectos en PHP

Unha vez que definiches a túa clase, podes crear tantos obxectos como queiras deste tipo de clase. 

Un exemplo de como crear un obxecto usando o operador **new .**

```php
$physics = new Libros;
$maths = new Libros;
$chemistry = new Libros;
```

Aquí creamos tres obxectos e estes son independentes entre si e terán a súa existencia por separado. A continuación veremos como acceder á función membro e procesar as variables dos membros.

## Chamada ás funcións membro

Despois de crear os teus obxectos, poderás chamar funcións membro relacionadas con ese obxecto. Unha función membro só poderá procesar a variable membro do obxecto relacionado.

O seguinte exemplo amosa como establecer o título e os prezos dos tres libros chamando ás funcións membro da clase.

```php
$physics->setTitle( "Physics for High School" );
$chemistry->setTitle( "Advanced Chemistry" );
$maths->setTitle( "Algebra" );

$physics->setPrice( 10 );
$chemistry->setPrice( 15 );
$maths->setPrice( 7 );
```

Agora chamas a outras funcións membro para obter os valores establecidos no exemplo anterior:

```php
$physics->getTitle();
$chemistry->getTitle();
$maths->getTitle();
$physics->getPrice();
$chemistry->getPrice();
$maths->getPrice();
```

Isto producirá o seguinte resultado −

```bash
Physics for High School
Advanced Chemistry
Algebra
10
15
7
```

## Funcións do construtor

As funcións de construtor son un tipo especial de funcións que se chaman automaticamente sempre que se crea un obxecto. Así que aproveitamos ao máximo este comportamento, inicializando moitas cousas mediante funcións de construtor.

PHP proporciona unha función especial chamada **__construct()** para definir un construtor. Podes pasarlle tantos argumentos como queiras á función de construtor.

O seguinte exemplo creará un construtor para a clase Libros e inicializará o prezo e o título do libro no momento da creación do obxecto.

```php
function __construct( $par1, $par2 ) {
   $this->title = $par1;
   $this->price = $par2;
}
```

Agora non necesitamos chamar á función ``set`` por separado para establecer o prezo e o título. Podemos inicializar estas dúas variables membro só no momento da creación do obxecto. Como no seguinte exemplo:

```php
$physics = new Libros( "Physics for High School", 10 );
$maths = new Libros ( "Advanced Chemistry", 15 );
$chemistry = new Libros ("Algebra", 7 );

/* Get those set values */
$physics->getTitle();
$chemistry->getTitle();
$maths->getTitle();

$physics->getPrice();
$chemistry->getPrice();
$maths->getPrice();
```

Isto producirá o seguinte resultado:

```
  Physics for High School
  Advanced Chemistry
  Algebra
  10
  15
  7
```

## Destrutor

Como unha función de construtor, pode definir unha función de destrución usando a función **__destruct()** . Podes liberar todos os recursos dentro dun destrutor.

## Herdanza

As definicións de clase PHP poden herdar, opcionalmente, dunha definición de clase pai mediante a cláusula extends. A sintaxe é a seguinte:

```php
class Child extends Parent {
   <definition body>
}
```

O efecto da herdanza é que a clase filla (ou subclase ou clase derivada) ten as seguintes características:

- Ten automaticamente todas as declaracións de variables membro da clase pai.
- Ten automaticamente todas as mesmas funcións membro que o pai, que (por defecto) funcionará do mesmo xeito que esas funcións no pai.

O seguinte exemplo herda a clase de Libros e engade máis funcionalidade segundo o requisito.

```php
class Novel extends Libros {
   var $publisher;
   
   function setPublisher($par){
      $this->publisher = $par;
   }
   
   function getPublisher(){
      echo $this->publisher. "<br />";
   }
}
```

Agora, ademais das funcións herdadas, a clase Novel mantén dúas funcións membros adicionais.

## Anulación de funcións

As definicións de función nas clases fillo anulan as definicións co mesmo nome nas clases principais. Nunha clase filla, podemos modificar a definición dunha función herdada da clase pai.

No seguinte exemplo, as funcións ``getPrice`` e ``getTitle`` son substituídas para devolver algúns valores.

```
function getPrice() {
   echo $this->price . "<br/>";
   return $this->price;
}
   
function getTitle(){
   echo $this->title . "<br/>";
   return $this->title;
}
```

## Membros públicos

A menos que se especifique o contrario, as propiedades e os métodos dunha clase son públicos. É dicir, pódese acceder a eles en tres posibles situacións:

- Desde fóra da clase na que se declara
- Desde dentro da clase na que se declara
- Desde dentro doutra clase que implementa a clase na que se declara

Ata agora vimos todos os membros como membros públicos. Se queres limitar a accesibilidade dos membros dunha clase, definirás os membros da clase como **privados** ou **protexidos** .

## Membros privados

Ao designar un membro como privado, limitas a súa accesibilidade á clase na que se declara. Non se pode facer referencia ao membro privado desde as clases que herdan a clase na que se declara e non se pode acceder desde fóra da clase.

Un membro da clase pódese facer privado usando a palabra clave **privada** diante do membro.

```php
class UnhaClase {
   private $automobil = "skoda";
   $driver = "SRK";
   
   function __construct($par) {
      // As instrucións definidas aquí
      // execútanse cada vez
      // que se crea unha instancia da clase.
   }
   
   function minhaFuncionPublica() {
      return("Eu son visible!");
   }
   
   private function minhaFuncionPrivada() {
      return("Eu non son visible fora de aquí!");
   }
}
```

Cando outra clase herda a clase *UnhaClase* mediante ``extends``, ``minhaFuncionPublica()`` estará visible, igual que ``$driver``. A clase ampliada non terá coñecemento nin acceso a minhaFuncionPrivada e $automobil, porque se declaran privadas.

## Membros protexidos

Unha propiedade ou método protexido é accesible na clase na que se declara, así como nas clases que estenden esa clase. Os membros protexidos non están dispoñibles fóra destes dous tipos de clases. Pódese protexer un membro da clase usando a palabra clave **protexida** diante do membro.

Aquí tes unha versión diferente de UnhaClase −

```php
class UnhaClase {
   protected $automobil = "skoda";
   $driver = "SRK";

   function __construct($par) {
      // As instrucións definidas aquí
      // execútanse cada vez
      // que se crea unha instancia da clase.
   }
   
   function minhaFuncionPublica() {
      return("Eu son visible!");
   }
   
   protected function minhaFuncionPrivada() {
      return("Eu non son visible na clase fillo!");
   }
}
```

## Interfaces

As interfaces defínense para proporcionar nomes de función comúns aos implementadores. Diferentes implementadores poden implementar esas interfaces segundo os seus requisitos. Podes dicir que as interfaces son esqueletos que son implementados polos desenvolvedores.

A partir de PHP5, é posible definir unha interface, como esta:

```php
interface Mail {
   public function sendMail();
}
```

Entón, se outra clase implementou esa interface, así:

```php
class Report implements Mail {
   // sendMail() Definition goes here
}
```

## Constantes

Unha constante é algo parecido a unha variable, xa que contén un valor, pero en realidade é máis como unha función porque unha constante é inmutable. Unha vez que declara unha constante, non cambia.

Declarar unha constante é doado, como se fai nesta versión de UnhaClase −

```php
class UnhaClase {
   const requiredMargin = 1.7;
   
   function __construct($incomingValue) {
      // As instrucións definidas aquí
      // execútanse cada vez
      // que se crea unha instancia da clase.
   }
}
```

Nesta clase, requiredMargin é unha constante. Declárase coa palabra clave const, e en ningún caso se pode cambiar a outra cousa que non sexa 1.7. Teña en conta que o nome da constante non ten un $ inicial, como os nomes das variables.

## Clases abstractas

Unha clase abstracta é aquela que non pode ser instanciada, só herdada. Declaras unha clase abstracta coa palabra clave **abstract** , como esta −

Cando se herda dunha clase abstracta, tódolos métodos marcados como *abstracts* na declaración de clase do pai deben ser definidos polo fillo; ademais, estes métodos deben definirse coa mesma visibilidade.

```php
abstract class MinhaClaseAbstracta {
   abstract function MinhaFuncionAbstracta() {
   }
}
```

Teña en conta que as definicións de función dentro dunha clase abstracta tamén deben ir precedidas da palabra clave ``abstract``. Non é legal ter definicións de funcións abstractas dentro dunha clase non abstracta.

## Palabra clave estática

Declarar membros da clase ou métodos como estáticos fainos accesibles sen necesidade dunha instanciación da clase. Non se pode acceder a un membro declarado como estático cun obxecto de clase instanciado (aínda que un método estático sí).

Proba o seguinte exemplo:

```php
<?php
   class Foo {
      public static $my_static = 'foo';
      
      public function staticValue() {
         return self::$my_static;
      }
   }
	
   print Foo::$my_static . "\n";
   $foo = new Foo();
   
   print $foo->staticValue() . "\n";
?>	
```

## Palabra clave final

PHP5 introduce a palabra clave final, que impide que as clases fillas anulen un método prefixando a definición con final. Se a propia clase está a ser definida como final, non se pode ampliar.

O seguinte exemplo da como resultado un erro fatal: non se pode anular o método final BaseClass::moreTesting()

```php
<?php

   class BaseClass {
      public function test() {
         echo "BaseClass::test() called<br>";
      }
      
      final public function moreTesting() {
         echo "BaseClass::moreTesting() called<br>";
      }
   }
   
   class ChildClass extends BaseClass {
      public function moreTesting() {
         echo "ChildClass::moreTesting() called<br>";
      }
   }
?>
```

## Chamando aos construtores pais

En lugar de escribir un construtor totalmente novo para a subclase, escribimos chamando explícitamente ao construtor do pai e despois facendo o que sexa necesario ademais para a instanciación da subclase. Aquí tes un exemplo sinxelo:

```php
class Name {
   var $_firstName;
   var $_lastName;
   
   function Name($first_name, $last_name) {
      $this->_firstName = $first_name;
      $this->_lastName = $last_name;
   }
   
   function toString() {
      return($this->_lastName .", " .$this->_firstName);
   }
}
class NameSub1 extends Name {
   var $_middleInitial;
   
   function NameSub1($first_name, $middle_initial, $last_name) {
      Name::Name($first_name, $last_name);
      $this->_middleInitial = $middle_initial;
   }
   
   function toString() {
      return(Name::toString() . " " . $this->_middleInitial);
   }
}
```

Neste exemplo, temos unha clase pai (``Name``), que ten un construtor de dous argumentos, e unha subclase (``NameSub1``), que ten un construtor de tres argumentos. O construtor de ``NameSub1`` funciona chamando ao seu construtor pai de forma explícita usando a sintaxe ``::`` (pasando dous dos seus argumentos) e despois establecendo un campo adicional. Do mesmo xeito, ``NameSub1`` define a súa función non construtora ``toString()`` en termos da función pai que anula.

**NOTA** − Un construtor pódese definir co mesmo nome que o nome dunha clase. Defínese no exemplo anterior.



____

_ref:_: https://www-tutorialspoint-com.translate.goog/php/php_object_oriented.htm



TEST

https://www.writephponline.com/



PHP Avanzado

https://designpatternsphp.readthedocs.io/en/latest/Creational/AbstractFactory/README.html