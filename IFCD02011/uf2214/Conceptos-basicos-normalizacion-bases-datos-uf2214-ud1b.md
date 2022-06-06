#### PROGRAMA DE EMPREGO

# FORMAWEB IV

| **DATA:**             | Marzo 2022                                                   |
| --------------------- | ------------------------------------------------------------ |
| **CURSO:**            | PROGRAMA DE EMPREGO<br>FORMAWEB IV                           |
| **MÓDULO**            | MF0966_3. Consulta e manipulación de información contida en xestores de datos |
| **UNIDADE FORMATIVA** | UF2214: Implementación e uso dunha base de datos             |
| **NºEXP:**            | 36/00004/2021                                                |

[TOC]

# Conceptos básicos de normalización de bases de datos

> *Ter unha comprensión básica desta terminoloxía é útil cando se discute o deseño de bases de datos relacionais.*

## Descrición da normalización

A normalización é o proceso de organizar os datos nunha base de datos. Inclúe a creación de táboas e o establecemento de relacións entre elas segundo regras deseñadas tanto para protexer os datos como para flexibilizar a base de datos eliminando a redundancia e as dependencias inconsistentes.

Os datos redundantes malgastan espazo no disco e crean problemas de mantemento. Se hai que cambiar os datos que existen en máis dun lugar, deben cambiarse exactamente do mesmo xeito en todas as súas localizacións. Un cambio no enderezo dun cliente é moito máis doado de implementar se os datos só se almacenan na táboa Clientes e non noutro lugar da base de datos.

Que é unha "dependencia inconsistente"? Aínda que é intuitivo para un usuario buscar na táboa Clientes para atopar o enderezo dun cliente en particular, quizais non teña sentido buscar alí o salario do empregado que chama a ese cliente. O salario do empregado está relacionado ou depende do empregado e, polo tanto, debe pasarse á táboa de Empregados. As dependencias inconsistentes poden dificultar o acceso porque o camiño para atopar os datos pode estar perdido ou roto.

Hai algunhas regras para normalizar unha base de datos. Cada regra chámase "forma normal". Se se cumpre a primeira regra, dise que a base de datos está na "primeira forma normal". Se se cumpren as tres primeiras regras, considérase que a base de datos está na "terceira forma normal". Aínda que son posibles outros niveis de normalización, a terceira forma normal considérase o nivel máis alto necesario para a maioría das aplicacións.

Como ocorre con moitas outras regras e especificacións formais, os estándares non sempre se cumpren perfectamente nos escenarios do mundo real. En xeral, a normalización require táboas adicionais, e algúns clientes consideran que isto é unha cantidade significativa de traballo. Se decide infrinxir unha das tres primeiras regras de normalización, asegúrese de que a súa aplicación prevé problemas que poidan xurdir, como datos redundantes e dependencias inconsistentes.

Os exemplos inclúense nas seguintes descricións.

## primeira forma normal

- Elimina os grupos que se repiten das táboas individuais.
- Crea unha táboa separada para cada conxunto de datos relacionados.
- Identifica cada conxunto de datos relacionados cunha clave primaria.

Non use varios campos nunha soa táboa para almacenar datos similares. Por exemplo, para rastrexar un artigo de inventario que procede de dúas posibles fontes, un rexistro de inventario pode conter campos para o Código de provedor 1 e o Código de provedor 2.

Que ocorre cando se engade un terceiro provedor? Engadir un campo non é a resposta, require modificacións nas táboas e no programa e non admite facilmente un número variable de provedores. En vez diso, coloque toda a información do provedor nunha táboa separada chamada Provedores e, a continuación, ligue o inventario a provedores co número de artigo como clave, ou vendedores ao inventario co código de provedor como clave.

## segunda forma normal

- Cree táboas separadas para conxuntos de valores que se apliquen a varios rexistros.
- Relaciona estas táboas cunha chave estranxeira.

Os rexistros non deben depender doutra cousa que non sexa unha chave primaria dunha táboa, unha chave composta se é necesario. Por exemplo, considere o enderezo dun cliente nun sistema de contabilidade. O enderezo é necesario na táboa Clientes, pero tamén nas táboas Pedidos, Envíos, Facturas, Contas por cobrar e Cobros. En lugar de almacenar o enderezo dun cliente como unha entrada separada en cada unha destas táboas, gárdao nun só lugar, xa sexa na táboa Clientes ou nunha táboa de Enderezos separada.

## terceira forma normal

- Elimina os campos que non dependen da clave.

Os valores dun rexistro que non forman parte da chave dese rexistro non pertencen á táboa. En xeral, sempre que o contido dun grupo de campos poida aplicarse a máis dun único rexistro da táboa, considere colocar estes campos nunha táboa separada.

Por exemplo, nunha táboa de contratación de empregados, pode incluír o nome da universidade e o enderezo dun candidato. Pero necesitas unha lista completa de facultades para enviar correos electrónicos de grupo. Se a información sobre a facultade se almacena na táboa de candidatos, non hai forma de enumerar as facultades que actualmente non teñen candidatos. Crea unha táboa de Universidades separada e vinculala á táboa de Candidatos co código da universidade como clave.

EXCEPCIÓN: Cumprir a terceira forma normal, aínda que teoricamente desexable, non sempre é práctico. Se tes unha táboa de Clientes e queres eliminar todas as posibles dependencias entre os campos, debes crear táboas separadas para cidades, códigos postales, representantes de vendas, clases de clientes e calquera outro factor que poida duplicarse en varios rexistros. En teoría, a normalización vale o traballo que supón. Non obstante, moitas táboas pequenas poden degradar o rendemento ou superar a capacidade de memoria ou abrir ficheiros.

Pode ser máis factible aplicar a terceira forma normal só aos datos que cambian con frecuencia. Se quedan campos dependentes, deseña a aplicación para que solicite ao usuario que comprobe todos os campos relacionados cando algún deles cambie.

## Outras formas de normalización

Existen a cuarta forma normal, tamén chamada Boyce Codd Normal Form (BCNF), e a quinta forma normal, pero raramente se consideran no deseño real. Se non se aplican estas regras, o deseño da base de datos pode ser menos que perfecto, pero non debería afectar á funcionalidade.

## Normalizar unha táboa de exemplo

Estes pasos demostran o proceso de normalización dunha táboa de estudantes ficticia.

1. Táboa non normalizada:

   | Nº alumno | Titor  | Despacho-Tit | Clase1 | Clase2 | Clase3 |
   | :-------- | :----- | :----------- | :----- | :----- | :----- |
   | 22:10     | García | 4:12         | 101-07 | 143-01 | 159-02 |
   | 4123      | Díaz   | 216          | 101-07 | 143-01 | 179-04 |

2. Primeira forma normal: sen grupos repetitivos

   As táboas só deben ter dúas dimensións. Dado que un alumno ten varias clases, estas clases deben aparecer nunha táboa separada. Os campos *Clase1*, *Clase2* e *Clase3* dos rexistros anteriores son indicativos dun problema de deseño.

   As follas de cálculo adoitan usar a terceira dimensión, pero as táboas non deberían. Outra forma de ver ese problema é cunha relación un-a-moitos e poñer o un e o varios lados en táboas separadas. En vez diso, cree outra táboa na primeira forma normal eliminando o grupo repetido (*Clase #*), como se mostra a continuación:

   | Nº alumno | Titor  | Despacho-Tit | Nº clase |
   | :-------- | :----- | :----------- | :------- |
   | 22:10     | García | 4:12         | 101-07   |
   | 22:10     | García | 4:12         | 143-01   |
   | 22:10     | García | 4:12         | 159-02   |
   | 4123      | Díaz   | 216          | 101-07   |
   | 4123      | Díaz   | 216          | 143-01   |
   | 4123      | Díaz   | 216          | 179-04   |

3. Segunda forma normal: eliminar datos redundantes

   Observe os distintos valores de *Clase#* para cada valor de *#* na táboa anterior. A clase # non depende funcionalmente de *Alumno#* (a chave primaria), polo que a relación non está na segunda forma normal.

   As seguintes táboas mostran a segunda forma normal:

  Alumnos:
 | Nº alumno | Tutor  | Despacho-Tut |
 | :-------- | :----- | :----------- |
 | 22:10     | García | 4:12         |
 | 4123      | Díaz   | 216          |

 Rexistro:
 | Nº alumno | Nº clase |
 | :-------- | :------- |
 | 22:10     | 101-07   |
 | 22:10     | 143-01   |
 | 22:10     | 159-02   |
 | 4123      | 101-07   |
 | 4123      | 143-01   |
 | 4123      | 179-04   |

4. Terceira forma normal: eliminar datos que non dependen da clave

   No último exemplo, *Despacho-Tit* (número do despacho do titor) depende funcionalmente do atributo Titor. A solución é pasar ese atributo da táboa Estudantes á táboa Persoal, como se mostra a continuación:

   Alumnos:

   | Nº alumno | Titor  |
   | :-------- | :----- |
   | 22:10     | García |
   | 4123      | Díaz   |

   Personal:

   | Nome   | Sala | Dept. |
   | :----- | :--- | :---- |
   | García | 4:12 | 42    |
   | Díaz   | 216  | 42    |


---
Fonte: https://docs.microsoft.com/es-es/office/troubleshoot/access/database-normalization-description

Maís info: [Normalización de bases de datos](https://es.wikipedia.org/wiki/Normalización_de_bases_de_datos)



----

MRZ 2022



![Programas de emprego Xunta de Galicia - Concello de Vigo 2021-2022](C:\laragon\www\uf2213\assets\A-VIGO-CIERRE-Obradoiros-20-21.jpg)