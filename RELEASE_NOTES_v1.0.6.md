# TSSPrintMaster 1.0.6

Esta versión corrige la aplicación del diseño en impresoras TSPL.

## Corrección principal

- Las impresoras TSPL reciben ahora el formato mediante comandos RAW `WINDOWSFONT` y `BARCODE`, igual que la prueba directa validada físicamente.
- Se evita la ruta anterior mediante `TSCLIB.dll`, que podía producir un diseño distinto aunque el servicio estuviera actualizado.
- Se conserva el diseño solicitado: área 22, paciente 26, edad/género 22 y código de barras con altura 50 en `Y=90`.

## Diagnóstico y mantenimiento

- Se agrega `C:\ProgramData\TSSPrintMaster\Logs\routing.log` con la ruta, lenguaje y geometría aplicada, sin guardar datos del paciente.
- El servicio recupera automáticamente la tarea `TSSPrintMaster-Actualizacion` cuando no existe.
- Se conserva el desinstalador integrado.
