# README — Instrucciones para el programador Backend

Breve guía para quien va a modificar y publicar el sitio web.

## Propósito
Este repositorio contiene la versión unificada del sitio web. El objetivo de esta guía es explicar cómo probar, editar y publicar cambios de forma segura.

## Estado actual (importante)
- El contenido actual fue subido a la rama `main` del remoto https://github.com/Vargasw82/jaguar.  
- Se creó la etiqueta remota `backup-before-clean` como respaldo antes de limpiar ramas antiguas.  
- Commit actual principal: `e95ce68d642dae5528c0c1ab073d762d5c671536`.

## Estructura relevante
- `index.html`, `index(null).html` — páginas principales.
- `Patrocinadores/` — imágenes y recursos de patrocinadores.
- `shotJaguar/` y `shot_jaguar/` — fotos; cuidado con nombres similares (mayúsculas/minúsculas).
- Archivos de imagen en la raíz (`*.png`, `*.jpg`) y otros activos.

Nota: hay un archivo `.DS_Store` en el repo; recomendamos añadir `.gitignore` para evitar subirlo de nuevo.

## Flujo de trabajo recomendado
1. Clonar el repositorio:

```bash
git clone https://github.com/Vargasw82/jaguar
cd jaguar
```

2. Probar el sitio localmente (servidor web simple):

```bash
python3 -m http.server 8000
# o usando Node:
npx serve .
```
Abrir http://localhost:8000

3. Hacer cambios en los archivos HTML/CSS/imagenes. Archivos típicos a editar: `index.html`, archivos en `Patrocinadores/`, carpetas `shotJaguar/` o `shot_jaguar/`.

4. Confirmar, commitear y enviar:

```bash
git add -A
git commit -m "Descripción corta del cambio"
git push origin main
```

Si por alguna razón necesitas sobrescribir remoto (NO recomendado), usar:

```bash
git push origin main --force
```

5. (Opcional y recomendado en desarrollos grandes) trabajar en una rama:

```bash
git checkout -b feature/nueva-cosa
# cuando esté lista:
git push -u origin feature/nueva-cosa
# abrir PR y luego merge a main
```

## Reversión al respaldo
Si necesitas volver al respaldo creado:

```bash
git fetch --tags
git checkout -b restore-backup backup-before-clean
```

## Notas y buenas prácticas
- Evitar commits de archivos del sistema (`.DS_Store`). Añadir `.gitignore` con:

```text
.DS_Store
# otras entradas según necesidad
```

- Atención a nombres de carpetas con diferencias de mayúsculas: macOS por defecto es case-insensitive y puede causar conflictos si el servidor de producción es case-sensitive.
- Si el sitio se publica con GitHub Pages o CI/CD, confirmar el flujo de despliegue en la configuración del repositorio.

## Soporte
Si quieres, puedo:
- Añadir `.gitignore` y limpiar `.DS_Store`.
- Configurar una rama de despliegue o un workflow básico de GitHub Actions.
- Crear una release o tag descriptivo para producción.

Indica qué prefieres y lo hago.
