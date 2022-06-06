# EXERCICIO

Exercicio resolto cunha táboa
Imos facer un exercicio de repaso de comandos que faga diferentes manipulacións sobre unha soa táboa. Será unha táboa que contén os datos do produto: código, nome, prezo e data de rexistro, para que poidamos traballar con datos de **texto**, **tipo numérico** e de **data**.

Os pasos que levaremos a cabo serán:

- Crear a base de datos
- Comezar a usala
- Introducir 3 datos de mostra
- Mostrar todos os datos
- Mostrar datos que teñan un nome determinado
- Mostrar datos que comezan cunha inicial determinada
- Ver só o nome e o prezo dos que cumpren unha condición (prezo > 22)
- Consultar o prezo medio daqueles produtos cuxo nome comeza por "Cadeira"
- Modificar a estrutura da táboa para engadir un novo campo: "categoría"
- Darlle o valor "ferramenta" á categoría de todos os produtos existentes
- Modificar os produtos que comezan pola palabra "cadeira", para que a súa categoría sexa "cadeira"
- Ver a lista de categorías (sen que aparezan datos duplicados)
- Consulta cantos produtos temos en cada categoría



Vexamos como:

Damos por sentado que MySQL está instalado. El primer paso es crear la base de datos:



```sql
create database produtos1;
```



E comenzar a usala bd recen creada:



```sql
use produtos1;
```



Crear a táboa de datos que imos empregar:



```sql
create table produtos (
  codigo varchar(3),
  nome varchar(30),
  prezo float(6,2),
  dataalta date,
  primary key (codigo)
);
```



Para introducir varios datos de exemplo:



```sql
insert into produtos values ('a01','Afiador', 2.50, '2007-11-02');
insert into produtos values ('s01','Cadeira mod. ZAZ', 20, '2007-11-03');
insert into produtos values ('s02','Cadeira mod. XAX', 25, '2007-11-03');
insert into produtos values ('a02','Arador', 3.30, '2007-11-02');
insert into produtos values ('s03','Cadeira mod. JZZ', 20, '2007-11-02');
insert into produtos values ('a03','Cadeira mod. XXX', 25, '2007-11-03');
```



Podemos ver tódolos datos para comprobar que son correctos:



```sql
select * from produtos;
```



e deberíamos obter



```txt
+--------+----------------+--------+------------+
| codigo | nome           | prezo  | dataalta   |
+--------+----------------+--------+------------+
| a01    | Afiador        |   2.50 | 2007-11-02 |
| s01    | Cadeira mod. ZAZ |  20.00 | 2007-11-03 |
| s02    | Cadeira mod. XAX |  25.00 | 2007-11-03 |
+--------+----------------+--------+------------+
```



Para ver qué produtos se chaman "Afiador":



```sql
select * from produtos where nome='Afiador';
```





```txt
+--------+----------+--------+------------+
| codigo | nome   | prezo | dataalta  |
+--------+----------+--------+------------+
| a01    | Afiador |   2.50 | 2007-11-02 |
+--------+----------+--------+------------+
```



Si queremos saber cales comezan por C:



```sql
select * from produtos where nome like 'C%';
```





```txt
+--------+------------------+--------+------------+
| codigo | nome             | prezo  |  dataalta  |
+--------+------------------+--------+------------+
| s01    | Cadeira mod. ZAZ |  20.00 | 2007-11-03 |
| s02    | Cadeira mod. XAX |  25.00 | 2007-11-03 |
+--------+------------------+--------+------------+
```



Si queremos ver cales teñen un prezo superior a 22, e a demais non desexamos ver todos os campos, senón só o nome e o prezo:



```sql
select nome, prezo from produtos where prezo > 22;
```





```txt
+------------------+--------+
| nome             | prezo  |
+------------------+--------+
| Cadeira mod. XAX |  25.00 |
+------------------+--------+
```



Prezo medio das cadeiras:



```sql
select avg(prezo) from produtos where left(nome,5) = 'Cadeira';
```





```txt
+-------------+
| avg(prezo) |
+-------------+
|   22.500000 |
+-------------+
```



Isto de mirar as primeiras letras para saber si é unha cadeira o non... quizá non sexa a mellor opción. Parece máis razoable engadir un novo dato: a "categoría". Imos a modificar a estrutura da táboa para facelo:



```sql
alter table produtos add categoria varchar(10);
```



Comprobamos con `select` que todo os foron ingresados correctamente:



```sql
select * from produtos;
```





```txt
+--------+------------------+--------+------------+-----------+
| codigo | nome             | prezo  | dataalta   | categoria |
+--------+------------------+--------+------------+-----------+
| a01    | Afiador          |   2.50 | 2007-11-02 | NULL      |
| s01    | Cadeira mod. ZAZ |  20.00 | 2007-11-03 | NULL      |
| s02    | Cadeira mod. XAX |  25.00 | 2007-11-03 | NULL      |
+--------+------------------+--------+------------+-----------+
```



Agora mesmo, tódalas categorías teñen o valor NULL, e iso non é moi útil. Imos a dar o valor "utensilio" á categoría de tódolos produtos existentes



```sql
update produtos set categoria='utensilio';
```



 E xa que estamos, modificaremos os produtos que comezan pola palabra "Cadeira", para que a súa categoría sexa "cadeira"



```sql
update produtos set categoria='cadeira' where left(nome,5) = 'Cadeira';
```





```txt
+--------+------------------+--------+------------+-----------+
| codigo | nome             | prezo  | dataalta   | categoria |
+--------+------------------+--------+------------+-----------+
| a01    | Afiador          |   2.50 | 2007-11-02 | utensilio |
| s01    | Cadeira mod. ZAZ |  20.00 | 2007-11-03 | cadeira   |
| s02    | Cadeira mod. XAX |  25.00 | 2007-11-03 | cadeira   |
+--------+------------------+--------+------------+-----------+
```



Para vela lista de categorías (sen que aparezan datos duplicados), deberemos usar a palabra `distinct` 



```sql
select distinct categoria from produtos;
```





```sql
+-----------+
| categoria |
+-----------+
| utensilio |
| cadeira   |
+-----------+
```



Finalmente, para ver a cantidade de produtos que temos en cada categoría, deberemos usar `count` e agrupalos datos cun `group by`:



```sql
select categoria, count(*) from produtos group by categoria;
```





```sql
+-----------+----------+
| categoria | count(*) |
+-----------+----------+
| cadeira   |        2 |
| utensilio |        1 |
+-----------+----------+
```