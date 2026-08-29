# TSSPrintMaster

Servicio de impresión local para equipos Windows, con activación autorizada y actualizaciones automáticas mediante GitHub Releases.

[![Última versión](https://img.shields.io/github/v/release/ocanalesanaliza/tssprint-releases?label=versi%C3%B3n)](https://github.com/ocanalesanaliza/tssprint-releases/releases/latest)
[![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4)](https://github.com/ocanalesanaliza/tssprint-releases/releases)

## Instalación inicial

1. Abra la sección [Releases](https://github.com/ocanalesanaliza/tssprint-releases/releases/latest).
2. Descargue `Instalar-TSSPrintMaster-X.Y.Z.exe`.
3. Ejecute el instalador como administrador.
4. Introduzca la clave asignada por el administrador de TSSPrintMaster.
5. Espere el mensaje de instalación completada.

Cada clave queda vinculada al equipo autorizado. No publique claves de activación en incidencias, capturas de pantalla o archivos compartidos.

## Verificación

Abra PowerShell y compruebe el servicio:

```powershell
Get-Service TSSPrintMaster
```

El estado esperado es `Running`. Para verificar el servidor local de impresión:

```powershell
Test-NetConnection 127.0.0.1 -Port 9000
```

El resultado esperado es `TcpTestSucceeded: True`.

## Actualizaciones automáticas

El instalador registra la tarea de Windows `TSSPrintMaster-Actualizacion`. Cuatro veces al día, la tarea:

1. Consulta el manifiesto del último GitHub Release.
2. Compara la versión instalada.
3. Descarga solamente una versión nueva.
4. Verifica su SHA-256.
5. Reemplaza el servicio y comprueba el puerto local.
6. Restaura automáticamente la versión anterior si la nueva falla.

Las computadoras esperan un intervalo aleatorio antes de consultar GitHub para distribuir la carga del despliegue.

## Archivos de cada Release

| Archivo | Propósito |
|---|---|
| `Instalar-TSSPrintMaster-X.Y.Z.exe` | Instalación inicial autorizada |
| `TSSPrintMaster-X.Y.Z-win-x64.zip` | Paquete consumido por el actualizador |
| `tssprint-update.json` | Versión y SHA-256 del paquete |
| `SHA256SUMS.txt` | Verificación manual de los recursos |

No extraiga ni ejecute manualmente `TSSPrintMaster.exe` desde el ZIP de actualización.

## Requisitos

- Windows 10 u 11 de 64 bits.
- Permisos administrativos durante la instalación inicial.
- Acceso a Internet durante la activación y para buscar actualizaciones.
- Impresoras y controladores configurados en Windows.

Después de la activación inicial, Apps Script no interviene en las impresiones, el arranque del servicio ni las actualizaciones.

## Diagnóstico

Estado de la tarea automática:

```powershell
Get-ScheduledTask -TaskName "TSSPrintMaster-Actualizacion"
```

Registro del actualizador:

```powershell
Get-Content "C:\ProgramData\TSSPrintMaster\Logs\updater.log" -Tail 50
```

Para soporte, informe la versión, sucursal, nombre del equipo y mensajes de error. No adjunte claves de activación ni archivos de licencia.

## Seguridad

- Las licencias se firman digitalmente y se validan localmente.
- El servicio usa un certificado final exclusivo para `localhost` con `CA=false`.
- Los paquetes de actualización se verifican mediante SHA-256.
- Este repositorio no debe contener claves privadas, licencias o tokens de acceso.

