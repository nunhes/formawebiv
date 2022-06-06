# EXERCICIOS

## Consultas con MySQL

Imos resolver algunhas consultas SQL usando o SGBD: **MySQL**. Son consultas básicas, sen unións nin outra cousa máis que proxeccións ou `select`s, e unha ollada as expresións regulares usando **LIKE**, agrupando con **GROUP BY** e utilizando algunhas funcións de agregación como **SUM**, **AVG**, **MIN**, etcétera.

:eye: *estas non son solucións definitivas, só propostas que - poden conter algún erro- non quitan que poida haber mellores formas de resolver ditas consultas.*



## Táboa SQL

Para traballar con estes exemplos utilizaremos a seguinte táboa. Si queres, podes copiar todo o script na CLI de MySQL para que a base de datos se cree automáticamente.

```sql
/*
Crea unha base de datos, só copia as seguintes dúas líñas non comentadas
*/
CREATE DATABASE IF NOT EXISTS probas;
USE probas;


/*
   Agora que xa tes unha base de datos, só copia o seguinte
*/
CREATE TABLE tblUsuarios (
   idx INT PRIMARY KEY AUTO_INCREMENT,
   usuario VARCHAR(20),
   nome VARCHAR(20),
   sexo VARCHAR(1),
   nivel TINYINT,
   email VARCHAR(50),
   telefono VARCHAR(20),
   marca VARCHAR(20),
   empresa VARCHAR(20),
   saldo FLOAT,
   activo BOOLEAN
);


INSERT INTO tblUsuarios 
VALUES 
('1','BRE2271','BRENDA','M','2','brenda@live.com','655-330-5736','SAMSUNG','IUSACELL','100','1'),
('2','OSC4677','OSCAR','H','3','oscar@gmail.com','655-143-4181','LG','TELCEL','0','1'),
('3','JOS7086','JOSE','H','3','francisco@gmail.com','655-143-3922','NOKIA','MOVISTAR','150','1'),
('4','LUI6115','LUIS','H','0','enrique@outlook.com','655-137-1279','SAMSUNG','TELCEL','50','1'),
('5','LUI7072','LUIS','H','1','luis@hotmail.com','655-100-8260','NOKIA','IUSACELL','50','0'),
('6','DAN2832','DANIEL','H','0','daniel@outlook.com','655-145-2586','SONY','UNEFON','100','1'),
('7','JAQ5351','JAQUELINE','M','0','jaqueline@outlook.com','655-330-5514','BLACKBERRY','AXEL','0','1'),
('8','ROM6520','ROMAN','H','2','roman@gmail.com','655-330-3263','LG','IUSACELL','50','1'),
('9','BLA9739','BLAS','H','0','blas@hotmail.com','655-330-3871','LG','UNEFON','100','1'),
('10','JES4752','JESSICA','M','1','jessica@hotmail.com','655-143-6861','SAMSUNG','TELCEL','500','1'),
('11','DIA6570','DIANA','M','1','diana@live.com','655-143-3952','SONY','UNEFON','100','0'),
('12','RIC8283','RICARDO','H','2','ricardo@hotmail.com','655-145-6049','MOTOROLA','IUSACELL','150','1'),
('13','VAL6882','VALENTINA','M','0','valentina@live.com','655-137-4253','BLACKBERRY','AT&T','50','0'),
('14','BRE8106','BRENDA','M','3','brenda2@gmail.com','655-100-1351','MOTOROLA','NEXTEL','150','1'),
('15','LUC4982','LUCIA','M','3','lucia@gmail.com','655-145-4992','BLACKBERRY','IUSACELL','0','1'),
('16','JUA2337','JUAN','H','0','juan@outlook.com','655-100-6517','SAMSUNG','AXEL','0','0'),
('17','ELP2984','ELPIDIO','H','1','elpidio@outlook.com','655-145-9938','MOTOROLA','MOVISTAR','500','1'),
('18','JES9640','JESSICA','M','3','jessica2@live.com','655-330-5143','SONY','IUSACELL','200','1'),
('19','LET4015','LETICIA','M','2','leticia@yahoo.com','655-143-4019','BLACKBERRY','UNEFON','100','1'),
('20','LUI1076','LUIS','H','3','luis2@live.com','655-100-5085','SONY','UNEFON','150','1'),
('21','HUG5441','HUGO','H','2','hugo@live.com','655-137-3935','MOTOROLA','AT&T','500','1');
```

## Consultas propostas

### Bloque 1

##### Consultas

1. Listar os nomes dos usuarios
2. Calcular o saldo máximo dos usuarios de sexo “Mujer”
3. Listar nome e teléfono dos usuarios con teléfono NOKIA, BLACKBERRY ou SONY
4. Contar os usuarios sin saldo o inactivos
5. Listar o login dos usuarios con nivel 1, 2 ou 3
6. Listar os números de teléfono con saldo menor ou igual a 300
7. Calcular a suma dos saldos dos usuarios da empresa telefónica NEXTEL
8. Contar ou número de usuarios por compañía telefónica
9. Contar ou número de usuarios por nivel
10. Listar ou login dos usuarios con nivel 2
11. Mostrar ou email dos usuarios que usan gmail
12. Listar nome e teléfono dos usuarios con teléfono LG, SAMSUNG ou MOTOROLA

#### Solucións

```sql
# Listar os nomes dos usuarios
SELECT nome FROM tblUsuarios;


# Calcular o saldo máximo dos usuarios de sexo "Muller"
SELECT MAX(saldo) FROM tblUsuarios WHERE sexo = 'M';


#Listar nome e teléfono dos usuarios con teléfono NOKIA, BLACKBERRY ou SONY
SELECT nome, telefono FROM tblUsuarios WHERE marca IN('NOKIA', 'BLACKBERRY', 'SONY');


#Contar os usuarios sin saldo ou inactivos
SELECT COUNT(*) FROM tblUsuarios WHERE NOT activo OR saldo <= 0;


#Listar o login dos usuarios con nivel 1, 2 ou 3
SELECT usuario FROM tblUsuarios WHERE nivel IN(1, 2, 3);


#Listar os números de teléfono con saldo menor ou igual a 300
SELECT telefono FROM tblUsuarios WHERE saldo <= 300;


#Calcular a suma dos saldos dos usuarios da empresa telefónica NEXTEL
SELECT SUM(saldo) FROM tblUsuarios WHERE empresa = 'NEXTEL';


#Contar ou número de usuarios por compañía telefónica
SELECT empresa, COUNT(*) FROM tblUsuarios GROUP BY empresa;


#Conta o número de usuarios por nivel
SELECT nivel, COUNT(*) FROM tblUsuarios GROUP BY nivel;


#Listar o login dos usuarios con nivel 2
SELECT usuario FROM tblUsuarios WHERE nivel = 2;


#Mostrar o email dos usuarios que usan gmail
SELECT email FROM tblUsuarios WHERE email LIKE '%gmail.com';


#Listar nome e teléfono dos usuarios con teléfono LG, SAMSUNG ou MOTOROLA
SELECT nome, telefono FROM tblUsuarios WHERE marca IN('LG', 'SAMSUNG', 'MOTOROLA');
```

### Bloque 2

#### Consultas

1. Listar nome e teléfono dos usuarios con teléfono que non sexa da marca LG o SAMSUNG
2. Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL
3. Listar o login e teléfono dos usuarios con empresa telefónica que non sexa TELCEL
4. Calcular o saldo promedio dos usuarios que teñen teléfono marca NOKIA
5. Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL o AXEL
6. Mostrar o email dos usuarios que non usan yahoo
7. Listar o login e teléfono dos usuarios con empresa telefónica que non sexa TELCEL o IUSACELL
8. Listar o login e teléfono dos usuarios con empresa telefónica UNEFON
9. Listar las diferentes marcas de celular en orden alfabético descendentemente
10. Listar las diferentes empresas en orden alfabético aleatorio
11. Listar o login dos usuarios con nivel 0 o 2
12. Calcular o saldo promedio dos usuarios que teñen teléfono marca LG

#### Solucións

```sql
# Listar nome e teléfono dos usuarios con teléfono que non sexa da marca LG o SAMSUNG
SELECT nome, telefono FROM tblUsuarios WHERE marca NOT IN('LG', 'SAMSUNG');


# Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL
SELECT usuario, telefono FROM tblUsuarios WHERE empresa = 'IUSACELL';


# Listar o login e teléfono dos usuarios con empresa telefónica que non sexa TELCEL
SELECT usuario, telefono FROM tblUsuarios WHERE empresa <> "TELCEL";


# Calcular o saldo promedio dos usuarios que teñen teléfono marca NOKIA
SELECT AVG(saldo) FROM tblUsuarios WHERE marca = 'NOKIA';


# Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL o AXEL
SELECT usuario, telefono FROM tblUsuarios WHERE empresa IN('IUSACELL', 'AXEL');


# Mostrar o email dos usuarios que non usan yahoo
SELECT email FROM tblUsuarios WHERE email NOT LIKE '%yahoo.com';


# Listar o login e teléfono dos usuarios con empresa telefónica que non sexa TELCEL o IUSACELL
SELECT usuario, telefono FROM tblUsuarios WHERE empresa NOT IN('TELCEL', 'IUSACELL');


# Listar o login e teléfono dos usuarios con empresa telefónica UNEFON
SELECT usuario, telefono FROM tblUsuarios WHERE empresa = 'UNEFON';


# Listar as diferentes marcas de celular en orden alfabético descendente
SELECT DISTINCT marca FROM tblUsuarios ORDER BY marca DESC;


# Listar as diferentes empresas en orden alfabético aleatorio
SELECT DISTINCT empresa FROM tblUsuarios ORDER BY RAND();


# Listar o login dos usuarios con nivel 0 ou 2
SELECT usuario FROM tblUsuarios WHERE nivel IN(0, 2);


# Calcular o saldo promedio dos usuarios que teñen teléfono marca LG
SELECT AVG(saldo) FROM tblUsuarios WHERE marca = 'LG';
```

### Bloque 3

#### Consultas

1. Listar o login dos usuarios con nivel 1 o 3
2. Listar nome e teléfono dos usuarios con teléfono que non sexa da marca BLACKBERRY
3. Listar o login dos usuarios con nivel 3
4. Listar o login dos usuarios con nivel 0
5. Listar o login dos usuarios con nivel 1
6. Contar o número de usuarios por sexo
7. Listar o login e teléfono dos usuarios con empresa telefónica AT&T
8. Listar las diferentes empresas en orden alfabético descendentemente
9. Listar o logn dos usuarios inactivos
10. Listar os números de teléfono sin saldo
11. Calcular o saldo mínimo dos usuarios de sexo “Home ”
12. Listar os números de teléfono con saldo maior a 300

#### Solucións

```sql
# Listar o login dos usuarios con nivel 1 o 3
SELECT usuario FROM tblUsuarios WHERE nivel IN(1, 3);


# Listar nome e teléfono dos usuarios con teléfono que non sexa da marca BLACKBERRY 
SELECT nome, telefono FROM tblUsuarios WHERE marca <> "BLACKBERRY";


# Listar o login dos usuarios con nivel 3
SELECT usuario FROM tblUsuarios WHERE nivel = 3;


# Listar o login dos usuarios con nivel 0
SELECT usuario FROM tblUsuarios WHERE nivel = 0;


# Listar o login dos usuarios con nivel 1
SELECT usuario FROM tblUsuarios WHERE nivel = 1;


# Contar o número de usuarios por sexo
SELECT sexo, COUNT(*) FROM tblUsuarios GROUP BY sexo;


# Listar o login e teléfono dos usuarios con empresa telefónica AT&T
SELECT usuario, telefono FROM tblUsuarios WHERE empresa = "AT&T";


# Listar las diferentes empresas en orden alfabético descendentemente
SELECT DISTINCT empresa FROM tblUsuarios ORDER BY empresa DESC;


# Listar o login dos usuarios inactivos
SELECT usuario FROM tblUsuarios WHERE NOT activo;


# Listar os números de teléfono sen saldo
SELECT telefono FROM tblUsuarios WHERE saldo <= 0;


# Calcular o saldo mínimo dos usuarios de sexo "Home "
SELECT MIN(saldo) FROM tblUsuarios WHERE sexo = 'H';


# Listar os números de teléfono con saldo maior a 300
SELECT telefono FROM tblUsuarios WHERE saldo > 300;
```

### Bloque 4

#### Consultas

1. Contar o número de usuarios por marca de teléfono
2. Listar nome e teléfono dos usuarios con teléfono que non sexa da marca LG
3. Listar las diferentes empresas en orden alfabético ascendentemente
4. Calcular a suma dos saldos dos usuarios da empresa telefónica UNEFON
5. Mostrar o email dos usuarios que usan hotmail
6. Listar os nomes dos usuarios sin saldo o inactivos
7. Listar o login e teléfono dos usuarios con empresa telefónicaIUSACELL o TELCEL
8. Listar las diferentes marcas de celular en orden alfabético ascendentemente
9. Listar las diferentes marcas de celular en orden alfabético aleatorio
10. Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL o UNEFON
11. Listar nome e teléfono dos usuarios con teléfono que non sexa da marca MOTOROLA o NOKIA
12. Calcular a suma dos saldos dos usuarios da empresa telefónica TELCEL

#### Solucións

```sql
# Contar o número de usuarios por marca de teléfono
SELECT marca, COUNT(*) FROM tblUsuarios GROUP BY marca;


# Listar nome e teléfono dos usuarios con teléfono que non sexa da marca LG
SELECT nome, telefono FROM tblUsuarios WHERE marca <> "LG";


# Listar as diferentes empresas en orden alfabético ascendentemente
SELECT DISTINCT empresa FROM tblUsuarios ORDER BY empresa ASC;


# Calcular a suma dos saldos dos usuarios da empresa telefónica UNEFON
SELECT SUM(saldo) FROM tblUsuarios WHERE empresa = 'UNEFON';


# Mostrar o email dos usuarios que usan hotmail
SELECT email FROM tblUsuarios WHERE email LIKE "%hotmail.com";


# Listar os nomes dos usuarios sin saldo ou inactivos
SELECT nome FROM tblUsuarios WHERE NOT activo OR saldo <= 0;


# Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL o TELCEL
SELECT usuario, telefono FROM tblUsuarios WHERE empresa IN('IUSACELL', 'TELCEL');


# Listar las diferentes marcas de celular en orden alfabético ascendentemente
SELECT DISTINCT marca FROM tblUsuarios ORDER BY marca DESC;


# Listar las diferentes marcas de celular en orden alfabético aleatorio
SELECT DISTINCT marca FROM tblUsuarios ORDER BY RAND();


# Listar o login e teléfono dos usuarios con empresa telefónica IUSACELL o UNEFON
SELECT usuario, telefono FROM tblUsuarios WHERE empresa IN('IUSACELL', 'UNEFON');


# Listar nome e teléfono dos usuarios con teléfono que non sexa da marca MOTOROLA o NOKIA
SELECT nome, telefono FROM tblUsuarios WHERE marca NOT IN('MOTOROLA', 'NOKIA');


# Calcular a suma dos saldos dos usuarios da empresa telefónica TELCEL
SELECT SUM(saldo) FROM tblUsuarios WHERE empresa = 'TELCEL';
```

## Conclusión

Estes exercicios, aínda que repetitivos, axudan aprender os comandos e sintaxe.



---

_ref.:_

- *https://parzibyte.me/blog/2018/02/06/ejercicios-resueltos-consultas-sql-mysql/_*

- *http://sqlfiddle.com/#!9/1f5b3/2*

- *https://josejuansanchez.org/bd/ejercicios-consultas-sql/index.html*

- *https://www.nachocabanes.com/sql/curso/sqle1.php*
- *https://www.w3schools.com/mysql/mysql_intro.asp*

