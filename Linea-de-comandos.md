La librería incluye dos programas que permiten trabajar con los CFD desde la 
linea de comandos: ```cfd``` para trabajar con la versión 2.0 y ```cfdi``` para trabajar 
con la versión 3.0. 

Para ejecutar estos comandos cambia al directorio donde se 
descomprimieron los archivos y ejecuta cualquiera de los siguientes ejemplos:

### Para validar un CFD sellado contra el esquema:

Linux:
```
# v3.0:
./bin/cfdi validar ejemplos/cfdv3.externo.xml
# v2.0:
./bin/cfd validar ejemplos/cfdv2.externo.xml
```

Windows:
```
rem v3.0:
.\bin\cfdi validar ejemplos\cfdv3.externo.xml 
rem v2.0:
.\bin\cfd validar ejemplos\cfdv2.externo.xml 
```


### Para verificar el sello del CFDI:

Linux:
```
# v3.0
./bin/cfdi verificar ejemplos/cfdv3.externo.xml 
# v2.0
./bin/cfd verificar ejemplos/cfdv2.externo.xml 
```

Windows:
```
rem v3.0:
.\bin\cfdi verificar ejemplos\cfdv3.externo.xml 
rem v2.0:
.\bin\cfd verificar ejemplos\cfdv2.externo.xml 
```

### Para sellar el CFDI:

Linux:
```
# v3.0:
./bin/cfdi sellar ejemplos/cfdv3.xml ejemplos/emisor.key a0123456789 ejemplos/emisor.cer cfdv3_sellado.xml 
# v2.0:
./bin/cfd sellar ejemplos/cfdv2.xml ejemplos/emisor.key a0123456789 ejemplos/emisor.cer cfdv2_sellado.xml 
```

Windows:
```
rem v3.0:
.\bin\cfdi sellar ejemplos\cfdv3.xml ejemplos\emisor.key a0123456789 ejemplos\emisor.cer cfdv3_sellado.xml 
rem v2.0:
.\bin\cfd sellar ejemplos\cfdv2.xml ejemplos\emisor.key a0123456789 ejemplos\emisor.cer cfdv2_sellado.xml 
```

### Para verificar un CFDI timbrado:

Linux:
```
# v3.0:
./bin/cfdi verificar-timbrado ejemplos/cfdv3.externo.xml ejemplos/pac.cer
```

Windows:
```
rem v3.0:
.\bin\cfdi verificar-timbrado ejemplos\cfdv3.externo.xml ejemplos\pac.cer
```

#### Funcionalidad adicional, para timbrar el CFDI:

Linux:
```
# v3.0:
./bin/cfdi timbrar ejemplos/cfdv3.externo.xml ejemplos/pac.key a0123456789 ejemplos/pac.cer cfdv3_timbrado.xml
```

Windows:
```
rem v3.0:
.\bin\cfdi timbrar ejemplos\cfdv3.externo.xml ejemplos\pac.key a0123456789 ejemplos\pac.cer cfdv3_timbrado.xml
```

Nota: Estos comandos no regresan ningún mensaje si la operación fue exitosa.