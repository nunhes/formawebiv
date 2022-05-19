

# Schematron

A partir de mayo de 2006 el lenguaje Schematron forma parte del estándar ISO - DSDL (Document Schema Definition Languages). La función de este lenguaje es la validación de estructura y contenidos en documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/). El lenguaje de esquema Schematron permite la comprobación de reglas de negocio que no pueden ser verificadas con otros lenguajes.

Schematron se presenta como una extensión de lenguajes de validación tales como DTD, XML Schema o RELAX-NG y puede ser empleado junto con analizadores.







# Schematron en pocas palabras

(Fragmento del libro publicado en alemán "Schematron - Reglas de negocio eficientes para documentos [XML](https://www.data2type.de/es/xml-xslt-xslfo/xml/)", capítulo 5)

[XPath](https://www.data2type.de/es/xml-xslt-xslfo/xpath/) ofrece numerosas posibilidades para analizar documentos XML y realizar comprobaciones de mano de los más diversos criterios. Con objeto de centrar la atención sobre posibles errores e imprecisiones y posibilitar la creación de avisos de error pertinentes incorporaremos las construcciones de XPath en el lenguaje de esquema Schematron. Este capítulo ofrece una introducción a Schematron y explica de forma detallada el funcionamiento de cada una de las construcciones.


Una vez finalizado el capítulo podrá analizar documentos XML según el estándar ISO de Schematron, comprender su funcionamiento e incluso definir esquemas aplicables en la práctica.
Tras una breve descripción de los orígenes de Schematron, pasaremos a explicar el funcionamiento de las construcciones más importantes de Schematron usando el ejemplo del capítulo 1.

```markup
<?xml version="1.0" encoding="UTF-8"?>
<arca xmlns="http://www.schematron.info/arche" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.schematron.info/arche arche.xsd">
  <carga>
    <compartimento>
      <animal genero="hembra" carnivoro="no">
        <especie>cebra</especie>
        <peso>200</peso>
        <edad>12</edad>
      </animal>
      <animal genero="macho" carnivoro="no">
        <especie>cebra</especie>
        <peso>250</peso>
        <edad>13</edad>
      </animal>
    </compartimento>
    <compartimento>
      <animal genero="hembra" carnivoro="sí">
        <especie>león</especie>
        <peso>200</peso>
        <edad>23</edad>
      </animal>
      <animal genero="macho" carnivoro="sí">
        <especie>león</especie>
        <peso>180</peso>
        <edad>30</edad>es.-
      </animal>
    </compartimento>
    <compartimento>
      <animal genero="hembra" carnivoro="no">
        <especie>elefante</especie>
        <peso>10000</peso>
        <edad>20</edad>
      </animal>
      <animal genero="macho" carnivoro="no">
        <especie>elefante</especie>
        <peso>15000</peso>
        <edad>40</edad>
      </animal>
    </compartimento>
  </carga>
  <edad-reproductiva-maxima>
    <especie-animal>
      <name>elefante</name>
      <macho>80</macho>
      <hembra>30</hembra>
    </especie-animal>
    <especie-animal>
      <name>león</name>
      <macho>30</macho>
      <hembra>15</hembra>
    </especie-animal>
    <especie-animal>
      <name>cebra</name>
      <macho>30</macho>
      <hembra>20</hembra>
    </especie-animal>
  </edad-reproductiva-maxima>
  <carga-util>44000</carga-util>
</arca>
```

Las bases para una "buena" convivencia en el arca se establecen en el siguiente XML Schema:

### Representación gráfica del Schema para la instancia del arca:



[![Grafische Darstellung des Arche-Schemas](https://www.data2type.de/fileadmin/images/Schema-arca.PNG)](https://www.data2type.de/fileadmin/images/Schematron-Schema.jpeg)



### El documento XML Schema:

```markup
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.schematron.info/arche" xmlns="http://www.schematron.info/arche" elementFormDefault="qualified">
  <xs:element name="edad" type="xs:positiveInteger"/>
  <xs:element name="arca">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="carga"/>
        <xs:element ref="edad-reproductiva-maxima"/>
        <xs:element ref="carga-util"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="especie" type="xs:string"/>
  <xs:element name="peso" type="xs:positiveInteger"/>
  <xs:element name="carga">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="compartimento" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="edad-reproductiva-maxima">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="especie-animal" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="macho" type="xs:positiveInteger"/>
  <xs:element name="nombre" type="xs:string"/>
  <xs:element name="carga-util" type="xs:positiveInteger"/>
  <xs:element name="animal">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="especie"/>
        <xs:element ref="peso"/>
        <xs:element ref="edad"/>
      </xs:sequence>
      <xs:attribute name="genero" use="required">
        <xs:simpleType>
          <xs:restriction base="xs:string">
            <xs:enumeration value="macho"/>
            <xs:enumeration value="hembra"/>
          </xs:restriction>
        </xs:simpleType>
      </xs:attribute>
      <xs:attribute name="carnivoro" use="required">
        <xs:simpleType>
          <xs:restriction base="xs:string">
            <xs:enumeration value="ja"/>
            <xs:enumeration value="nein"/>
          </xs:restriction>
        </xs:simpleType>
      </xs:attribute>
    </xs:complexType>
  </xs:element>
  <xs:element name="especie-animal">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="nombre"/>
        <xs:element ref="macho"/>
        <xs:element ref="hembra"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="compartimento">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="animal" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="hembra" type="xs:positiveInteger"/>
</xs:schema>
```

|      | [siguiente >>](https://www.data2type.de/es/xml-xslt-xslfo/tecnologias-xml-schematron-introduccion-a-schematron-y-referencia/introduccion-schematron/historia-y-flujo-de-trabajo#c4311) |
| ---- | ------------------------------------------------------------ |
|      |                                                              |