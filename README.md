# 🎨 Let's Paint

**→ Juguemos: [guia-ai.github.io/lets-paint](https://guia-ai.github.io/lets-paint/)**

Tres editores de dibujo hechos a mano, en HTML/`<canvas>` puro. **Sin instalar nada, sin dependencias.** Corren en tu navegador — y andan hasta sin internet.

Un experimento de **Let's See Lab**, el laboratorio de [GUIA](https://guia-ai.com.ar): levantamos cosas open source y las facilitamos.

**Creado por [Andu Truel — GUIA](https://guia-ai.com.ar)** · Libre y abierto (MIT), para todos. Si te gustó: 💛 [apoyá el proyecto](https://cafecito.app/anduguia) para que siga creciendo, o contale a alguien.

> 📐 La **visión del proyecto**, las tres líneas y —sobre todo— la dirección de funcionalidad del Atelier (los **paneles sueltos / escritorio organizable**) están documentadas en **[`VISION.md`](VISION.md)**.

## Cómo abrir

- **Doble clic en `index.html`** → lanzador para elegir versión.
- O abrí directo cualquiera de las dos:
  - `clasico.html` — Paint Clásico
  - `moderno.html` — PaintCraft (editor de bloques, homenaje de fans)

Funciona en cualquier navegador (Chrome, Safari, Firefox, Edge).

## Contenido

| Archivo | Qué es |
|---|---|
| `index.html` | Lanzador: elegís la versión |
| `clasico.html` | **Paint Clásico** — réplica fiel del Paint de Windows |
| `moderno.html` | **PaintCraft** — editor de bloques, homenaje de fans a Minecraft (voxel / pixel-art) |
| `atelier.html` | **Paint Atelier** — acuarela de ensueño (dibujo, de simple a pro) |

> Todas las versiones tienen un botón **⌂ Inicio** para volver al lanzador, y un **💬 Contame** para pedir otro Paint, sugerir mejoras o avisar errores (llega directo por correo).

---

### Paint Clásico (`clasico.html`)
Réplica del Paint de Windows XP/7.
- 16 herramientas: lápiz, pincel (4 formas), borrador, balde, cuentagotas, lupa, texto, línea, curva Bézier, rectángulo, polígono, rect. redondeado, elipse, selección libre y rectangular.
- Menús completos: Archivo, Edición, Ver, Imagen, Colores, Ayuda.
- Texto con barra de Fuentes (fuente, tamaño, N/K/S, fondo opaco/transparente).
- Selección: mover, cortar, copiar, pegar, **insertar imagen** como capa flotante.
- Imagen: voltear, rotar, estirar/sesgar, invertir, redimensionar lienzo.
- Deshacer/rehacer, guardar PNG/JPG, imprimir. Atajos de teclado estándar.
- 🥚 Se dice que guarda **tres secretos de época**… y que ni mirando el código los vas a encontrar.

### PaintCraft (`moderno.html`)
Editor de **bloques** — **homenaje de fans a Minecraft**, gratis. Pixel-art / voxel.
> Proyecto de fans. No oficial, sin relación ni aprobación de Mojang/Microsoft. Texturas 100% propias (procedurales); no usa assets de Mojang.
- Construís con **bloques** sobre una grilla (modo creativo).
- **20 materiales** con textura procedural y **nombres como en Minecraft**: Bloque de césped, Tierra, Piedra, Roca, Tablones de roble, Arena, Ladrillos, Hojas de roble, Bloque de diamante, Bloque de oro, Bloque de hierro, Bloque de redstone, Lava, Agua, Vidrio, Obsidiana, Piedra luminosa, Bloque de nieve, **TNT**, Bloque de netherita.
- **Tamaño de cubo** (1×–4×): un **3× es un bloque grande**, no varios chicos. Va junto al **tamaño de grilla** (resolución de píxel).
- **Fondo** manipulable (día/atardecer/noche/liso/transparente).
- **Hotbar** de inventario (teclas 1-9) + inventario completo (🎒).
- Herramientas: colocar, romper, llenar, tomar material, línea, rectángulo, **mechero 🔥**.
- 🔥💥 *Easter egg*: el **mechero** quema de a un bloque al arrastrar… pero si el fuego toca una **TNT**, ésta **se enciende** (vibra, crece y parpadea) y explota en 6×6 — con reacción en cadena **en ondas**. A veces te ayuda, a veces te vuela el trabajo.
- 🥚 Hay un **secreto escondido** que desbloquea algo que no está en ningún menú. Los que jugaron Minecraft tienen ventaja…
- 🎨 *Gesto inteligente* (en los tres editores): tocá un color/material con cualquier herramienta que no pinte y volvés solo a tu última herramienta de dibujo.
- Bloques **emisivos con glow** (lava, diamante, oro, piedra luminosa), agua translúcida, vidrio.
- **🔗 Compartir por link:** tu obra viaja codificada en la URL — quien abra el link la ve reconstruida. Sin servidor, sin cuentas.
- Deshacer/rehacer, exportar PNG, vaciar. **Gratis.**

### Paint Atelier (`atelier.html`)
Editor de dibujo suave y premium, centrado en la **acuarela**. Arranca simple (hobby) y puede crecer hacia algo más pro.
- **Pincel de acuarela** que se funde y construye color en capas (la firma de esta versión).
- Tinta (línea limpia), **difuminar**, goma suave, aguada/relleno, cuentagotas.
- Paleta de ensueño con nombres (Cielo, Pradera, Atardecer, Lavanda…) + color a medida.
- UI de **vidrio esmerilado** (glassmorphism), cielo con nubes y motas de luz, cursor de pincel en vivo.
- Tamaño y flujo del pincel, deshacer/rehacer, exportar PNG sobre papel crema.

---

*Hecho con Claude Code.*
