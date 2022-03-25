---
marp: true
---

# Diagramas E/R

Un [diagrama de relación entre entidades](https://en.wikipedia.org/wiki/Entity–relationship_model) (ERD), tamén coñecido como ERD ou modelo de emerxencia, é unha representación visual de **diferentes entidades dentro dun sistema e como se relacionan ditas entidades entre si**. 

*Por exemplo, os elementos escritor, novela e consumidor pódense describir usando diagramas ER do seguinte xeito:*

---

![bg 90% left Exemplo de diagrama ER](./assets/ER-Diagram-Example.jpeg)<br>*Diagrama ER con obxectos básicos*

---

 


### Historia dos diagramas ER

Aínda que o modelado de datos converteuse nunha necesidade ao redor da década de 1970, non había un xeito estándar de modelar bases de datos ou procesos de negocio. Aínda que se propuxeron e discutiron moitas solucións, ningunha foi amplamente adoptada.

Se lle atribue a [Peter Chen](https://en.wikipedia.org/wiki/Peter_Chen) a introdución do modelo ER amplamente adoptado no seu artigo " [The Entity Relationship Model - Towards a Unified View of Data](http://www.csc.lsu.edu/~chen/pdf/erd-5-pages.pdf) ".

---

O seu modelo inspirouse nos diagramas de estrutura de datos introducidos por Charles Bachman. Unha das primeiras formas de diagramas ER, os diagramas de Bachman reciben o seu nome.

Para obter un historial detallado dos diagramas ER e da avaliación do modelado de datos, consulte [este artigo](http://www.dataversity.net/a-short-history-of-the-er-diagram-and-information-modeling/).

---

### Usando diagramas ER

Cales son os usos dos diagramas ER? Onde se usan? Aínda que poden usarse para modelar case calquera sistema, utilízanse principalmente nas seguintes áreas:

---

#### Modelos ER para o deseño de bases de datos

Son moi utilizados para deseñar bases de datos relacionais. As entidades do esquema ER convértense en táboas, atributos e convértense no esquema de base de datos. Dado que poden usarse para visualizar táboas de bases de datos e as súas relacións, adoitan usarse tamén para solucionar problemas de bases de datos.

---

#### Diagramas ER en enxeñaría de software

Os diagramas de relación de entidades utilízanse na enxeñaría de software durante as etapas de planificación do proxecto de software. Axudan a identificar os distintos elementos do sistema e as súas relacións entre si. Adoita utilizarse como base para diagramas de fluxo de datos ou DFD, como se coñecen comunmente.

Por exemplo, un software de inventario usado nunha tenda de venda polo miúdo terá unha base de datos que supervisa elementos como compras, artigo, tipo de elemento, orixe do artigo e prezo do artigo. Presentar esta información a través dun diagrama ER sería algo así:

---

![bg 90% left Exemplo de diagrama ER cunha entidade con atributos](./assets/ER-Diagram-Example-2.jpeg)<br>*Exemplo de diagrama ER cunha entidade con atributos.<br> A información dentro das formas ovales son atributos dunha entidade particular.*

---

![bg 90% left Os símbolos do diagrama ER discutidos neste tutorial do diagrama ER](./assets/ER-Diagram-Elements.jpeg)<br>
*Elementos dos diagramas ER*

---

### Símbolos e notas do diagrama de urxencias

Hai tres elementos básicos nun diagrama ER: Entidade, Atributo, Relación. Hai máis elementos que se basean nos elementos principais. Son entidade débil, atributo multivalor, atributo derivado, relación débil e relación recursiva. A cardinalidade e a ordinalidade son outras dúas notacións usadas nos diagramas ER para definir mellor as relacións.

---

#### Entidade

Unha entidade pode ser unha persoa, un lugar, un evento ou un obxecto que é relevante para un sistema determinado. Por exemplo, un sistema escolar pode incluír estudantes, profesores, cursos principais, materias, taxas e outros elementos. As entidades represéntanse nos diagramas ER mediante un rectángulo e son nomeadas usando substantivos singulares.

---

#### entidade débil

Unha entidade débil é unha entidade que depende da existencia doutra entidade. En termos máis técnicos, pódese definir como unha entidade que non pode ser identificada polos seus propios atributos. Usa unha chave estranxeira combinada co seu atributo para formar a chave primaria. Unha entidade como o artigo do pedido é un bo exemplo diso. O artigo da orde carecerá de significado sen unha garantía, polo que depende da existencia da orde.

---

![bg 90% left Entidade débil nos diagramas de relacións de entidades](./assets/weak-entity-ER-diagrams.jpeg)<br>*Exemplo de entidade débil en diagramas ER*

---

#### Atributo

Un atributo é unha propiedade, trazo ou característica dunha entidade, unha relación ou calquera outro atributo. Por exemplo, o atributo *Nome do artigo* de inventario* é un atributo da entidade *Elemento de inventario*. Unha entidade pode ter tantos atributos como sexa necesario.


---

![bg 90% left Atributos nos diagramas ER](./assets/Attributes-ER-Diagrams.jpeg)<br>*Atributos en diagramas ER. Un atributo pode ter os seus propios atributos (atributo composto).*


Atributos dos atributos.
P.ex.: o atributo *Enderezo do cliente* pode ter os atributos *número*, *rúa*, *cidade* e *estado*. Chámanse *atributos compostos*. Algúns diagramas ER de nivel superior non amosan atributos por mor da simplicidade. Os atributos están representados por formas ovales.

---

![bg 90% left Atributo multivalor nos diagramas de relación de entidades](./assets/Multivalued-Attribute-ER-Diagrams.jpeg)<br>*Exemplo dun atributo multivalor*

#### atributo multivalor

Se un atributo pode ter máis dun valor, chámase atributo multivalor. É importante ter en conta que isto é diferente dun atributo que ten os seus propios atributos. Por exemplo, unha entidade docente pode ter varios valores de materia.

---

![bg 90% left Atributo derivado nos diagramas ER](./assets/Derived-Attribute-ER-Diagrams.jpeg)<br>*Atributo derivado nos diagramas ER*

#### atributo derivado

Un atributo baseado noutro atributo. Isto raramente se atopa nos diagramas ER. Por exemplo, para un círculo, a área pódese derivar a partir do raio.

---


![bg 90% left Relacións nos diagramas ER](./assets/Relationship-ER-diagrams.jpeg)<br>*Utilización de relacións en diagramas de relacións de entidades*

**Relación**

Unha relación describe como interactúan as entidades. Por exemplo, a entidade "Carpinteiro" pode estar relacionada coa entidade "táboa" pola relación "constrúe" ou "fai". As relacións represéntanse con formas de diamante e están etiquetadas con verbos.

---
![bg 90% left Relación recursiva en diagramas ER](./assets/Recursive-Relationship-ER-Diagrams.jpeg)<br>
*Exemplo de relación recursiva*

#### relación recursiva

Se a mesma entidade participa máis dunha vez nunha relación coñécese como relación recursiva. No seguinte exemplo, un empregado pode ser supervisor e ser supervisado, polo que hai unha relación recursiva.

---


![bg 90% left Cardinalidade nos diagramas ER](./assets/Cardinality-ER-Diagrams.jpeg)<br>*Cardinalidade en diagramas ER usando notación UML*

#### Cardinalidade e ordinalidade

Definen aínda máis as relacións entre entidades colocando a relación no contexto dos números. Nun sistema de correo-e, p.ex., unha conta pode ter varios contactos. A relación, neste caso, segue o modelo "un a moitos". Hai  notacións específicas para presentar a cardinalidade nos diagramas ER. Chen, UML, Crow's Foot, Bachman son algunhas das máis populares.


---

### Debuxar diagramas ER

Puntos a ter ne conta ao crear un diagrama ER.

1. **Identifica todas as entidades** do sistema. Unha entidade debe aparecer só unha vez nun diagrama dado. Crea rectángulos para todas as entidades e nomeaos correctamente.
2. **Identificar as relacións** entre as entidades. Conéctaos usando unha liña e engade un diamante no medio que describe a relación.
3. **Engadir** atributos para entidades. Dá nomes de atributos significativos para que se poidan entender facilmente.

Parece sinxelo, non? Nun sistema complexo, pode ser un pesadelo identificar relacións. Isto é algo que só perfeccionarás coa práctica.

---

#### Boas prácticas do diagrama ER

1. Proporcione un nome preciso e axeitado para cada entidade, atributo e relación do diagrama. Os termos que son sinxelos e familiares sempre superan as palabras vagas e técnicas. Ao nomear entidades, lembre de usar substantivos singulares. Non obstante, pódense usar adxectivos para distinguir entidades que pertencen á mesma clase (empregado a tempo parcial e empregado a tempo completo, por exemplo). Mentres tanto, os nomes dos atributos deben ser significativos, únicos, independentes do sistema e facilmente comprensibles.

---

2. Elimina relacións vagas, redundantes ou innecesarias entre entidades.
3. Nunca conectes unha relación con outra relación.
4. Fai un uso eficaz das cores. Podes usar cores para clasificar características similares ou para resaltar áreas clave dos teus diagramas.

#### Debuxa diagramas ER

Podes debuxar diagramas de relacións de entidades manualmente, especialmente cando estás a mostrar de xeito informal sistemas sinxelos aos teus compañeiros. Non obstante, para sistemas máis complexos e para públicos externos, mellor empregar un software de diagramación.

---

ref:
- https://creately.com/blog/es/negocios/tutorial-del-diagrama-de-er/
- https://michael-fuchs-sql.netlify.app/2021/03/03/entity-relationship-diagram-erd/
- https://michael-fuchs-python.netlify.app/2021/03/24/sql/