# Publicar una versión

Este documento es para el administrador del repositorio.

## Primer push del repositorio

Desde esta carpeta:

```powershell
git init -b main
git add README.md RELEASE_NOTES_v1.0.7.md PUBLICACION.md .gitignore
git commit -m "Preparar canal de releases de TSSPrintMaster"
git remote add origin https://github.com/ocanalesanaliza/tssprint-releases.git
git push -u origin main
```

## Crear el Release v1.0.7

Los binarios de `release-assets/` están ignorados por Git y deben cargarse como recursos del Release, no mediante `git add`.

Con GitHub CLI instalado y autenticado:

```powershell
gh release create v1.0.7 ".\release-assets\v1.0.7\Instalar-TSSPrintMaster-1.0.7.exe" ".\release-assets\v1.0.7\TSSPrintMaster-1.0.7-win-x64.zip" ".\release-assets\v1.0.7\tssprint-update.json" ".\release-assets\v1.0.7\SHA256SUMS.txt" --repo "ocanalesanaliza/tssprint-releases" --title "TSSPrintMaster 1.0.7" --notes-file ".\RELEASE_NOTES_v1.0.7.md" --latest
```

Antes de confirmar la publicación, verifique que el Release no esté marcado como borrador ni prerelease. El actualizador utiliza la ruta pública `releases/latest/download`.

## Versiones posteriores

1. Cambiar `APP_VERSION` en el proyecto privado.
2. Compilar el servicio y el instalador.
3. Ejecutar `package-release.ps1`.
4. Copiar los recursos a una carpeta local `release-assets/vX.Y.Z`.
5. Generar y comprobar `SHA256SUMS.txt`.
6. Crear un Release estable con etiqueta `vX.Y.Z`.
7. Probar primero en un grupo piloto.
