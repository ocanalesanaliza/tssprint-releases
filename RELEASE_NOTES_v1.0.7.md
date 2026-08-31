# TSSPrintMaster 1.0.7

Esta versión recupera el diseño completo en impresoras TSC y corrige permanentemente la ruta del servicio.

## Impresión

- Los textos se generan nuevamente mediante TSCLIB.dll, evitando que ciertos modelos TSC omitan área, paciente, edad y sexo.
- El diseño parte de la geometría original de la aplicación.
- La altura del código de barras baja de 86 a 69 puntos, exactamente un 20%.
- El área y edad/sexo usan tamaño 20; el nombre del paciente usa tamaño 24.
- Zebra y TSC conservan la misma geometría general.

## Actualización

- El actualizador comprueba y corrige la ruta registrada de TSSPrintMaster.
- Si encuentra una instalación antigua como C:\services\TSSPrintMaster.exe, la cambia a C:\Program Files\TSSPrintMaster\TSSPrintMaster.exe y reinicia el servicio.
- La reparación se ejecuta incluso cuando no hay una versión más reciente disponible.
- El servicio también vuelve a fijar su ruta correcta durante el inicio.

## Instalador

- Los diálogos de instalación y desinstalación ahora son nativos de Windows y ya no dependen de Tkinter/Tcl.
