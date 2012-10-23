Los usuarios avanzados que quieran **mejorar o extender** las librerías pueden descargar y compilar el código fuente. Para utilizar las librerías en tus propios desarrollos no es necesario descargar el código fuente (descarga los archivos ya compilados o utiliza las librerías en maven).

#### Pre-requisitos
Para trabajar con el código fuente de la librería de factura electrónica debes tener instalados los siguientes sistemas:

* Java >= 6
* Maven

#### Obtener el código fuente
Existen dos opciones A) clonar el repositorio utilizando git para explorar el código fuente.

```
git clone git://github.com/bigdata-mx/factura-electronica.git
```

B) Crear tu propio `Fork` a fin de reincorporar tus cambios al repositorio utilizando un `Pull Request` [leer más](https://help.github.com/articles/fork-a-repo). 


```
git@github.com:bigdata-mx/factura-electronica.git
```


#### Compilar los componentes
Para compilar los componentes, utiliza el comando:

 mvn compile

este comando preparará todas las dependencias y generará el código necesario 
para trabajar con el XSD de la versión 3.0 y 2.0 del CFD y la versión 1.0 del 
TFD.

#### Ejecutar el programa de ejemplo
Para ejecutar el programa de ejemplo, utiliza el comando:

 mvn exec:java