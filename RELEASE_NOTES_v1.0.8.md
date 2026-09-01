# TSSPrintMaster 1.0.8

Esta versión corrige el desplazamiento acumulativo de las etiquetas.

## Corrección del avance

- Se restaura la configuración física utilizada por la aplicación original: SIZE 2,1.
- Se restaura GAP 3 mm,3 mm, incluyendo el desplazamiento original del sensor.
- Se evita que cada impresión avance menos de lo necesario y termine cortando la parte superior del siguiente sticker.
- Para impresoras ZPL se usa el equivalente de 2 × 1 pulgadas a 203 DPI.

## Diseño conservado

- Área y edad/sexo mantienen tamaño 20.
- El nombre del paciente mantiene tamaño 24.
- El código de barras mantiene altura 69, un 20% menos que los 86 puntos del diseño original.
- Se conservan las reparaciones automáticas de la ruta del servicio y del actualizador.
