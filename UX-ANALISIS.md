# 🔬 Análisis UX del proyecto Paint
*Auditoría con soporte teórico, práctico y criterio de design thinking. Junio 2026.*

---

## 1. Marco teórico (el "por qué" detrás de cada hallazgo)

**Las 10 heurísticas de Nielsen** ([NN/g, 1994](https://www.nngroup.com/articles/ten-usability-heuristics/)) — los 10 principios contra los que se audita una interfaz. Las que más pesan acá:
- **H1 Visibilidad del estado**: el sistema siempre cuenta qué está pasando.
- **H2 Coincidencia con el mundo real**: hablar el idioma del usuario, no del sistema.
- **H6 Reconocer antes que recordar**: que las opciones se vean, no que haya que memorizarlas.
- **H8 Diseño estético y minimalista**: cada elemento extra compite con los importantes.
- **H10 Ayuda y documentación**: disponible, pero sin estorbar.

**Progressive disclosure** ([Nielsen, 1995](https://lollypop.design/blog/2025/may/progressive-disclosure/)): mostrar primero lo crucial y revelar lo avanzado **a pedido**. Es LA herramienta para la pregunta de Andu: *"¿qué se puede ocultar atrás de un ícono?"* — respuesta teórica: todo lo que no sea parte de la tarea principal (dibujar).

**Señalizadores de Norman** (signifiers): una capacidad que no se *señaliza* no existe para el usuario. Si las gotitas se pueden mover pero nada lo insinúa, para el 99% de la gente esa magia no existe.

**Design thinking** (empatizar → definir → idear → prototipar → testear): el criterio rector es **la tarea del usuario** (dibujar/jugar/compartir), no nuestras features. Y la regla de oro de Nielsen: **probar con 5 usuarios reales** encuentra ~85% de los problemas.

## 2. Personas (¿para quién es cada Paint?)

| Persona | Llega buscando | Su éxito es | Su riesgo es |
|---|---|---|---|
| 🧒 **El nostálgico** (25-45) | el Paint de su infancia | dibujar algo feo y reírse en 30 segundos | que algo NO sea como lo recuerda |
| ⛏️ **El fan de Minecraft** (8-20) | jugar/construir | volar una TNT y compartir su mundo | aburrirse antes de descubrir el mechero |
| 🎨 **La dibujante hobby** (15-50) | un lugar lindo para pintar | una acuarela que la sorprenda a ella misma | sentirse torpe con las herramientas |

## 3. Auditoría práctica (hallazgo → heurística → propuesta)

### 🌍 Transversal (lo más importante del informe)
| # | Hallazgo | Teoría | Propuesta | Impacto/Esfuerzo |
|---|---|---|---|---|
| T1 | **Al compartir el link en WhatsApp/redes no aparece NINGUNA preview** (sin meta tags Open Graph, sin favicon) | H1 — el primer "estado" del producto ocurre fuera del producto | Meta tags OG + favicon + imagen de preview por editor. **Es la mejora nº1 de transmisión**: cada link compartido se vuelve un cartel | 🔥 Alto / Bajo |
| T2 | Nada explica **qué es esto** en los primeros 5 segundos (el lanzador asume contexto) | H2 | Subtítulo emocional: "El Paint de tu infancia, el de bloques y uno para pintar de verdad. Gratis, sin registro, en tu navegador" | Alto / Bajo |
| T3 | **Móvil/tablet**: los layouts no están pensados para touch (pointer events ya funcionan, el layout no acompaña) | — | Fase propia: layout responsive + botones táctiles. Es proyecto grande, no parche | Alto / Alto |
| T4 | Accesibilidad: faltan `aria-label` en botones-ícono, foco visible de teclado | H4 consistencia | Pasada de aria-labels + focus rings | Medio / Bajo |

### 🚪 Lanzador
| # | Hallazgo | Teoría | Propuesta |
|---|---|---|---|
| L1 | Las tarjetas **cuentan** los editores pero no los **muestran** (las previews son maquetas estáticas) | "Show, don't tell" | Mini-GIF o canvas animado en cada tarjeta (el Atelier pintándose solo, una TNT explotando) |
| L2 | La cacería aparece como texto chico — es de lo más diferencial y casi no se ve | H8 jerarquía | Darle entidad visual propia: huevo grande, contador, link al Salón |

### 🖼️ Paint Clásico
| # | Hallazgo | Teoría | Propuesta |
|---|---|---|---|
| C1 | El botón "💬 Contame" en la barra de menú **rompe la época** (un emoji en Windows XP) | Consistencia interna de la máscara | Moverlo adentro del menú Ayuda, estilo de texto plano de la época. La fidelidad ES la UX de este editor |
| C2 | Nada más que tocar: su métrica es "idéntico al original" y la cumple | — | No tocar. *(Decisión consciente, no omisión)* |

### ⛏️ PaintCraft
| # | Hallazgo | Teoría | Propuesta |
|---|---|---|---|
| P1 | El **disclaimer legal ocupa el header** — necesario pero ruidoso | H8 + progressive disclosure | **Ocultarlo atrás de un ícono ⓘ** (modal "Acerca de"). Cumple legal y limpia la cabecera — el ejemplo perfecto de lo que pedía Andu |
| P2 | Botones de acción con texto largo (EXPORTAR / COMPARTIR / VACIAR) | H6 vs H8 en tensión | Ícono + palabra corta. *No* solo-ícono: reconocer > recordar |
| P3 | Etiquetas de grilla "XL/L/M/S/XS" no dicen qué cambia | H2 mapping | Tooltip "XL = bloques grandes (24 de ancho)" o mini-preview al hover |
| P4 | El mechero y el portal no se señalizan | ¡Intencional! | Mantener: son secretos de la cacería. La falta de señalizador acá es **diseño de juego**, no error |

### 🎨 Atelier
| # | Hallazgo | Teoría | Propuesta |
|---|---|---|---|
| A1 | **Las gotitas movibles no tienen señalizador** — la feature más encantadora es invisible | Norman: sin signifier no existe | Micro-hint la primera visita: *"psst… todo lo que ves se puede agarrar y mover 💧"* (toast que aparece una vez y nunca más) |
| A2 | Lienzo vacío mudo: la dibujante hobby duda ("¿toco acá?") | Empty state | Marca de agua suave *"tocá y arrastrá para pintar"* que se desvanece con el primer trazo |
| A3 | Atajos de teclado (B/I/S/E/F/P, 1-9, [ ]) **completamente invisibles** | H6 + H10 | **Ocultar atrás de un ícono "?"**: cheatsheet flotante con todos los atajos. Segundo ejemplo perfecto de "esconder tras ícono" |
| A4 | Íconos emoji (🖌️✒️👆) desentonan con la estética sedosa de vidrio | Consistencia estética | Set propio de íconos SVG monocromos finos (fase 2 — es polish, no urgencia) |
| A5 | El botón 💛 aparece sin contexto | H2 | Tooltip ya dice "sé parte" ✓; al hacer clic, podría mostrar 1 línea de por qué antes de ir a Cafecito |

## 4. Qué NO se está transmitiendo (y vale oro)

1. **"Gratis, sin registro, sin instalar"** — el superpoder del proyecto, no está dicho en ningún lado visible.
2. **"Hecho con amor por una persona real"** — el crédito existe, la *historia* no se siente (→ por eso HISTORIA.md también es una pieza UX).
3. **"Hay secretos escondidos"** — la promesa más viral está en letra chica.
4. **"Tu obra viaja en un link"** — compartir-sin-cuentas es mágico y nadie lo anuncia.

## 5. Plan priorizado (impacto × esfuerzo)

```
AHORA (alto impacto, bajo esfuerzo)          DESPUÉS (alto/alto)
┌────────────────────────────────────┐      ┌──────────────────────────┐
│ 1. OG metas + favicon (T1)         │      │ 7. Layout móvil/touch    │
│ 2. Hint gotitas 1ª visita (A1)     │      │ 8. Set de íconos SVG     │
│ 3. Empty state Atelier (A2)        │      │ 9. GIFs en lanzador      │
│ 4. ⓘ disclaimer PaintCraft (P1)    │      │ 10. i18n (EN)            │
│ 5. "?" cheatsheet atajos (A3)      │      └──────────────────────────┘
│ 6. Subtítulo emocional + cacería   │
│    con jerarquía en lanzador (T2,L2)│
└────────────────────────────────────┘
```

## 6. Método para validar (design thinking, paso "testear")

**Protocolo de prueba con 5 personas** (basta con 5 — Nielsen): 1 nostálgico, 2 fans de MC (ideal: un niño con su adulto), 2 dibujantes hobby. Tareas sin ayuda: *"dibujá algo y guardalo"*, *"compartile tu mundo a un amigo"*, *"cambiá el tamaño del pincel"*. Observar dónde dudan (no preguntarles si "les gusta"). Cada duda = un hallazgo nuevo para este documento.

---

### Fuentes
[10 Usability Heuristics — NN/g](https://www.nngroup.com/articles/ten-usability-heuristics/) · [Heurísticas aplicadas a apps complejas — NN/g](https://www.nngroup.com/articles/usability-heuristics-complex-applications/) · [Progressive Disclosure](https://lollypop.design/blog/2025/may/progressive-disclosure/) · [Nielsen's Heuristics — The Decision Lab](https://thedecisionlab.com/reference-guide/design/nielsens-heuristics) · [Aplicando las 10 heurísticas](https://www.futurelabs.technology/writing/understanding-how-to-apply-nielsen-normans-10-usability-heuristics)
