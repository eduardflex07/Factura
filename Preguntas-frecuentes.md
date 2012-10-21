**¿Puedo utilizar los componentes en aplicaciones comerciales?**

Sí, siempre y cuando se atribuya adecuadamente según los términos de la [http://www.apache.org/licenses/LICENSE-2.0 Apache License, Version 2.0]. Para más información consulta la página de  [http://www.apache.org/foundation/licence-FAQ.html preguntas frecuentes] de la Licencia.

**¿Cuáles características implementa?**

La librería implementa el sellado de los CFDI con SHA1 y RSA, así como la verificación del sello. Por otro lado implementa el timbrado de los CFDI así como la verificación del timbre.

Adicionalmente se ha agregado soporte para el  sellado de los CFD v2.0 con SHA1 y RSA, así como la verificación del sello.

**¿Qué debo hacer para reportar un problema o sugerir una mejora?**

Busca la respuesta en la sección de [preguntas frecuentes](https://github.com/bigdata-mx/factura-electronica/wiki/Preguntas-frecuentes) o en la sección de 
[seguimiento](https://github.com/bigdata-mx/factura-electronica/issues?state=open). Si no encuentras la respuesta, crea una nueva entrada utilizando la liga de `New Issue` y haremos todo lo posible por solucionarlo.

**¿Cómo puedo descargar el código?**

Solo necesitas descargar el código si vas a modificar o mejorar la funcionalidad central de la librería, o si quieres conocer su funcionamiento. Para hacerlo puedes clonar el repositorio utilizando git:

```
git clone git://github.com/bigdata-mx/factura-electronica.git
```

O crear tu propio `Fork` y reincorporar tus cambios utilizando un `Pull Request` [leer más](https://help.github.com/articles/fork-a-repo). 

Para compilar el código fuente, sigue las instrucciones en: 

https://github.com/bigdata-mx/factura-electronica/wiki/Compilar-el-codigo-fuente

En general puedes utilizar el .jar de la versión más reciente que esté disponible en https://github.com/bigdata-mx/factura-electronica/downloads, para realizar las funciones principales de los CFD.

**¿Cuáles son las dependencias de los componentes?**

Actualmente los componentes dependen de las siguientes librerías: [http://code.google.com/p/guava-libraries/ guava-libraries], [http://commons.apache.org/codec/ Commons Codec] y [http://juliusdavies.ca/commons-ssl/ not-yet-commons-ssl], todas ellas disponibles bajo la Licencia Apache, Version 2.0 y las librerías de [https://jaxb.dev.java.net/ JAXB] disponibles bajo la licencia [http://www.sun.com/cddl/ CDDL]. Adicionalmente se utiliza la librería [http://www.bouncycastle.org/java.html Bouncy Castle] para depurar la aplicación.

**¿Cómo agrego el código del SVN a NetBeans o Eclipse para compilar las librerías?**

### Eclipse

Para agregar el código a Eclipse es necesario instalar el plugin [http://m2eclipse.sonatype.org/installing-m2eclipse.html m2eclipse] 
e importar el proyecto utilizando el menú: `File > Import > Maven > Existing Maven Projects`.
Finalmente sobre el proyecto de ecplise `Maven > Update Project Configuration` para generar los esquemas y actualizar la configuración del proyecto.

### NetBeans
Para agregar el código a NetBeans es muy importante tener instalada al menos la versión 3.0.1 de [
http://maven.apache.org/download.html Maven].  Para configurar la versión de Maven en NetBeans:

* `Tools > Options > Miscellaneous  > Maven`
* En External Maven Home, agrega el PATH a la versión 3.0.1 de Maven

A continuación importa el proyecto de la siguiente manera: `File > New Project > Maven > Maven Project with Existing POM` 
y en el siguiente diálogo selecciona el directorio con el código de git.  

Finalmente construye el proyecto con el comando Build. Esto compila el código generado y corrige los errores de compilación
que aparecen al importar el proyecto.

Para más información consulta: http://wiki.netbeans.org/MavenBestPractices

**¿Se pueden utilizar las librerías en Google App Engine?**

Sí, las librerías están diseñadas para funcionar sobre [Google App Engine](http://code.google.com/appengine/). Para hacerlo es necesario utilizar el TransofrmerFactory de [Xalan](http://xml.apache.org/xalan-j/), ya que la implementación de `javax.xml.transform.TransformerFactory` no es compatible con las restricciones de la plataforma en App Engine. 

Puedes cambiar el TransformerFactory de la siguiente manera:

```
      CFDv3 cfd = new CFDv3(...);
      TransformerFactory factory = TransformerFactory.newInstance(
                        "org.apache.xalan.processor.TransformerFactoryImpl",
                         Thread.currentThread().getContextClassLoader()); 
      cfd.setTransformerFactory(factory);
```

En esta liga hay un ejemplo de un CFD generado en GAE utilizando las librerías: http://factura-electronica.appspot.com/ejemplos/cfdv3

**¿Cómo utilizo caracteres Unicode (caracteres acentuados y otros caracteres especiales) dentro del código de mi programa?**

La forma recomendada para incluir caracteres Unicode en el código fuente es en su forma escapada, de esta forma los caracteres siempre corresponderán a su representación Unicode independientemente de como esté codificado el archivo. Por ejemplo, en lugar de utilizar: 

   ```comp.setFormaDePago("UNA SOLA EXHIBICIÓN");```

es conveniente utilizar:

   ```comp.setFormaDePago("UNA SOLA EXHIBICI\u00D3N");```

Ya que la segunda forma es independiente de la codificación de la plataforma donde se compile el programa. Esto es importante ya que la codificación del CFD se hace en UTF-8 y una codificación distinta puede resultar en errores al verificar el certificado.

**¿Cuál es el objetivo de escribir esta librería?**

La librería busca tener una base de código común para el desarrollo de aplicaciones de factura electrónica escritas en Java, a fin de que los desarrolladores  dirigan sus esfuerzos a generar aplicaciones con mayor valor agregado. Al mismo tiempo que las librerías se benefician de su uso generalizado y las mejoras provenientes de la comunidad.

10. *¿Cuáles son las siguientes metas del proyecto?

Las siguientes metas son:
  * Mejorar los mensajes de error del programa de línea de comandos
  * Agregar los esquemas de los complementos

11. *¿Cómo me entero de las actualizaciones y mejoras a las librerías?

Entérate de las mejoras y actualizaciones a las librerías a través de nuestra [http://www.twitter.com/bigdata_mx cuenta de twitter]  [http://www.twitter.com/bigdata_mx http://twitter-badges.s3.amazonaws.com/t_mini-a.png]