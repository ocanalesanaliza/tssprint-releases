# TSSPrintMaster 1.0.1

Actualización de mantenimiento preparada para validar el canal de actualizaciones automáticas de TSSPrintMaster.

## Instalación nueva

Descargue y ejecute `Instalar-TSSPrintMaster-1.0.1.exe` como administrador. La primera instalación solicitará una clave de licencia.

## Equipos con TSSPrintMaster instalado

No necesitan ejecutar el instalador. La tarea `TSSPrintMaster-Actualizacion` detectará esta versión, validará su integridad, reemplazará el ejecutable y reiniciará el servicio automáticamente.

La comprobación también puede iniciarse manualmente desde PowerShell como administrador:

```powershell
& "C:\Program Files\TSSPrintMaster\updater.ps1" -NoRandomDelay
```
