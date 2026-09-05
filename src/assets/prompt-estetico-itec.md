# Prompt descriptivo — Estética esperada
## Reingeniería del Ecosistema Digital ITEC El Molino

> **Brief de diseño para generar el prototipo (documento HTML único).**
> Sirve como especificación de la identidad visual, la estructura y el comportamiento
> del sitio rediseñado. Está construido a partir de las capturas del sitio actual y de
> las mejoras propuestas por el equipo.

---

## 0. Regla de oro (no negociable)

**El contenido textual NO cambia.** Todos los textos, nombres, cargos, descripciones de
carreras, cursos, servicios, datos de contacto y logos institucionales se conservan tal cual
están en el sitio actual. Lo único que se rediseña es el **formato, la distribución, la
jerarquía visual, el color, la tipografía y las interacciones**. No inventar carreras, no
agregar noticias falsas, no cambiar redacciones: solo re-ordenar y re-vestir lo que ya existe.

---

## 0.bis Requisito técnico (no negociable): prototipo navegable con JS

El prototipo se entrega como **un único documento HTML** y debe tener **navegación
completamente funcional dentro de sí mismo**, resuelta con **JavaScript** (comportamiento tipo
SPA — *single page application*). No es una maqueta estática ni una imagen: el docente/usuario
tiene que poder **hacer clic en el menú y en los botones y moverse por todas las secciones**
sin recargar la página y sin depender de archivos externos.

**Cómo debe funcionar la navegación:**
- Todas las "páginas" del sitio (Inicio, Institucional, Formación, las tres vistas de Formación,
  Servicios, Contacto, Empresas que Educan) viven dentro del mismo HTML como **secciones/vistas**
  que JS **muestra y oculta** según la opción elegida. Una sola vista visible por vez.
- El **navbar** dispara la navegación por JS: al hacer clic en un ítem se cambia la vista activa.
  Los **desplegables** (Institucional ▾ y Formación ▾) abren y navegan a sus subsecciones también
  por JS.
- Las **tarjetas y botones internos** son navegables: p. ej. las tres cards de Formación llevan a
  su vista correspondiente ("Ver Tecnicaturas" → vista Tecnicaturas), los CTA del hero llevan a la
  sección que corresponda, "Empresas que Educan" abre su vista, etc.
- Estado de navegación visible: el ítem activo del menú se **resalta**; conviene reflejar la vista
  actual en el hash de la URL (ej. `#formacion/tecnicaturas`) para que la navegación por
  atrás/adelante del navegador y los enlaces directos funcionen.
- Interacciones internas también por JS y funcionales: **menú hamburguesa** en mobile
  (abre/cierra), **acordeones** de las tecnicaturas (Duración / Acreditación Oficial / Plan de
  Estudio se despliegan), formulario de Contacto con **validación básica** en cliente, scroll al
  tope al cambiar de vista.

**Restricciones de implementación:**
- **HTML + CSS + JavaScript vanilla**, todo autocontenido en el mismo archivo `.html` (`<style>` y
  `<script>` embebidos), sin build ni dependencias externas obligatorias, para que abra con solo
  hacer doble clic.
- **Código limpio, estructurado y comentado** (lo pide la consigna): separar claramente las
  vistas, la lógica de navegación y los componentes; comentar las funciones principales.
- El enlace roto **"La Red"** no debe quedar como enlace muerto: resolverlo como vista interna o
  removerlo del menú.

---

## 1. Concepto e intención

Rediseñar el portal del Instituto Tecnológico El Molino (Esperanza, Santa Fe) para que
transmita **prestigio educativo y tecnológico**: una institución seria, moderna y confiable,
con 25 años de trayectoria. La sensación buscada es la de un **instituto técnico
contemporáneo** —limpio, ordenado, con aire— y no la de un sitio WordPress genérico y
recargado.

La palabra rectora es **prestigio**. Eso se logra con: espacio en blanco generoso, una grilla
consistente, tipografía firme, contraste claro y microinteracciones sobrias. **Moderno e
interactivo, pero sin exageración**: nada de animaciones estridentes, carruseles innecesarios
ni efectos que distraigan. La elegancia está en la contención.

---

## 2. Paleta de color

El sitio actual ya tiene un sistema de color latente; lo formalizamos.

**Colores institucionales (base):**
- **Rojo institucional** — acento principal, tomado del logo y del edificio. Aprox. `#B01E28` / `#C1121F`. Se usa con moderación: logo, subrayados de sección, un botón primario clave, detalles.
- **Gris oscuro** — texto y estructura. Aprox. `#333333` / `#3A3A3A`.
- **Gris medio** — textos secundarios, líneas. Aprox. `#6E6E6E`.
- **Gris claro / off-white** — fondos alternos de sección. Aprox. `#F4F4F4` / `#EDEDED`.
- **Blanco** — fondo dominante, para dar aire y sensación de limpieza.

**Colores de acento por trayecto formativo** (ya existen en el sitio y se conservan como
sistema de codificación de las tres propuestas educativas):
- **Magenta / rosa fuerte** — Tecnicaturas Terciarias (`tec`). Aprox. `#E5005B`.
- **Naranja** — Formación Profesional (`prof`). Aprox. `#F39200`.
- **Turquesa** — Capacitaciones (`cap`). Aprox. `#5CC4C4`.

**Regla de uso:** el rojo y los grises mandan en toda la navegación general (home,
institucional, servicios, contacto, footer). Los tres colores de acento aparecen **solo** en
la zona de Formación y en las vistas de cada trayecto, como código visual que ayuda al usuario
a ubicarse. Así se evita el "arcoíris" disperso del sitio actual y se gana coherencia.

---

## 3. Tipografía

- **Una sola familia sans-serif moderna y legible** para todo el sitio (por ejemplo tipo
  Inter, Poppins, Montserrat o similar), con jerarquía marcada por peso y tamaño, no por
  cambiar de fuente en cada sección.
- **Escala tipográfica consistente y definida:** un tamaño para títulos de sección (H1/H2),
  otro para subtítulos (H3), otro para cuerpo, otro para etiquetas/botones. Aplicada **igual en
  todas las páginas**.
- Títulos con peso alto (bold/semibold) y buen interlineado; cuerpo con tamaño cómodo (mínimo
  16px) y line-height amplio para lectura fluida.
- Corregir la inconsistencia actual: hoy conviven mayúsculas, minúsculas, tamaños y estilos
  distintos entre páginas. **Un único sistema tipográfico** unifica todo.

---

## 4. Sistema visual y layout

- **Grilla consistente** con márgenes y espaciados parejos (sistema de spacing basado en
  múltiplos, ej. 8px). Todas las secciones respiran igual.
- **Diseño mobile-first:** pensar primero la pantalla chica. Navegación con menú hamburguesa
  en mobile; tarjetas que pasan a una columna; textos y botones táctiles cómodos.
- **Tarjetas (cards)** como componente organizador principal: se usan para carreras, cursos,
  servicios y cualquier bloque de contenido repetible. Bordes suaves, sombra sutil, hover
  discreto.
- **Botones que parezcan botones:** los CTA actuales no destacan. Definir un botón primario
  (fondo sólido rojo institucional, texto blanco) y uno secundario (contorno). Estados de
  hover/focus visibles. Bordes redondeados sutiles, buen padding.
- **Secciones alternadas** fondo blanco / gris claro para separar bloques sin necesidad de
  líneas duras, dando ritmo y ayudando a la jerarquía.
- **Accesibilidad:** contraste suficiente texto/fondo (AA), tamaños de texto legibles, foco
  visible en navegación por teclado, áreas táctiles amplias.

---

## 5. Componentes transversales

**Navbar (header):**
- Logo El Molino a la izquierda. Menú simplificado y ordenado.
- Ítems: **Inicio · Institucional ▾ · Formación ▾ · Servicios · Contacto**, más un acceso
  destacado a **Empresas que Educan**.
- **Simplificar la navegación:** el menú actual tiene demasiadas opciones sueltas. Agrupar los
  desplegables de forma clara y **quitar el enlace roto "La Red"** (o resolverlo como sección
  interna / enlace externo válido; hoy no funciona).
- Sticky sutil al hacer scroll. En mobile, hamburguesa con panel desplegable ordenado.
- Un CTA destacado en el header (ej. **"Conocé la oferta 2026"** o **"Inscripciones"**) para
  resaltar los accesos importantes: Carreras, Inscripciones y Contacto.

**Footer (rediseñado):**
- El footer actual está desprolijo y desalineado. Rehacerlo como un footer **estructurado en
  columnas**: datos de contacto, mapa del sitio / accesos rápidos, formulario de suscripción al
  Newsletter ITEC, redes sociales y logos de instituciones asociadas (RED de Centros
  Tecnológicos ADIMRA, Ministerio de Trabajo, etc.).
- Alineación pareja, jerarquía clara, fondo gris oscuro o gris claro uniforme. Que se sienta
  parte del mismo sistema y no un agregado.

**Microinteracciones (sobrias):**
- Hover suave en tarjetas y botones, transiciones cortas, aparición gradual de secciones al
  hacer scroll (fade/slide leve). Nada agresivo. Todo debe reforzar la sensación de calidad,
  no competir con el contenido.

---

## 6. Sección por sección

### 6.1 Inicio (Home)
- **Hero con un solo mensaje fuerte y un CTA claro.** Hoy el hero repite dos veces el mensaje
  institucional ("Proyectamos, crecemos, innovamos" / "25 años juntos") sin llamado a la
  acción. Unificar en **un** título potente + subtítulo breve + **un botón claro** (ej.
  *"Conocé la oferta 2026"* o *"Sobre el 25° Aniversario"*). Imagen de fondo del edificio o del
  aniversario, con overlay para asegurar contraste del texto.
- Debajo, bloque **"El Molino"** (descripción del proyecto educativo público-privado) con su
  frase *"Formando personas valiosas para la región y sus empresas"* y el botón *"Acerca del
  Instituto"*, ordenado en una grilla limpia junto a los logos de las entidades fundadoras
  (CICAE, Esperanza, etc.).
- **Dos accesos principales en tarjetas: FORMACIÓN y SERVICIOS**, cada uno con su ícono, bajada
  y botón "Nuestra propuesta". Reemplazan al bloque disperso actual.
- **Secciones de fotos (equipamiento, aula-taller, etc.):** hoy están sueltas y sin conexión.
  Integrarlas en una estructura coherente —una galería o una franja con títulos y misma
  proporción de imágenes— para que se lean como parte de un mismo relato, no como recortes
  aislados.
- Bloque de **instituciones asociadas / credenciales** (RED de Centros Tecnológicos ADIMRA y
  logos aliados) presentado como una franja prolija de logos en escala de grises uniforme.
- Cierre con el **footer rediseñado**.

### 6.2 Institucional (desplegable)
Subsecciones: **Misión y Visión · Autoridades · Equipo de trabajo**.
- **Misión y Visión** en dos columnas equilibradas, con imagen de apoyo arriba (los jóvenes),
  títulos consistentes y buen espaciado. Conservar los textos exactos.
- **Autoridades** y **Equipo de trabajo** presentados como **listas prolijas o tarjetas** en
  dos columnas, con nombre, cargo y entidad. Tipografía uniforme, alineación pareja. Conservar
  todos los nombres y cargos tal cual.

### 6.3 Formación (desplegable) — corazón del sitio
- Página de entrada con **tres tarjetas** grandes y parejas, una por trayecto, usando los
  colores de acento: **Tecnicaturas (magenta) · Formación Profesional (naranja) ·
  Capacitaciones (turquesa)**. Cada tarjeta: logo del trayecto (`tec` / `prof` / `cap`),
  bajada breve (texto actual) y **botón claro** ("Ver Tecnicaturas", "Ver Cursos", "Ver
  Capacitaciones"). Misma altura, mismo estilo, alineación perfecta.

**Vista Tecnicaturas Terciarias:**
- Header con banda magenta y título + bajada (texto actual: "conectan la educación y el
  trabajo…", "formación práctica en espacios aula-taller").
- Cada carrera (Gestión Industrial, Mantenimiento Industrial, etc.) como **bloque/acordeón**
  con su descripción y tres desplegables consistentes: **Duración · Acreditación Oficial ·
  Plan de Estudio**. Mantener el patrón de acordeón, pero prolijo, con íconos "+" claros y
  animación suave. Conservar todos los textos.

**Vista Formación Profesional:**
- Header con banda naranja, título y bajada (texto actual sobre "formación basada en
  competencias").
- Franja de logos organizada en tres grupos rotulados: **Impulsados por · Organizan ·
  Colaboran** (Ministerio de Trabajo, ADIMRA, IAEA, RED, Esperanza, etc.), alineados y en
  escala de grises uniforme.
- Dos accesos en tarjetas: **Trayectos Formativos** y **Cursos Vigentes**, con su bajada y
  enlace ("Conocé nuestros trayectos formativos" / "Ver cursos").
- Sello de certificación (IRAM – MTEYSS) prolijo al pie.

**Vista Capacitaciones:**
- Header con banda turquesa, título y bajada (texto actual).
- Mismo patrón que Formación Profesional: dos accesos en tarjetas —**Trayectos Formativos** y
  **Capacitaciones Vigentes**— y bloque de suscripción al **Boletín informativo ITEC**.
- La estructura visual debe ser **idéntica** a la de las otras dos vistas para dar uniformidad.

### 6.4 Servicios
- Hoy es solo texto plano. Reorganizar en **tarjetas con ícono** manteniendo el contenido:
  **Servicios Tecnológicos** (ensayos destructivos, no destructivos, metalográficos, soldadura)
  y **UVT** (Unidad de Vinculación Tecnológica). Íconos consistentes, bajadas ordenadas, misma
  grilla que el resto del sitio. Conservar todos los textos y listados.

### 6.5 Contacto
- Hoy el formulario está mal ubicado con el mapa como header. Rediseñar en **dos columnas
  equilibradas**: a la izquierda, datos de contacto (dirección Rivadavia 1390, email, teléfono,
  WhatsApp) y el mapa; a la derecha, el **formulario prolijo** (Nombre, Email, Asunto, Mensaje +
  botón Enviar). Campos con buen tamaño, labels claras, botón primario destacado. El mapa como
  bloque integrado, no como banda superior aislada.

### 6.6 Empresas que Educan
- Página/sección propia con la descripción del programa (texto actual) y el **diagrama
  circular** (El Molino → Empleados → Empresas → intercambio y formación). Mantener el contenido
  e integrarlo al mismo sistema visual (misma tipografía, mismos márgenes, mismo footer). Que
  deje de verse como una página "aparte" con estilo distinto.

---

## 7. Checklist de mejoras a evidenciar (mapea las notas del equipo)

- [x] **Jerarquía clara:** hero con un único mensaje + un CTA (no repetir el mensaje dos veces).
- [x] **Estructura conectada** para las secciones de fotos (equipamiento, aula-taller): grilla/galería coherente.
- [x] **Tipografía consistente** (títulos/subtítulos/cuerpo) y **espaciados parejos** en todo el sitio.
- [x] **Botones que se distinguen** como botones, con estados visibles.
- [x] **Navegación simplificada:** menos opciones sueltas, desplegables ordenados, **enlace roto "La Red" resuelto**.
- [x] **Uniformidad:** todas las secciones comparten la misma estructura visual y sistema de tarjetas.
- [x] **Accesibilidad:** contraste, tamaños de texto legibles, foco visible, navegación mobile.
- [x] **Diseño mobile-first** en toda la propuesta.
- [x] **Cards** para carreras, cursos, servicios y noticias; accesos destacados a **Carreras, Inscripciones y Contacto**.
- [x] **Footer rediseñado** y prolijo.
- [x] **Contenido intacto:** solo cambian formato, distribución y color.

---

## 8. Resumen en una línea (para pegar como prompt)

> *Rediseñá el portal del Instituto Tecnológico El Molino como un sitio moderno, limpio y de
> aire prestigioso (educación + tecnología), respetando el contenido textual exacto y cambiando
> solo formato, distribución y color. Paleta: rojo institucional + grises como base, y magenta,
> naranja y turquesa como códigos de los tres trayectos de Formación. Una sola tipografía
> sans-serif con jerarquía consistente, grilla y espaciados parejos, diseño mobile-first,
> componentes en tarjetas, botones claros y destacados, hero con un único mensaje y un CTA
> ("Conocé la oferta 2026"), navegación simplificada sin enlaces rotos, y footer reestructurado.
> Microinteracciones sobrias. Estructura: Inicio, Institucional (Misión y Visión, Autoridades,
> Equipo), Formación (Tecnicaturas, Formación Profesional, Capacitaciones), Servicios, Contacto y
> Empresas que Educan, todas con el mismo sistema visual. Entregá todo en **un único archivo HTML
> autocontenido (HTML + CSS + JS vanilla, comentado)** con **navegación completamente funcional
> tipo SPA**: el menú, los desplegables, las tarjetas y los botones muestran/ocultan vistas con
> JavaScript sin recargar, con ítem activo resaltado, menú hamburguesa en mobile, acordeones de
> tecnicaturas y validación básica del formulario de contacto, y sin enlaces rotos.*
