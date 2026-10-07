# Reingeniería del Ecosistema Digital ITEC

**TP Integrador — Análisis y rediseño integral del portal ITEC**

Rediseño y desarrollo del sitio web del [Instituto Tecnológico El Molino](https://itec-elmolino.edu.ar/) (Esperanza, Santa Fe). Abarca toda la estructura principal del sitio: **Inicio, Institucional, Formación, Servicios y Contacto**, con todas sus subsecciones.

Hecho con HTML, CSS y JavaScript sobre [Astro](https://astro.build/). El resultado final es un sitio estático: solo archivos HTML, CSS, JS e imágenes.

## Datos del trabajo

| | |
| :--- | :--- |
| **Carrera** | Tecnicatura Superior en Desarrollo de Software — 3° año |
| **Institución** | ITEC El Molino |
| **Unidad curricular** | Programación II |
| **Docente** | Nicolas Zeballos |
| **Ciclo lectivo** | 2026 |

**Integrantes:** Bertram, Ivana · Lamerata, Daniela · Stauber, Tomas

## Cómo ejecutarlo

Requiere [Node.js](https://nodejs.org/) 22.12 o superior.

```sh
npm install      # instala las dependencias (solo la primera vez)
npm run dev      # servidor de desarrollo en http://localhost:4321
```

| Comando | Qué hace |
| :--- | :--- |
| `npm run dev` | Levanta el sitio en `localhost:4321` y lo recarga con cada cambio |
| `npm run build` | Genera el sitio final en la carpeta `dist/` |
| `npm run preview` | Sirve la carpeta `dist/` para revisar el resultado final |

## Qué se entrega y dónde está

| Punto de la consigna | Entregable | Ubicación |
| :--- | :--- | :--- |
| 4. Análisis, fallas y propuestas de mejora | Documento PDF | Se entrega aparte |
| 5. Diseño visual (UI/UX) | Prototipo navegable del sitio completo | [`src/assets/ITEC El Molino - Prototipo.html`](src/assets/ITEC%20El%20Molino%20-%20Prototipo.html) (se abre directo en el navegador) |
| 5. Diseño visual (UI/UX) | Brief de diseño que dio origen al prototipo | [`src/assets/prompt-estetico-itec.md`](src/assets/prompt-estetico-itec.md) |
| 5. Programación | Sitio rediseñado | Este repositorio (`src/`) |

## Del análisis al código

Cada falla detectada en el análisis del sitio original tiene una solución concreta en el código.

| Falla en el sitio original | Solución | Dónde está |
| :--- | :--- | :--- |
| Misión, Visión, Autoridades y Equipo estaban mezclados en un solo bloque de texto | Una página propia para cada uno, accesible desde el menú | `src/pages/institucional/` |
| Para pasar de una subsección a otra había que volver a la página de Institucional | Menú desplegable con las 6 subsecciones, presente en todas las páginas | `src/components/Header.astro` |
| En el celular no aparecían las subsecciones de Institucional | Menú hamburguesa con todas las opciones | `src/components/Header.astro` |
| Footer mínimo, sin datos de contacto ni mapa del sitio | Footer en 4 columnas: contacto, mapa del sitio, newsletter, e instituciones asociadas con redes | `src/components/Footer.astro` |
| Newsletter y redes sociales dependían de plugins de terceros | Validación propia en JavaScript y enlaces directos, sin plugins | `src/components/Footer.astro` |
| Las carreras se mostraban como texto continuo y extenso | Una tarjeta por carrera con acordeones (duración, acreditación, plan de estudio) | `src/components/Carrera.astro` |
| Los servicios eran bloques de texto con poca diferenciación | Tres tarjetas independientes: Servicios Tecnológicos, UVT y Asistencia Técnica | `src/pages/servicios.astro` |
| Tipografías, colores y espaciados distintos entre secciones | Una sola paleta, escala tipográfica y set de clases para todo el sitio | `src/styles/global.css` |

## Decisiones técnicas

**Astro en lugar de HTML suelto.** El sitio tiene 15 páginas que comparten encabezado y pie. En HTML puro eso significa copiar el mismo bloque 15 veces, y cada cambio en el menú se repite 15 veces. Astro permite escribirlo una vez como componente y, al compilar, lo inserta en cada página. El costo es que hace falta Node y un paso de compilación; a cambio, lo que recibe el navegador sigue siendo HTML, CSS y JS comunes.

**Sin frameworks de interfaz ni librerías de estilos.** Es un sitio de contenido, no una aplicación: casi todo es texto e imágenes que no cambian mientras el usuario navega. Sumar React o Bootstrap agregaría peso a la descarga sin resolver ningún problema real del sitio.

**Un solo layout.** Todas las páginas usan `Layout.astro`, que arma el `<head>`, el Header y el Footer. Un cambio en la navegación se hace una vez y se refleja en todo el sitio.

**Contenido separado del diseño.** Los datos que se repiten con la misma forma (carreras, autoridades, equipo, noticias) están en `datos.json` y las páginas los recorren para generar las tarjetas. Agregar una carrera es agregar un objeto al JSON, sin tocar el HTML. El contenido único de cada página queda escrito en la página misma.

**Rutas definidas por carpetas.** La ubicación de un archivo en `src/pages/` define su URL. Las noticias usan una sola plantilla, `[slug].astro`, que al compilar genera una página por cada noticia cargada en `datos.json`.

**Estilos en dos niveles.** `global.css` define la paleta, la escala tipográfica y las clases comunes (`contenedor`, `seccion`, `banda`, `grilla`, `tarjeta`, `btn`, `campo`). Cada página o componente agrega solo lo propio en su bloque `<style>`, que Astro aísla para que no afecte al resto del sitio.

**JavaScript solo donde hay interacción.** Astro no envía JavaScript salvo que se lo pida. Hay JS en los desplegables y el menú mobile del Header, los acordeones de las carreras, la validación de los formularios (Contacto, boletín y newsletter) y la aparición gradual de los bloques al hacer scroll.

**Tipografía instalada como dependencia.** Archivo se sirve desde el propio sitio (`@fontsource/archivo`) en lugar de pedirla a Google Fonts: no depende de un servidor externo y funciona sin conexión durante el desarrollo.

**Formularios validados en el navegador.** Contacto, boletín y newsletter revisan los campos con JavaScript y muestran el error o la confirmación en pantalla. Al ser un sitio estático no hay servidor que reciba los datos: el envío real queda fuera del alcance de este trabajo.

**Diseño adaptable y accesible.** Las grillas pasan a una columna en pantallas chicas y el menú se convierte en hamburguesa. El menú se puede recorrer con teclado, el foco es visible y cada campo de formulario muestra su propio mensaje de error.

## Secciones del sitio

| Sección | Ruta | Archivo |
| :--- | :--- | :--- |
| Inicio | `/` | `src/pages/index.astro` |
| Institucional · Misión y Visión | `/institucional/mision` | `src/pages/institucional/mision.astro` |
| Institucional · Autoridades | `/institucional/autoridades` | `src/pages/institucional/autoridades.astro` |
| Institucional · Equipo de trabajo | `/institucional/equipo` | `src/pages/institucional/equipo.astro` |
| Institucional · Articulación | `/institucional/articulacion` | `src/pages/institucional/articulacion.astro` |
| Institucional · Noticias | `/institucional/noticias` | `src/pages/institucional/noticias/index.astro` |
| Institucional · Artículo de noticia | `/institucional/noticias/<slug>` | `src/pages/institucional/noticias/[slug].astro` |
| Institucional · Infraestructura y Equipamiento | `/institucional/infraestructura` | `src/pages/institucional/infraestructura.astro` |
| Formación · Nuestra propuesta | `/formacion` | `src/pages/formacion/index.astro` |
| Formación · Tecnicaturas | `/formacion/tecnicaturas` | `src/pages/formacion/tecnicaturas.astro` |
| Formación · Formación Profesional | `/formacion/profesional` | `src/pages/formacion/profesional.astro` |
| Formación · Capacitaciones | `/formacion/capacitaciones` | `src/pages/formacion/capacitaciones.astro` |
| Servicios | `/servicios` | `src/pages/servicios.astro` |
| Contacto | `/contacto` | `src/pages/contacto.astro` |
| Empresas que Educan | `/empresas` | `src/pages/empresas.astro` |

## Estructura del proyecto

```text
/
├── public/                  Imágenes del sitio (se copian tal cual al compilar)
│   ├── imagenes/            Institucional: infraestructura y noticias
│   └── img/                 Inicio
├── src/
│   ├── assets/              Prototipo, brief de diseño y logos de Articulación
│   ├── components/          Piezas reutilizables
│   │   ├── Header.astro     Navegación, desplegables y menú mobile
│   │   ├── Footer.astro     Contacto, mapa del sitio, newsletter y redes
│   │   └── Carrera.astro    Tarjeta de carrera con acordeones
│   ├── data/
│   │   └── datos.json       Carreras, autoridades, equipo y noticias
│   ├── layouts/
│   │   └── Layout.astro     Base de todas las páginas: <head>, Header y Footer
│   ├── pages/               Una página por archivo; la carpeta define la URL
│   └── styles/
│       └── global.css       Variables de color, tipografía y clases compartidas
└── package.json
```

## Forma de trabajo

El desarrollo se organizó con las herramientas de GitHub:

- **Issues:** cada sección o componente se cargó como un issue, con su descripción, criterio de "listo cuando" y responsable.
- **Ramas:** una rama por issue, con el formato `feature/<número>-<nombre>`.
- **Pull requests:** cada rama se integró a `main` mediante un pull request, con la descripción de lo realizado y cómo probarlo.

---

3° año Tec. Sup. Desarrollo de Software | ITEC El Molino