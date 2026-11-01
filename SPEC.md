# RoomFinder

Sitio web responsivo donde estudiantes universitarios encuentran habitaciones cerca de su campus y anfitriones las publican. Startup RoomCo.

> Solo **Datos** y **Estructura** son de este proyecto. El resto sirve de punto de partida para cualquier proyecto HTML y CSS con Figma.

## Datos
- Figma: https://www.figma.com/design/xjYFuz0dnfAjgzTHst7P5y/RoomFinder_PRINCIPAL
- Página del Figma con las pantallas: «3.4 · Mock-ups» (tableros «04 · Mockups · Desktop» y «04 · Mockups · Mobile»)
- Sistema de diseño: página «3.3 · Sistema de diseño» y variables de las colecciones «RoomFinder · Primitivos» y «RoomFinder · Sistema»
- Fuente: Inter
- UI: HTML y CSS puros

## Cómo trabajar
Haz solo la pantalla que te pida. Léela en el Figma, impleméntala y verifica que se vea bien al abrirla en el navegador.
Al terminar, lista los archivos creados y qué quedó pendiente.
No cambies las variables ni los estilos de otras pantallas.

## Estructura
Sigue la siguiente estructura:

```
├── index.html                          # 01 Landing page, con su propia cabecera y pie
├── css/
│   └── styles.css                      # Único CSS: variables, reset y estilos de todas las pantallas
├── js/                                 # Vacía por ahora, sin archivos
├── img/                                # Imágenes del sitio
└── pages/
    ├── auth/                           # Grupo de acceso (se nombra por su función)
    │   ├── login.html                  # 02 Iniciar sesión
    │   ├── recuperar-contrasena.html   # 03 Recuperar contraseña
    │   ├── crear-cuenta.html           # 04 Crear cuenta
    │   ├── seleccion-rol.html          # 05 Selección de rol
    │   └── verificar-correo.html       # 06 Verificar correo universitario
    ├── estudiante/                     # Grupo por tipo de usuario
    │   ├── explorar.html               # 07 Explorar habitaciones
    │   ├── detalle-habitacion.html     # 08 Detalle de habitación
    │   ├── favoritos.html              # 09 Favoritos
    │   ├── comparar.html               # 10 Comparar habitaciones
    │   ├── solicitar-visita.html       # 11 Solicitar visita
    │   ├── confirmacion-solicitud.html # 12 Confirmación de solicitud
    │   ├── mis-solicitudes.html        # 13 Mis solicitudes de visita
    │   └── perfil.html                 # 14 Perfil y preferencias
    └── anfitrion/
        ├── panel.html                  # 15 Panel del anfitrión
        ├── publicacion.html            # 16 Crear o editar publicación
        ├── interesados.html            # 17 Interesados y comparación
        ├── solicitudes.html            # 18 Solicitudes de visita · Anfitrión
        └── reportes.html               # 19 Reportes de demanda
```
Un grupo es un conjunto de pantallas que comparten el mismo aspecto (cabecera y pie).

## Alcance
Solo dibuja cada pantalla y conéctala: formularios con sus campos, listas con datos de ejemplo
y enlaces entre pantallas. La lógica no existe en este proyecto.

- **Sí:** HTML semántico, CSS, `<form>` con atributos de validación (`required`, `type="email"`, `minlength`), listas con datos de ejemplo fijos, navegación con `<a href>`.
- **No:** JavaScript (la carpeta `js/` queda vacía; ni `<script>` ni `onclick`), frameworks, librerías, CDNs ni preprocesadores. No calcules, filtres ni busques. Usa los valores del Figma, tal cual.
- Contadores, chips y buscadores: déjalos dibujados, sin comportamiento.
- Si dudas, déjalo fijo.

## Reglas
- **Archivos:** un `.html` por pantalla dentro de la carpeta de su grupo en `pages/`, y un solo `css/styles.css` para todo el sitio. Nombres en minúsculas y guiones.
- **HTML:** semántico (`header`, `nav`, `main`, `section`, `footer`), un solo `<h1>` por página, `alt` en todas las imágenes y `<label>` en cada campo.
- **CSS:** clases con nombres claros (estilo BEM), sin estilos inline ni `!important`. Colores, fuentes y espacios van como variables al inicio de `css/styles.css`, y los estilos de cada pantalla van en su propia sección con un comentario.
- **Formularios:** cada campo con su `<label>`, `name` y validación HTML. El mensaje de error va debajo del campo, en el idioma del Figma.
- **Navegación:** todos los botones y enlaces usan `<a href>`, también el que envía un formulario.
- **Rutas:** son relativas. `index.html` usa `css/styles.css` e `img/...`. Las páginas de `pages/<grupo>/` usan `../../css/styles.css` e `../../img/...`. Para ir a otra página de otro grupo: `../estudiante/explorar.html`; para volver al inicio: `../../index.html`.
- **Landing (index.html):** es una sola página en la raíz, fuera de `pages/`. Lleva su propia cabecera y pie, y sus botones salen hacia los demás grupos.
- **Responsive:** el Figma trae dos diseños por pantalla, escritorio y móvil. Impleméntalos en el mismo `.html` con `@media` en `css/styles.css`: empieza por el móvil y usa `@media (min-width: 768px)` para el escritorio. Usa Flexbox o Grid, sin archivos ni páginas aparte para móvil.
- **Diseño:** respeta el Figma en ambos tamaños y usa las variables de `css/styles.css`.
- **Pantallas alternativas** (error, vacío, rechazo): son estados de la misma pantalla, no páginas nuevas. Por ahora solo los errores de formulario.
- Si dudas, pregunta. No inventes pantallas.
