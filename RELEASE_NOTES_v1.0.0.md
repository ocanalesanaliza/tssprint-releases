# TSSPrintMaster 1.0.0

Primera versión del canal administrado de TSSPrintMaster.

## Incluye

- Instalación con activación única mediante una clave autorizada.
- Licencia firmada y vinculada localmente al equipo.
- Servicio de impresión automático en Windows.
- Servidor seguro en `wss://localhost:9000`.
- Certificado final de `localhost` con `CA=false`.
- Retiro automático del certificado CA legado conocido.
- Actualización automática desde GitHub Releases.
- Validación SHA-256 y rollback ante fallos.
- Tarea de actualización ejecutada como `SYSTEM` cuatro veces al día.

## Recomendación de despliegue

Instalar primero en un grupo piloto pequeño y confirmar impresión térmica, de impacto y etiquetas antes de ampliar el despliegue.

