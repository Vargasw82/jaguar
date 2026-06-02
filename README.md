# README — México Salvando al Jaguar · Sitio Web 2026

Guía para el desarrollador que modifique o mantenga este repositorio.

---

## URL de producción

| Página | URL |
|---|---|
| Home | https://vargasw82.github.io/jaguar/ |
| Shot Jaguar (QR) | https://vargasw82.github.io/jaguar/shotJaguar/ |

Publicado vía **GitHub Pages** desde la rama `main`, carpeta raíz `/`.

---

## Estructura del repositorio

```
/
├── index.html               # Página principal (todo el sitio en un solo archivo)
├── index(null).html         # Versión anterior — NO usar, conservar como referencia
│
├── shotJaguar/
│   └── index.html           # Página de activación Shot Jaguar (solo acceso por QR)
│
├── shot_jaguar/             # Fotos para la página /shotJaguar (9 imágenes)
│   ├── Chuz_Captura_May2023.jpg
│   ├── Cria1.png
│   ├── Cria2.png
│   ├── David_Captura_May2023.png
│   ├── Pedro.jpg
│   ├── Regina_Captura_May2023.png
│   ├── Sol.jpg
│   ├── Tony_Gemini.png
│   └── Veronica_Gemini.png
│
├── Patrocinadores/          # Logos de patrocinadores (8 imágenes)
│   ├── Patro1.png … patro5.png
│   ├── CalakmulAmigo.png
│   ├── GC_Logo.png
│   └── StopExt.png
│
└── *.png / *.jpg            # Imágenes de fondo, íconos y assets generales
```

> **Atención:** `shot_jaguar/` (con guión bajo, minúsculas) y `shotJaguar/` (camelCase) son dos carpetas distintas. No confundirlas. macOS es case-insensitive pero el servidor de GitHub Pages es case-sensitive.

---

## Página principal — `index.html`

Sitio estático de una sola página (no hay framework ni build step). Secciones en orden:

1. **Ticker** — barra superior con donaciones ficticias animadas
2. **Nav** — fija, con hamburger en móvil
3. **Hero** — foto de jaguar, scorebug y feed de cronología
4. **Stats bar** — contadores animados
5. **La Paradoja** — contexto de conservación
6. **Alineación de Patrocinadores** — grid 4 columnas, logos de `Patrocinadores/`
7. **Cada Peso Tiene Destino** — 5 tarjetas de destino de fondos
8. **Donar** — CTA principal
9. **Comunidad (#MiSelecciónEsElJaguar)** — widget social Behold
10. **Respaldo Científico** — Dr. Gerardo Ceballos / ANCJ
11. **CTA final**
12. **Footer**

### Links importantes ya configurados

| Elemento | Destino |
|---|---|
| Botón "Donar" (hero y CTA) | GoFundMe: https://gofund.me/153706751 |
| Logo ANCJ (hero) | https://www.ancjaguar.org/ |
| Logo ANCJ (sección Dr. Ceballos) | https://www.ancjaguar.org/ |
| Texto "ANCJ" en footer | https://www.ancjaguar.org/ |

---

## Página Shot Jaguar — `shotJaguar/index.html`

Página independiente, accesible únicamente por código QR en activaciones presenciales. **No está linkeada desde el home.**

- Muestra 1 foto a la vez de `shot_jaguar/`, en orden aleatorio (Fisher-Yates), rotando cada 5 segundos con fade
- Botón **Donar Ahora** → GoFundMe: https://gofund.me/153706751
- Botón **Ir al Home** → `../index.html`
- El QR debe apuntar a: `https://vargasw82.github.io/jaguar/shotJaguar/`

Para agregar o quitar fotos: colocar/eliminar archivos en `shot_jaguar/` y actualizar el array `photos` en el `<script>` al final de `shotJaguar/index.html`.

---

## Flujo de trabajo

### Clonar y probar localmente

```bash
git clone https://github.com/Vargasw82/jaguar
cd jaguar
python3 -m http.server 8000
# Abrir http://localhost:8000
```

### Publicar cambios

```bash
git add archivo-modificado.html
git commit -m "Descripción corta del cambio"
git push origin main
```

GitHub Pages se actualiza automáticamente en ~1-2 minutos tras el push a `main`.

### Trabajar en una rama (recomendado para cambios grandes)

```bash
git checkout -b feature/nombre-del-cambio
# ... editar ...
git push -u origin feature/nombre-del-cambio
# Abrir Pull Request en GitHub y hacer merge a main
```

---

## Notas para el backend

- **No hay backend ni base de datos** — todo es HTML/CSS/JS estático.
- **No hay build step** — editar directamente los `.html`, no se necesita npm ni compilador.
- **Donaciones** van a GoFundMe externo; no hay procesamiento de pagos en este repo.
- **Widget social** (sección Comunidad) usa Behold (`behold.so`) — la configuración está en su dashboard, no en este repo.
- **`.DS_Store`** está trackeado por error. Conviene agregar un `.gitignore`:

```
.DS_Store
```

- **`index(null).html`** es un archivo residual de una versión anterior. Se puede eliminar cuando se confirme que no se necesita.
