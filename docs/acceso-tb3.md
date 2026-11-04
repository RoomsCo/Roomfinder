# Acceso de RoomFinder para TB3

Pantallas 02–06 de Santiago, en `feature/acceso` y PR #2 hacia `develop`. Implementación estática en HTML y CSS, revisada contra los mock-ups de escritorio y móvil el 2 de noviembre de 2026.

## Abrir y recorrer las pantallas

Abrir `pages/auth/login.html` directamente en un navegador moderno. No requiere instalación, JavaScript, servicios externos ni conexión a Internet para cargar sus recursos.

| Pantalla | Archivo | Mock-up escritorio / móvil |
| --- | --- | --- |
| 02 Iniciar sesión | `pages/auth/login.html` | `2101:450` / `2101:2175` |
| 03 Recuperar contraseña | `pages/auth/recuperar-contrasena.html` | `2101:499` / `2101:2224` |
| 04 Crear cuenta | `pages/auth/crear-cuenta.html` | `2101:533` / `2101:2258` |
| 05 Selección de rol | `pages/auth/seleccion-rol.html` | `2101:589` / `2101:2314` |
| 06 Verificar correo | `pages/auth/verificar-correo.html` | `2101:627` / `2101:2345` |

[Archivo de Figma de referencia](https://www.figma.com/design/xjYFuz0dnfAjgzTHst7P5y/RoomFinder_PRINCIPAL).

Recorrido: iniciar sesión → crear cuenta → crear cuenta (enlace inferior del formulario) → selección de rol → tarjeta «Busco alojamiento» → verificar correo. «¿Olvidaste tu contraseña?» abre recuperación y «Volver a iniciar sesión» regresa al acceso. «Cambiar correo» vuelve al registro.

## Comportamiento del Sprint 1

- Los campos contienen los ejemplos del Figma. Las contraseñas son datos ficticios de demostración.
- Los enlaces de acción solo cambian de pantalla. No autentican, registran, envían correo ni validan un código contra un servidor. Un enlace no ejecuta la validación nativa de envío del formulario.
- `required`, `type="email"`, `minlength` y `pattern` expresan restricciones HTML. CSS muestra los errores después de editar un campo inválido y salir de él (`:user-invalid`). Los errores desaparecen al corregirlo.
- El registro exige al menos ocho caracteres, una letra y un número. Los seis campos de verificación admiten un dígito cada uno.
- Los formularios usan `method="dialog"` fuera de un diálogo para impedir un envío implícito al pulsar Enter. La navegación autorizada se realiza exclusivamente mediante los enlaces.
- Los iconos de idioma y de visibilidad de contraseña son estáticos, sin enlaces ficticios `href="#"`. El contador de reenvío también es fijo.
- Las tarjetas de rol enlazan directamente a su flujo. «Continuar» conserva el estado deshabilitado inicial del mock-up y se representa como texto no interactivo con `aria-disabled`; no conduce incorrectamente al estudiante al elegir anfitrión. Guardar una selección queda fuera del alcance estático.
- Los controles de casilla son nativos y operables con teclado; su apariencia puede variar ligeramente entre navegadores.

## Dependencias de integración

Esta rama contiene las cinco pantallas de acceso. No se copiaron ni modificaron las pantallas de los compañeros.

| Destino | Enlace desde acceso | Rama que contiene el archivo |
| --- | --- | --- |
| Explorar habitaciones | Iniciar sesión y Verificar | `feature/estudiante`, PR #3 |
| Panel del anfitrión | Ofrezco una habitación | `feature/anfitrion`, PR #4 |
| Landing completa | Logotipo | `feature/landing`, PR #1 |

Los archivos `pages/estudiante/explorar.html` y `pages/anfitrion/panel.html` existen en sus respectivas ramas remotas, pero no en esta rama aislada. Estos destinos funcionarán en la aplicación integrada. El `index.html` de esta rama sigue siendo el esqueleto compartido. La integración y el merge corresponden al equipo.

## Verificación realizada

Pruebas locales en Microsoft Edge con Playwright como herramienta externa de revisión; ningún script de prueba forma parte de la web.

- Cinco pantallas en 320, 390, 768 y 1440 px: 20 combinaciones sin desplazamiento horizontal.
- Revisión visual de las diez capturas principales (390 × 844 y 1440 × 1024) contra Figma.
- Imágenes locales cargadas, dimensiones iguales a las exportaciones y fuente local disponible.
- Un solo `h1`, identificadores únicos, etiquetas y nombres de campos completos, y referencias `aria-describedby` existentes.
- Errores visibles y recuperación comprobados para contraseña, correo y código; navegación interna de acceso comprobada.
- Enter en recuperación no cambia la URL ni envía el correo como parámetro.
- Foco visible para enlaces y campos; opciones de inicio de sesión se ajustan en teléfonos estrechos.
- Sin JavaScript, manejadores de eventos, estilos inline en HTML, `!important`, frameworks ni CDNs.
- Variables, reset, base, Landing y secciones de estudiante/anfitrión del CSS original preservados.

## Recursos

Los SVG de `img/auth/` se exportaron del Figma y se mantienen sin redibujar. Los recursos compartidos existentes en `img/` permanecen intactos. Los SVG exportados pueden contener metadatos de estilo en su raíz; se cargan como imágenes externas y no como estilos inline de las páginas HTML.

La fuente [Inter](https://rsms.me/inter/) se sirve desde `fonts/inter-variable.woff2`, con su licencia SIL OFL en `fonts/OFL.txt`. El nombre de familia CSS `RoomFinder Auth Inter` limita su aplicación a las pantallas de acceso, sin cambiar la fuente de otros grupos.
