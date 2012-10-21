*0.1.5* -- 25/12/2010
  * Se corrigió y documentó el soporte para Google App Engine
  * Se agregó soporte para cargar el `Comprobante` directamente de un archivo sin pasar por el CFD
  * Se agregó la capacidad de obtener la cadena original y el sello a partir de un `Comprobante` sellado.
  * Se cambiaron las hojas de transformación XSLT por las nuevas hojas del SAT para que los `CFDI` sean validos de acuerdo al [https://www.consulta.sat.gob.mx/sicofi_web/moduloECFD_plus/ValidadorCFDI/Validador%20cfdi.html validador] oficial del SAT.

*0.1.4* -- 21/11/2010
  * Se corrigió un [http://code.google.com/p/factura-electronica/issues/detail?id=14 error] al verificar el comprobante v2.0 utilizando el certificado interno.
  * Se generó una distribución binaria que incluye todas las dependencias y archivos binarios para ejecutar la línea de comandos.
  * Se mejoró la documentación del wiki.

*0.1.3* -- 12/11/2010

  * Se agregó funcionalidad para la versión 2.0 del CFD en la clase CFDv2.
  * Se cambió la estructura de los _packages_ al incluir la versión 2.0 del CFD.
  * Se eliminaron las dependencias con hojas de estilo _XSLT_ externas, ahora están incluidas en la librería.
  * Se programaron pruebas unitarias para cada uno de los componentes. 

*0.1.2* -- 29/10/2010
  * Primera versión estable.