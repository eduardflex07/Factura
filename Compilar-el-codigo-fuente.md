Los usuarios avanzados que quieran **mejorar o extender** las librerías pueden descargar y compilar el código fuente. Para utilizarlas en tus propios desarrollos no es necesario descargar el código fuente (descarga los archivos ya compilados o utiliza las librerías en maven).

 Para ello es necesario seguir los siguientes pasos:

#### Pre-requisitos
Para trabajar con el código fuente de la librería de factura electrónica debes
 tener instalados los siguientes sistemas:

* Java 6
* Maven

#### Obtener el código fuente
Realiza un Fork del repositorio:

git@github.com:bigdata-mx/factura-electronica.git


Revisa la información en las preguntas frecuentes para agregar el código fuente
a un IDE (Netbeans o Eclipse)

#### Compilar los componentes
Para compilar los componentes, utiliza el comando:

 mvn compile

este comando preparará todas las dependencias y generará el código necesario 
para trabajar con el XSD de la versión 3.0 y 2.0 del CFD y la versión 1.0 del 
TFD.

#### Ejecutar el programa de ejemplo
Para ejecutar el programa de ejemplo, utiliza el comando:

 mvn exec:java