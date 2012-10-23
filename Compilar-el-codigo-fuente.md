Los usuarios avanzados que quieran **mejorar o extender** las librerías pueden descargar y compilar el código fuente. Para utilizar las librerías en tus propios desarrollos no es necesario descargar el código fuente (descarga los archivos ya compilados o utiliza las librerías en maven).

### Pre-requisitos
Para trabajar con el código fuente de la librería de factura electrónica debes tener instalados los siguientes sistemas:

* Java >= 6
* Maven

### Obtener el código fuente
Existen dos opciones A) clonar el repositorio utilizando git para explorar el código fuente.

```
git clone git://github.com/bigdata-mx/factura-electronica.git
```

B) Crear tu propio `Fork` a fin de reincorporar tus cambios al repositorio utilizando un `Pull Request` [leer más](https://help.github.com/articles/fork-a-repo). 

### Agregar el código fuente a un IDE

#### Eclipse

Para agregar el código a Eclipse es necesario instalar el plugin [m2eclipse](http://m2eclipse.sonatype.org/installing-m2eclipse.html) 
e importar el proyecto utilizando el menú: `File > Import > Maven > Existing Maven Projects`.
Finalmente sobre el proyecto de ecplise `Maven > Update Project Configuration` para generar los esquemas y actualizar la configuración del proyecto.

#### NetBeans
Para agregar el código a NetBeans es muy importante tener instalada al menos la versión 3.0.1 de [Maven]
(http://maven.apache.org/download.html). Para configurar la versión de Maven en NetBeans:

* `Tools > Options > Miscellaneous  > Maven`
* En External Maven Home, agrega el PATH a la versión 3.0.1 de Maven

A continuación importa el proyecto de la siguiente manera: `File > New Project > Maven > Maven Project with Existing POM` 
y en el siguiente diálogo selecciona el directorio con el código de git.  

Finalmente construye el proyecto con el comando Build. Esto compila el código generado y corrige los errores de compilación que aparecen al importar el proyecto.

Para más información consulta: http://wiki.netbeans.org/MavenBestPractices

### Compilar en línea de comandos

#### Compilar los componentes
Para compilar los componentes, utiliza el comando:

 ```mvn compile```

este comando preparará todas las dependencias y generará el código necesario 
para trabajar con el XSD de la versión 3.0 y 2.0 del CFD y la versión 1.0 del 
TFD.

#### Ejecutar el programa de ejemplo
Para ejecutar el programa de ejemplo, utiliza el comando:

 ```mvn exec:java```

#### Probar los componentes
Para ejecutar el programa de ejemplo, utiliza el comando:

 ```mvn compile test```