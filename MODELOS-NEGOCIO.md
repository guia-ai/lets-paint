# Modelos de negocio: open source + privado / win-win / cooperativos

Investigación comparativa para decidir el modelo del proyecto Paint (en particular, el Atelier). Fuentes al pie. *Junio 2026.*

---

## Modelo 1 — Open Core (abierto + privado)

**Cómo funciona:** el núcleo del producto es open source y gratuito; las features "premium" son privadas y pagas. La línea divisoria clásica: lo que usa el individuo es gratis, lo que necesita la organización/poder se paga.

**Casos:**
- **GitLab** — núcleo open source; tiers pagos por nivel de usuario (individuo gratis → manager → director → C-level). Retención del 97% y cientos de millones en revenue.
- **Sidekiq** (Mike Perham, una sola persona) — framework open source LGPL; *Sidekiq Pro* y *Enterprise* cerrados. **~USD 10M/año siendo un solo dev.** El caso aspiracional del indie.

**Quién gana qué:** la comunidad recibe un núcleo real y útil gratis; el creador captura valor de quienes más lo necesitan; los usuarios pagos financian el mantenimiento del núcleo.

**Riesgos:** tensión permanente sobre *dónde* trazar la línea (si lo bueno queda detrás del pago, la comunidad se resiente — "crippleware"); la comunidad puede fork-ear las features pagas.

**Encaje con Paint:** natural — Atelier base gratis, "Atelier Pro" (capas, vectores) pago. Pero en un sitio estático el código Pro es visible: el candado es de honor.

---

## Modelo 2 — Sponsorware (win-win secuencial)

**Cómo funciona:** lo nuevo nace **solo para apoyantes** (sponsors recurrentes); se fija una **meta pública** (n sponsors o $X); al alcanzarla, **se libera para todo el mundo**. Quien paga no compra exclusividad permanente: compra acceso anticipado **y financia la apertura para todos**.

**Caso:** **Caleb Porzio** — su paquete *Sushi*: arrancó con 23 sponsors, prometió liberarlo a los 75, llegó a 101 (~USD 2.633/mes) y lo abrió. En 6 meses superó **USD 100.000** con este mecanismo (luego >100k/año sostenido).

**Quién gana qué:** el apoyante gana acceso primero + el rol de "mecenas" visible; la comunidad gana que TODO termina abierto; el creador gana ingresos recurrentes y previsibles. Es el único modelo donde **pagar es literalmente regalarle el producto al resto** — win-win estructural.

**Riesgos:** necesita audiencia/hype previo (sin público que espere, no hay tracción); ingresos menos predecibles que una suscripción clásica; exige transparencia de números (que también es virtud).

**Encaje con Paint:** altísimo — ya existe comunidad-juego (cacería, temporadas), y el espíritu "de fans para fans" calza perfecto con "apoyá hoy, se abre para todos".

---

## Modelo 3 — Cooperativa de plataforma (propiedad común)

**Cómo funciona:** la plataforma es propiedad de quienes la usan/trabajan, con gobernanza democrática (un miembro = un voto). Variante jurídico-licencia: **Coopyleft** — el software es libre *solo para quienes operan como cooperativa / economía social*; las empresas convencionales no pueden usarlo.

**Casos:**
- **CoopCycle** — federación de cooperativas de reparto en bici (¡con presencia en Argentina!). Software bajo licencia Coopyleft; el costo de servidores/mantenimiento se decide democráticamente entre las coops federadas.
- **Resonate** — streaming musical cooperativo multi-stakeholder (artistas + oyentes + trabajadores gobiernan juntos); modelo "stream-to-own": escuchás y vas comprando gradualmente la música.

**Quién gana qué:** los miembros son dueños (valor + decisiones); nadie extrae renta desde afuera; la licencia protege el commons de la apropiación corporativa.

**Riesgos:** estructura legal y de gobernanza pesada para un proyecto chico; crecimiento más lento; el revenue suele ser de subsistencia, no de escala; Coopyleft no es licencia OSI-aprobada (fricción con el ecosistema open source).

**Encaje con Paint:** como estructura completa hoy, sobredimensionado. Como **espíritu de gobernanza** (la comunidad vota el roadmap), encaja perfecto — y ya está construido en la cacería.

---

## Bonus — El modelo de los editores de dibujo reales (comparables directos)

| | **Aseprite** | **Krita** |
|---|---|---|
| Licencia | Source-available (EULA): podés ver y compilar el código vos mismo, **prohibido redistribuir** | 100% open source (GPL), sin restricciones |
| Qué se paga | **Los binarios** (web, Steam, itch.io) — comprar = comodidad + soporte | Versión **idéntica y gratis** en su web; en Steam/tiendas se paga por **conveniencia + apoyar** |
| Resultado | Negocio indie sólido (la referencia del pixel-art) | "Steam fue clave para pasar de 2 a 4 devs full-time" |

**Lección:** la gente **paga por comodidad y por apoyar**, aun cuando lo gratis existe al lado. No hace falta encerrar nada para cobrar.

---

## Comparativa

| Dimensión | Open Core | Sponsorware | Cooperativa | Aseprite/Krita |
|---|---|---|---|---|
| ¿Qué queda abierto? | El núcleo, para siempre | **Todo, eventualmente** | Todo (solo para coops, en Coopyleft) | Todo o casi todo |
| ¿Qué se paga? | Features premium permanentes | Acceso anticipado + mecenazgo | Membresía / aporte | Binarios / comodidad |
| Win-win estructural | Medio (línea conflictiva) | **Alto** (pagar libera para todos) | Alto (propiedad común) | Alto (gratis convive con pago) |
| Complejidad para arrancar | Media | **Baja** | Alta (legal/gobernanza) | Baja-media (tiendas) |
| Ingresos posibles | Altos (Sidekiq ~10M/año) | Medios (100k/año caso real) | Bajos-medios | Medios (sostiene equipos chicos) |
| Necesita | Features "de empresa" que encerrar | **Audiencia que espera** | Comunidad militante | Producto descargable |
| Riesgo principal | Resentimiento por la línea | Sin hype no arranca | Burocracia mata al proyecto | Piratería (les es indiferente) |

---

## 🌟 Propuesta: **"Temporadas Abiertas"** (sponsorware comunitario por temporadas)

Síntesis de los tres, a medida del proyecto Paint y del espíritu GUIA ("que todos tengamos ganas de ganar, que todos puedan ser ganadores, pero que sea desafiante"):

1. **La base es libre para siempre** *(de Krita)*: Clásico y PaintCraft nunca cobran (fan content, además lo exigen las guidelines de Mojang). El Atelier base, también gratis. Código abierto en GitHub (MIT).
2. **Cada feature Pro del Atelier nace como sponsorware** *(de Porzio)*: las **capas** salen primero solo para apoyantes (Cafecito/Ko-fi, desde $1). Meta pública: *"a los N apoyantes, capas se liberan para todos"*. Al llegar, se abren — y arranca la siguiente feature (vectores, formas…). **Pagar = tenerlo primero + regalárselo al mundo.**
3. **La comunidad gobierna el roadmap** *(espíritu cooperativo, sin burocracia)*: los que completan la cacería + los apoyantes **votan qué Paint/feature viene cada temporada**, con crédito eterno al proponente. Gobernanza real, estructura liviana. (Si algún día escala: formalizar como coop es el camino natural — CoopCycle ya opera en Argentina como referencia.)
4. **Conveniencia paga después** *(de Aseprite)*: cuando haya app empaquetada (PWA/desktop), versión en tiendas con precio — la web sigue gratis.
5. **Transparencia total**: metas, números de apoyo y estado de cada feature, públicos (el sponsorware lo exige y construye confianza).

**Por qué este y no uno puro:**
- Open core puro traiciona el "todos pueden ganar" (lo premium nunca llega a quien no paga).
- Cooperativa pura es burocracia prematura para un proyecto de una persona.
- Sponsorware puro no aprovecha la comunidad-juego ya construida (cacería/temporadas/votos).
- **Temporadas Abiertas** convierte el ciclo en un juego: *apoyo → feature → se abre → la comunidad vota la próxima → nuevo Paint trae nuevos secretos → más comunidad*. El flywheel del producto y el del negocio son el mismo.

**Primer experimento concreto:** capas del Atelier como sponsorware con meta de **50 apoyantes**. Si se alcanza: modelo validado. Si no: lo aprendido no cuesta nada y las capas se liberan igual (gesto de buena fe que construye la audiencia para la próxima).

---

---

## ✅ DECISIÓN (11/06/2026) — Modelo "Manos Libres"

Criterios de Andu (la vara real): **libertad personal, que exista más allá de él, crecimiento orgánico, mínima atención**. No busca maximizar ingresos.

Contra esos criterios se descartó el open core estricto (mantener un producto pago = soporte + cobros + "la línea" = atención constante) y el sponsorware con metas (exige empuje/hype). **Decisión:**

1. **Todo abierto (MIT) y largado al mundo** — GitHub público + Pages (deploy automático, $0, sobrevive sin atención). El proyecto puede continuar en forks: existencia más allá del autor, por diseño.
2. **Apoyo voluntario sin promesas** — botón Cafecito/Ko-fi, sin metas ni tiers ni recompensas. Regalo, no contrato.
3. **Operación automatizada** — rutina semanal (agente programado) que: valida códigos de easter eggs contra el Diario → pasa los válidos al Salón de la Fama, clasifica el feedback y entrega a Andu un resumen de 5 minutos (si no hay nada, silencio). El único rol humano: leer, y construir solo lo que entusiasme.
4. **Open core / sponsorware quedan como opciones futuras** si algo grande lo entusiasma — no como compromiso.

*Se crea la rutina automática en la sesión del deploy (para probarla con datos reales y verificar que el agente programado tenga acceso a Notion en ejecución desatendida).*

### Fuentes
- Open core / GitLab: [Stewardship de GitLab](https://handbook.gitlab.com/handbook/company/stewardship/) · [Cómo monetiza GitLab](https://about.gitlab.com/blog/2018/11/09/monetizing-and-being-open-source/) · [FourWeekMBA](https://fourweekmba.com/how-does-gitlab-make-money/)
- Sidekiq: [Wikipedia](https://en.wikipedia.org/wiki/Sidekiq) · [Entrevista a Mike Perham](https://garrettdimon.com/starting-and-sustaining/interviews/mike-perham) · [Startups for the Rest of Us #661](https://www.startupsfortherestofus.com/episodes/episode-661-millions-in-revenue-as-a-one-person-software-company)
- Sponsorware: [Caleb Porzio — Introducing Sponsorware](https://calebporzio.com/sponsorware) · [sponsorware/docs](https://github.com/sponsorware/docs) · [Indie Hackers — $100k/yr en GitHub Sponsors](https://www.indiehackers.com/post/i-just-hit-100k-yr-on-github-sponsors-how-i-did-it-878100de89)
- Cooperativas: [CoopCycle — licencia Coopyleft](https://wiki.coopcycle.org/en:license) · [CoopCycle en Argentina](https://geo.coop/articles/coopcycle-argentina) · [Resonate — It's a co-op](https://resonate.coop/coop/)
- Editores de dibujo: [Aseprite FAQ](https://www.aseprite.org/faq/) · [Aseprite — Wikipedia](https://en.wikipedia.org/wiki/Aseprite) · [Krita en Steam](https://store.steampowered.com/app/280680/Krita/) · [Krita — Wikipedia](https://en.wikipedia.org/wiki/Krita)
