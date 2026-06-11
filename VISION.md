# 🎨 Paint — Visión, líneas y funcionalidades

Documento vivo del proyecto. Acá queda registrado **el por qué** de cada versión y, sobre todo, **la dirección de funcionalidad** que Andu pidió para el Atelier (la parte de los paneles sueltos / escritorio organizable). Si volvés a esto en seis meses, este archivo te devuelve el contexto.

---

## Las tres líneas

El proyecto no es "un Paint": son **tres lecturas distintas** de qué puede ser Paint. Cada una se valida con su propio criterio.

### 1. Clásico (`clasico.html`) — *fidelidad*
Réplica del Paint de Windows XP/7. El criterio acá es **idéntico al original**: nada de reinterpretar, todo como era. 16 herramientas, menús completos, texto, selección, insertar imagen, operaciones de Imagen.

### 2. PaintCraft (`moderno.html`) — *juego* · **homenaje de fans a Minecraft**, gratis
Editor de **bloques** matérico y divertido. Se construye con materiales (TNT, diamante, redstone, lava, obsidiana, netherita…), tamaño de cubo (un 3× = un bloque grande) **junto al** tamaño de grilla, y fondo manipulable. Easter egg: **mechero 🔥** que prende la TNT → explosión 6×6 con reacción en cadena.

> **Legal (fan project):** según las [Usage Guidelines de Mojang](https://www.minecraft.net/en-us/usage-guidelines), el contenido de fans está permitido si: (a) "Minecraft" va solo como título/descripción **secundaria** (PaintCraft es nombre propio → ok), (b) hay un **disclaimer prominente** de no-afiliación (lo tiene), (c) **no se usan sus assets** reales (las texturas son 100% propias/procedurales), (d) es **gratis**. "TNT" es término genérico. → PaintCraft es **gratis siempre**.

### 3. Atelier (`atelier.html`) — *ensueño*
Editor de **dibujo** suave y premium, centrado en la **acuarela** (pincel que se funde y construye color en capas). La **hoja** (papel crema con textura y sombra) es el corazón y no se toca.

> **Nota de marca:** el norte estético del Atelier lo charlamos con referencias a estudios/marcas conocidas. Eso fue **lenguaje de la conversación, NO copy del producto** — no va en pantalla. En el producto se habla de "acuarela de ensueño", "dibujá a tu ritmo", etc.

---

## 🧭 Filosofía del producto (norte mayor)

1. **Núcleo compartido + personalidad como máscara.** Todos los editores comparten un **motor versátil**: en cualquiera podés crear de verdad. La temática es **presentación + un gesto propio**, no una jaula. Cada uno "sabe hacer" algo particular por su tema (bloques en Cubitos, acuarela en Atelier), pero **nunca se pierde la versatilidad**.
2. **Cada editor con su Easter egg propio**, atado a su personalidad (enmascaramiento, no funcionalidad de fondo).
3. **Atelier por niveles (de hobby a pro).** Arranca **simple, estilo Paint**. Quien quiera, **habilita "pro"**: **capas, más formas, unir vectores**, etc. Crece con el usuario — **siempre desde el dibujo y siempre simple de base**. Nunca se vuelve un monstruo: el usuario decide cuánto destrabar (revelado progresivo).
4. **Lo conversacional no llega al producto.** Referencias, chistes internos y andamiaje de la charla se quedan acá (en docs), no en la pantalla.
5. **Gesto inteligente de color (los tres editores):** si tocás un color/material mientras tenés una herramienta que no pinta (goma, mechero, cuentagotas, selección, lupa…), el sistema entiende que querés pintar y **cambia solo a la última herramienta de color que usaste**. Nació de una fricción real de Andu (quería poner TNT con el mechero en la mano y "no andaba"); si le pasó a él, le pasa a la gente. En el Clásico además es fiel: el Paint real volvía a la herramienta anterior tras el cuentagotas.
6. **El mechero de PaintCraft (easter egg con riesgo):** arrastrás y **quema de a un bloque** (goma fina de fuego); pero si el fuego toca una **TNT** → explota 6×6 con cadena. "A veces te ayuda, a veces te vuela el trabajo" — es a propósito: el riesgo es parte del juego.

---

## ⭐ Dirección de funcionalidad del Atelier — "escritorio organizable"

> Lo que disparó esto (palabras de Andu, resumidas):
> *"La hoja está re bien lograda. Pero todas las otras cositas, ¿por qué tienen que vivir en un recuadro? ¿Por qué no las dejamos sueltas, medio 3D, medio agarrables, como si pudieras agarrarlas? El recuadro totalmente transparente, que sea un área de clickeado. Cuando hagas hover, que se pinte un poquito de blanco transparente esa área. Que los botones sean flotadores, como un escritorio que yo puedo organizar. Ir un poco más allá en la funcionalidad."*

### Principios (esto es lo importante de conservar)

> **Evolución:** primero probamos "paneles sueltos flotando como un escritorio que arrastrás y se acomoda solo" (transparentes, con velo blanco al hover, draggables y persistentes). Funcionó, pero la dirección final que pidió Andu fue **consolidar todo a la izquierda** y reusar la lógica del Paint clásico (opciones que cambian según la herramienta). Lo de abajo es el estado actual; el experimento flotante quedó como aprendizaje.

1. **Todo a la izquierda, en una columna.** Tools + detalles + paleta + acciones viven juntos en una barra izquierda transparente. La **hoja** (papel) queda fija y centrada — no se toca, es lo más logrado.
2. **Teclas transparentes; blanco fuerte solo al apretar/seleccionar.** Las herramientas son íconos sin caja. La **seleccionada** (o la que se está apretando) se vuelve una **tecla blanco fuerte** con relieve; el resto, transparentes. Nunca color/rojo para marcar selección.
3. **Se sienten como teclado físico.** Keycaps redondeados que **se hunden al apretar** (`:active` → `translateY`), como un teclado mecánico moderno.
4. **Los detalles aparecen según lo seleccionado** (lógica tipo Paint clásico). Un contenedor `#details` se reconstruye por herramienta: pincel/tinta/goma → Tamaño + Flujo; aguada → Intensidad; cuentagotas → ayuda. La **paleta se muestra solo** para herramientas que usan color (se oculta en goma, difuminar, cuentagotas).

### Cómo está implementado (para quien lo edite)

- Layout: `<aside class="leftbar">` fija a la izquierda con `.keys` (grid 2 col), `#details` (contextual), `.palette-card`, `.acts`. La hoja se corre con `padding-left` en `.work`.
- Teclas: `.tool` es `background:transparent`; `.tool:active` y `.tool.on` aplican el blanco fuerte + relieve + hundido.
- Contextual: `renderDetails()` lee `TOOL_INFO[state.tool]` y arma los controles (re-bindeando los sliders a `state.size`/`state.flow`). Se llama en `selectTool` y al iniciar. Es el equivalente del `buildOptions()` del Clásico.
- **Aguada (gotita):** el balde **reemplaza** con el color elegido (no acumula) → nunca sale gris/turbio, aunque rellenes varias veces.

### Ajuste final (lo que quedó)

- **Se mantiene la columna izquierda** (a Andu le gusta). **Nada de bloque a la derecha.**
- Botones **más transparentes / ghost**: las teclas casi no se ven hasta el hover; la seleccionada es un blanco apenas insinuado (sutil, sin relieve pesado); las acciones son pastillas translúcidas.
- **Ayuda al hover:** pasar el mouse por cualquier herramienta (y por Deshacer/Rehacer) muestra un tooltip con **qué es, para qué sirve y cómo usarla** (mapa `HELP`).
- **Ítems individuales y movibles:** las **6 herramientas + Deshacer + Rehacer** se arrastran de a uno (`makeDraggable`, distingue clic de arrastre con umbral de 5px), y la posición se recuerda (`localStorage atelier-pos-v2`).
- **Reordenar** (abajo a la izquierda) vuelve todo a la posición inicial **y es reversible**: el botón pasa a "↩ Deshacer" para restaurar tu armado.
- **Re-acople individual:** si arrastrás un ítem y lo soltás de vuelta **sobre la columna izquierda** (centro x < 184px), se vuelve a meter en su ranura (deja de flotar). Así no queda "pegado arriba de los otros".
- La etiqueta de la acuarela es **"Carga"** (antes "Flujo").

### Hacia dónde puede seguir (ideas abiertas)

- **Snap a bordes / imán** entre paneles al soltarlos cerca.
- **Minimizar/colapsar** un grupo a una bolita arrastrable.
- **Capas** reales en el lienzo (la acuarela lo pide).
- **Más pinceles**: tiza, óleo, lápiz graso, espátula.
- **Mojado real** (water-flow) para que la acuarela se siga corriendo unos segundos.
- Llevar la misma filosofía de "controles sueltos" a las otras dos versiones, si gusta.

---

## Decisiones registradas

- **Empaquetado:** `index.html` es el **lanzador**; cada versión vive en su archivo y tiene botón **⌂ Inicio** para volver. Todo offline, sin dependencias, en `<canvas>` puro.
- **Texto del Clásico:** se dibuja **WYSIWYG** (lo que ves en el cuadro es lo que queda); la tipografía vive en una **barra de Fuentes** flotante (no encajada en la columna).
- **Atelier — la hoja:** el papel es un fondo CSS detrás de un canvas transparente; la goma borra al papel (no a un blanco plano) y el export compone papel + obra.
- **Modelo:** **PaintCraft** y **Paint Clásico** son **gratis** (fan / homenaje). El único que monetiza es el **Atelier** (100% original). Hosting estático = ~gratis; el costo real es dominio + tiempo.
- **Plan de monetización del Atelier (decidido: arrancar YA, sin esperar):**
  - **Fase 0 (ahora):** deploy a GitHub Pages + botón **☕ Apoyá el Atelier** (constante `SUPPORT_URL` en atelier.html, oculto hasta tener link). Canales: **Cafecito.app** (MercadoPago, público AR) + **Ko-fi** (internacional, USD, membresía ~1 USD/mes). Las cuentas las crea Andu (5 min); Claude no puede crear cuentas.
  - **Fase 1:** construir **Atelier Pro** por niveles (capas → formas → vectores). Gratis lo base; Pro se desbloquea con **clave de apoyo** que entrega Cafecito/Ko-fi al apoyar (gate de honor en localStorage — en un sitio estático el código es público, así que el candado es simbólico; estándar indie para fan-pricing).
  - **Fase 2 (si tracciona):** subdominio `paint.guia-ai.com.ar`, checkout con licencias reales (Lemon Squeezy / Gumroad, sin backend propio).
  - **Framing:** "early supporter" — apoyás hoy, el Pro te llega primero. No se cobra por features que aún no existen.
- **Pendientes de Andu (3 pasos, ~10 min):** (1) `gh auth login` en la terminal → Claude hace el deploy; (2) crear Cafecito y/o Ko-fi → pegar link en `SUPPORT_URL`; (3) compartir el formulario de Notion → pegar link en `FORM_URL`.
- **Compartir sin servidor (PaintCraft):** la obra se serializa (grilla, fondo, bloques-origen) a base64url en el **hash de la URL** (`#a=…`). Quien abre el link la ve reconstruida (`loadFromHash()` al iniciar). Cero backend → cero costo. Mismo patrón aplicable al Atelier/Clásico si se quiere.
- **Canal de feedback (los 4: lanzador + 3 editores):** botón **💬 Contame** con formulario (tipo: *quiero otro Paint / mejora / error / me encantó* + mensaje + nombre opcional). Envío por **mailto a andutruel@guia-ai.com** con asunto `[Paint · <app>]` → **todo le llega a Andu directo al mail**, sin servidor ni costo. El lanzador además tiene la sección destacada *"¿Qué otro Paint te gustaría que exista?"*.
- **Feedback → SOLO Notion (decisión de Andu: nada de mail).** Se eliminó todo `mailto`. La base **💬 Feedback Paint** vive en el hub GUIA (Mensaje / App / Tipo / Nombre / **Código** / Estado / Fecha; Tipo incluye **🏆 Easter egg**) con vista Formulario creada. **ÚNICO paso pendiente de Andu:** abrir la vista "Contame (form)" → revisar/añadir preguntas (App, Tipo, Nombre, Código) → **Compartir formulario** → copiar el link → pegarlo en la constante `FORM_URL` de los 4 HTML (o pasárselo a Claude). Hasta entonces, los botones 💬 muestran "el registro abre pronto".
- **🥚 La Cacería (estilo Halliday / Ready Player One):** hay **4 secretos** repartidos en los Paints (3 en el Clásico, 1 en PaintCraft).
  - **Los secretos NO están en este repo.** Los gatillos por entrada se verifican contra **hashes SHA-256** (el fuente guarda la *huella*, no el secreto) y los **códigos de hallazgo** de 6 caracteres se derivan del propio secreto al descubrirlo — tampoco están escritos. (Límite honesto: los eggs *de acción* tienen su mecánica legible en el código para quien lo estudie a fondo; los de palabra/secuencia son 100% ciegos.)
  - **Registro:** el jugador descubre → recibe su código (se copia solo al portapapeles) → "Registrar hallazgo 🏆" abre el formulario → cae en la base de Notion con Tipo=🏆.
  - **La lista completa de secretos, gatillos y códigos de validación vive en Notion: página privada "🥚 Diario de secretos — Paint" (hub GUIA). NO publicar ese contenido acá: este archivo viaja en el repo público.**
  - **Contador compartido:** `localStorage paint-eggs-v1` cruza los tres Paints — badge 🥚 n/4 en Clásico (statusbar), PaintCraft (abajo-izq.) y lanzador ("Cacería de secretos").
  - **Salón de la Fama:** vista "🏆 Salón de la Fama" ya creada en la base (filtra Tipo=🏆, ordena por Fecha). Para hacerla pública: abrir la vista → Compartir → Publicar en la web; pegar el link en `HALL_URL` (index.html) y aparece "Ver el Salón de la Fama →" en el lanzador.
  - **El premio (diseño win-win, escalable y desafiante):**
    1. **Todos ganan algo, automático y $0:** al completar 4/4 se desbloquea el **Bloque del Cazador** (dorado, con glow) en el inventario de PaintCraft + badge pasa a 🏆. (Próximos: pincel dorado en Atelier, color secreto en Clásico.)
    2. **Todos ganan reconocimiento:** nombre en el **Salón de la Fama** público, ordenado por fecha (los primeros cazadores, arriba para siempre).
    3. **El gran premio escala por temporadas:** completar la cacería da **voz y voto para el próximo Paint** — los cazadores proponen ideas; cada temporada se construye LA ganadora, con crédito al proponente ("Paint sugerido por X"). Una build por temporada sin importar cuántos completen → sostenible. Y el Paint nuevo lo disfruta toda la comunidad (el premio beneficia a todos) **y trae eggs nuevos** → nueva temporada → flywheel.
    4. **Desafiante pero ganable:** los secretos por entrada son invisibles aun leyendo el código; si la gente se traba, se publican **pistas progresivas** (en el lanzador o redes) hasta que todos puedan llegar.
- La marca de la casa (teclas móviles/gotitas) queda para los editores originales; el Clásico guiña en su propio idioma de época.

## 🏁 La Carrera de Paints (diseño aprobado, a construir en el deploy)

La gamificación de "proponé el próximo Paint", pedida por Andu: *"que se vea como una carrera, que la gente le ponga una fotito/avatar, que se pueda votar, y el que gana es el que hacemos"*.

- **Proponer:** quien completa la cacería (o apoya) propone su Paint soñado vía formulario: nombre de la idea, descripción con sus palabras, **avatar/fotito** (elegible o subida).
- **La pista:** una página/vista pública tipo **carrera** — cada propuesta es un corredor con su avatar, avanzando según votos. Se tiene que *sentir* carrera: posiciones, distancia, sprint final de temporada.
- **Votar:** simple y sin fricción (formulario o reacciones; el conteo lo hace el agente semanal — sin backend).
- **El final:** al cierre de temporada, la propuesta ganadora **se construye**, con crédito eterno al proponente ("Paint sugerido por X") y su avatar en el Salón de la Fama.
- **Implementación $0:** base Notion "🏁 Carrera de Paints" (Propuesta / Avatar / Proponente / Votos / Temporada) + vista pública gallery; el agente semanal valida y cuenta. Evolución posible: GitHub Discussions (votos 👍 nativos y avatares automáticos) cuando la comunidad sea más técnica.

## 🪪 Atribución y voz (decisión de Andu)

- **"Es para todos, pero no quiero quedar invisibilizada":** licencia MIT con copyright **"© Andu Truel — GUIA"** (legalmente debe conservarse en toda copia) + crédito visible en lanzador (footer con link a guia-ai.com.ar), Acerca de del Clásico y README. Los forks pueden quitar el crédito visible (la cultura open source lo conserva), pero el LICENSE no.
- **El copy de apoyo NO es "invitame un cafecito":** es **"Apoyá este proyecto / apoyá para seguir creando — sé parte"**. El que apoya es parte, no propina.

## 📣 Comunidades (investigación inicial, 11/06/2026)

Dónde vive el público natural del proyecto (mix de búsqueda + conocimiento general, a validar al lanzar):
- **Lanzamiento:** Reddit (r/InternetIsBeautiful, r/SideProject, r/WebGames, r/PixelArt para PaintCraft), Show HN (Hacker News), Product Hunt, itch.io (como herramienta gratuita).
- **Comunidades de dibujo/pixel art:** Pixiv, Doodle Addicts, comunidades de Aseprite/pixel art en Discord; plataformas colaborativas como Magma/Drawpile muestran que hay audiencia activa de "dibujar en el navegador".
- **Regla manos-libres:** Claude prepara los borradores de posts (por comunidad, en su tono); **Andu publica** (las comunidades penalizan cuentas-bot y la voz tiene que ser suya). Una sola pasada de lanzamiento; después, el producto se difunde solo (share-link + cacería).
- Claude **no puede hacer llamadas** ni outreach directo en nombre de Andu; sí puede investigar comunidades específicas, preparar mensajes y armar la lista priorizada.

*Mantener este archivo al día cuando cambie la dirección. — Proyecto Paint.*
