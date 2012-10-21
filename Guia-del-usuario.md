La librería presenta una interfaz muy simple centrada en el Comprobante Fiscal Digital (CFD), las clases principales son `CFDv32` y `CFDv22` que tienen la lógica correspondiente a las versiones 3.2 y 2.2 del CFD respectivamente.

### Breve introducción

A continuación se presentan a manera de introducción algunos ejemplos de como utilizar la librería. Más adelante se explican a detalle los pasos necesarios para descargar e instalar la librería.

### Creación de un CFDv32

Se puede crear un `CFDv32` de tres formas:

A partir de un `InputStream`, que puede ser un archivo previamente  generado o el contenido de un request HTTP, etc.:
```java
    CFDv32 cfd = new CFDv32(new FileInputStream(file));
```
A partir de un `Comprobante` nuevo: 
```java
    ObjectFactory of = new ObjectFactory();
    Comprobante comp = of.createComprobante();
    comp.setVersion("3.2");
    comp.setFecha(new Date());
    ...
    CFDv32 cfd = new CFDv32(comp);
```
Cargar un `Comprobante` a partir de un archivo y posteriormente utilizarlo para crear un `CFDv3`: 
```
    Comprobante comp = CFDv322.newComprobante(new FileInputStream(file));
    ...
    CFDv32 cfd = new CFDv32(comp);
```

### Creación de un CFDv22

De igual forma se puede crear un `CFDv22`:

A partir de un `InputStream`, que puede ser un archivo previamente  generado o el contenido de un request HTTP, etc.:
```java
    CFDv22 cfd = new CFDv22(new FileInputStream(file));
```
A partir de un `Comprobante`, que es el modelo que representa al XSD en la aplicación: 
```java
    ObjectFactory of = new ObjectFactory();
    Comprobante comp = of.createComprobante();
    comp.setVersion("2.2");
    comp.setFecha(new Date());
    ...
    CFDv22 cfd = new CFDv22(comp);
```
Cargar un `Comprobante` a partir de un archivo y posteriormente utilizarlo para crear un `CFDv22`: 
```java
    Comprobante comp = CFDv22.newComprobante(new FileInputStream(file));
    ...
    CFDv22 cfd = new CFDv22(comp);
```

### Principales operaciones

Las clases CFDv3 y el CFDv2, tienen cuatro métodos principales `sellar()`, `validar()`,  `verificar()` y `guardar()`.

El flujo típico para _firmar_ un CFDI versión 3.0 se ve así:
```java
    CFDv32 cfd = new CFDv32(new FileInputStream(file)); // Crea el CFD a partir de un archivo
    Key key = KeyLoader.loadPKCS8PrivateKey(new FileInputStream(keyfile),  password); // Carga la llave privada
    Certificate cert = KeyLoader.loadX509Certificate(new FileInputStream(certFile)); // Carga el certificado
    Comprobante sellado = cfd.sellarComprobante(key, cert); // Sellar CFD y obtener un Comprobante sellado
    cfd.guardar(new FileOutputStream(outFile)); // Serializa el CFD ya firmado
    String cadena = cfd.getCadenaOriginal(); // Obtener cadena original
    String sello = sellado.getSello(); // Obtener sello
```

El flujo típico para _verificar_ un CFDI versión 3.0, se ve así:

```java
    CFDv32 cfd = new CFDv32(new FileInputStream(file)); // Crea el CFD a partir de un archivo
    cfd.validar(); // Valida el XML, que todos los elementos estén presentes
    cfd.verificar(); // Verifica un CFD ya firmado
```

Además de estas operaciones el CFDv2 permite verificar el CFD utilizando un certificado externo:

```java
    CFDv22 cfd = new CFDv22(new FileInputStream(file)); // Crea el CFD a partir de un archivo
    Certificate cert = KeyLoader.loadX509Certificate(new FileInputStream(certFile)); // Carga el certificado
    cfd.validar(); // Valida el XML, que todos los elementos estén presentes
    cfd.verificar(cert); // Verifica un CFD ya firmado
```

_Nota:  Puedes encontrar un ejemplo del uso de las librerías en las clases:_ [mx.bigdata.sat.cfdi.examples.Main](https://github.com/bigdata-mx/factura-electronica/blob/master/src/main/java/mx/bigdata/sat/cfdi/examples/Main.java) y [mx.bigdata.sat.cfd.examples.Main](https://github.com/bigdata-mx/factura-electronica/blob/master/src/main/java/mx/bigdata/sat/cfd/examples/Main.java).
 
### Creación de un `Comprobante` utilizando las librerías

Para crear un `Comprobante` de forma procedural es necesario utilizar los métodos de la clase [mx.bigdata.sat.cfdi.schema.ObjectFactory](http://factura-electronica.googlecode.com/svn/javadoc/mx/bigdata/sat/cfdi/schema/ObjectFactory.html) para la versión 3.0 y [mx.bigdata.sat.cfd.schema.ObjectFactory](http://factura-electronica.googlecode.com/svn/javadoc/mx/bigdata/sat/cfd/schema/ObjectFactory.html) para la versión 2.0.

```java
    // CFDI versión 3.0
    ObjectFactory of = new ObjectFactory();
    Comprobante comp = of.createComprobante();
    comp.setVersion("3.2");
    comp.setFecha(new Date());
    comp.setFormaDePago("PAGO EN UNA SOLA EXHIBICION");
    comp.setSubTotal(new BigDecimal("488.50"));
    comp.setTotal(new BigDecimal("488.50"));
    comp.setTipoDeComprobante("ingreso");
    comp.setEmisor(createEmisor(of));
    comp.setReceptor(createReceptor(of));
    comp.setConceptos(createConceptos(of));
    comp.setImpuestos(createImpuestos(of));
    CFDv32 cfd = new CFDv32(comp); 
    ...
```

```java
    // CFD versión 2.2
    ObjectFactory of = new ObjectFactory();
    Comprobante comp = of.createComprobante();
    comp.setVersion("2.2");
    comp.setFecha(new Date());
    comp.setSerie("ABCD");
    comp.setFolio("2");
    comp.setNoAprobacion(new BigInteger("49"));
    comp.setAnoAprobacion(new BigInteger("2008"));
    comp.setFormaDePago("UNA SOLA EXHIBICI\u00D3N");
    comp.setSubTotal(new BigDecimal("2000.00"));
    comp.setTotal(new BigDecimal("2320.00"));
    comp.setDescuento(new BigDecimal("0.00"));
    comp.setTipoDeComprobante("ingreso");
    comp.setEmisor(createEmisor(of));
    comp.setReceptor(createReceptor(of));
    comp.setConceptos(createConceptos(of));
    comp.setImpuestos(createImpuestos(of));
    CFDv22 cfd = new CFDv22(comp); 
    ...
```

_Nota:  Puedes encontrar un ejemplo de este código en las clases:_ [mx.bigdata.sat.cfdi.examples.ExampleCFDv32Factory](https://github.com/bigdata-mx/factura-electronica/blob/master/src/main/java/mx/bigdata/sat/cfdi/examples/ExampleCFDv32Factory.java)  y [mx.bigdata.sat.cfd.examples.ExampleCFDv22Factory](https://github.com/bigdata-mx/factura-electronica/blob/master/src/main/java/mx/bigdata/sat/cfd/examples/ExampleCFDv22Factory.java).
