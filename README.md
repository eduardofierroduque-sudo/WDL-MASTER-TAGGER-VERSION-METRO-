<p align="center">
  <img width="800" src="https://img.itch.zone/aW1nLzI3MTIwODUyLnBuZw==/original/YlguIp.png" alt="WDL MASTER TAGGER">
</p>

<div align="center">

# ░▒▓ WDL MASTER TAGGER ▓▒░

**EL SIMULADOR DE GRAFFITI EN PRIMERA PERSONA MÁS INMERSIVO DE LA WEB**

*No es un juego de disparos. Es un juego de trackear, marcar territorio y dejar tu firma.*

---

[![Play Now](https://img.shields.io/badge/JUGAR_AHORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/WWW.FIERRODUQUE.COM-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</div>

<img width="1920" height="1080" alt="WDL MASTER TAGGER Banner" src="https://github.com/user-attachments/assets/e36704b2-a72d-4af0-9d15-818dddf80608" />

---

## 📡 LA COLECCIÓN COMPLETA — 7 ESCENARIOS

<div align="center">

| # | ESCENARIO | TIPO | DIFICULTAD | JUGAR |
|---|---|---|---|---|
| 🚇 | **MAESTRANZA METRO/TREN** | Talleres ferroviarios | ⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) |
| 🚃 | **NYC SUBWAY** | Metro de Nueva York | ⭐⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) |
| 🚉 | **BA SUBTE** | Subte Buenos Aires | ⭐⭐⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) |
| 🏭 | **CONTAINER 1** | Astillero industrial | ⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) |
| 💡 | **BODEGA FLUOR** | Laberinto neón | ⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/) |
| 🏬 | **EDIFICIO ABANDONADO** | Rascacielos urbano | ⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) |
| 🚪 | **LABERINTO DE NOCHE** | Laberinto exterior | ⭐⭐ | [▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) |

</div>

> **Todos los escenarios incluyen RADIO integrada con música original de #eduardofierroduque vía YouTube.** Cada mapa se carga al instante desde el navegador. Sin descargas, sin instalaciones.

---

## 🎬 TRAILER OFICIAL

<p align="center">
  <a href="https://youtu.be/KE8L0RL6YC8">
    <img src="https://img.youtube.com/vi/KE8L0RL6YC8/0.jpg" alt="Trailer WDL MASTER TAGGER" width="600">
  </a>
  <br>
  <a href="https://youtu.be/KE8L0RL6YC8">▶ VER TRAILER EN YOUTUBE</a>
</p>

---

## ⚙️ MOTOR DEL JUEGO — LO QUE HAY BAJO EL CAPÓ

```
┌──────────────────────────────────────────────┐
│              WDL CUSTOM ENGINE                │
│  Three.js • WebGL • JavaScript Vanilla        │
│  DecalGeometry • AABB Collision • FogExp2    │
│  Raycasting • Drip Particles • Shadow Maps   │
│  YouTube IFrame API • Audio Fallback System  │
│  Zero Dependencies • Low Footprint (<50KB)   │
└──────────────────────────────────────────────┘
```

<table>
<tr>
<td width="50%">

### 🎨 SISTEMA DE PINTURA

- **DecalGeometry Spray** en NYC/BA — textura de aerosol real con *alphaTest*, *polygonOffset* y *depthWrite: false* para evitar Z-fighting.
- **CircleGeometry Decals** en el resto de mapas — ligeros, rápidos, con `renderOrder` dinámico por capa.
- **Válvula ajustable:** Grosor del trazo desde `0.05` hasta `5.0` unidades.
- **Selector de color completo** con paleta cromática ilimitada.

</td>
<td width="50%">

### 💧 SISTEMA DE GOTEO

- Si mantenés el spray en un punto fijo, el motor genera gotas finas que escurren verticalmente.
- **Física de fluido:** Cada gota tiene velocidad, longitud y grosor aleatorio — simulando viscosidad real del aerosol.
- Umbral configurable (`DRIP_THRESHOLD`) y máximo de gotas activas en pantalla.

</td>
</tr>
<tr>
<td width="50%">

### 🚆 TRENES EN MOVIMIENTO (BA SUBTE)

- **Tren 1:** Vía X=-100, sentido norte, aparece cada 120s.
- **Tren 2:** Vía X=+100, sentido sur, desincronizado del primero.
- 4 coches articulados con faro *PointLight* que ilumina en la distancia.
- **Colisión AABB** contra la cámara del jugador → **GAME OVER**.

</td>
<td width="50%">

### 📸 SNAPSHOT MODE [P]

- Presioná `[P]` para capturar tu pieza terminada.
- El motor renderiza el buffer actual y descarga un **PNG en alta resolución**.
- Listo para compartir en redes sociales.

</td>
</tr>
</table>

---

## 🗺️ LOS MAPAS — UNO POR UNO

<img width="144" height="68" alt="metro1" src="https://github.com/user-attachments/assets/9ae73a9b-e3a8-447a-b50f-269e039a506a" />
<img width="144" height="68" alt="metro2" src="https://github.com/user-attachments/assets/62368dac-d8d3-49ea-9a60-97818bd30655" />
<img width="144" height="68" alt="metro3" src="https://github.com/user-attachments/assets/65f23e73-9763-432e-983f-bdd13f1a3b4b" />
<img width="144" height="68" alt="metro4" src="https://github.com/user-attachments/assets/5f0d1497-100b-4477-9db0-f27bf182eeca" />
<img width="144" height="68" alt="metro5" src="https://github.com/user-attachments/assets/493d1c9b-94b0-4f5c-8f58-f91cd6acfef9" />

---

### 🚇 1. MAESTRANZA METRO/TREN — Santiago, Talleres L2

> *El original. El que empezó todo. Un hangar ferroviario con 22 formaciones NS-74 esperando ser intervenidas.*

| | |
|---|---|
| **Ambientación** | Hangar industrial (400×600×50), 3 túneles, andenes, columnas de hierro, 40 cajas de repuestos distribuidas. |
| **Iluminación** | Luces rojas `#ff3300` en los túneles. Niebla `FogExp2(0x020202, 0.008)`. Cian `#00a9e0` en los trenes. |
| **Trenes** | 22 formaciones estáticas NS-74, pintura azul, con cabina, parabrisas de vidrio y acoples metálicos. |
| **Movilidad** | WASD + Shift sprint (0.45→0.75) + Space salto + rebote vertical sinusoidal al caminar. |
| **Timer** | 1200 segundos. Al llegar a 0, se recarga la página. |
| **Radio** | YouTube integrada vía IFrame API. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger)

---

### 🚃 2. NYC SUBWAY — New York City

> *El underGround neoyorquino. 14 trenes plateados en un depósito de 4 vías con pasillos transversales cada 120 metros.*

| | |
|---|---|
| **Ambientación** | Estación central (400×100m) + túneles norte/sur con cruces transversales. Paredes de azulejo blanco, columnas verdes NYC, tubos de túnel. |
| **Iluminación** | Luces frías de estación `#dcf0f7` cada 60m. Luces cálidas `#ffb84d` en los tubos. Niebla `FogExp2(0x020202, 0.012)`. |
| **Trenes** | 14 formaciones NYC: metal plateado, techo negro, luces LED rojas en la cola. |
| **Pintura** | **DecalGeometry** con textura de spray radial. Sistema de goteo dinámico (máx. 400 gotas activas). |
| **Brush** | Válvula 0.1 a 5.0 — de tags finísimos a throw-ups monumentales. |
| **Radio** | YouTube integrada. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-ny-subway)

---

### 🚉 3. BA SUBTE — Buenos Aires (EL MÁS COMPLETO)

> *990 líneas de código. Un laberinto en grilla de 1100×1100m con 2 trenes en movimiento que te pueden borrar. Game Over real.*

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzEyLnBuZw==/original/3mj0P3.png" width="48%" alt="BA Subte 1">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="48%" alt="BA Subte Game Over">
</p>

| | |
|---|---|
| **Ambientación** | Grilla de 11×11 bloques (1100×1100m). Bloques de 70m con pasillos de 30m. Estación central vacía (100×300m). Columnas de hierro estilo Subte. |
| **Iluminación** | Luces cálidas `#ffddaa` en estación, `#ffb84d` en intersecciones. Niebla `FogExp2(0x020202, 0.008)`. |
| **Trenes** | 2 trenes en movimiento circulando en vías laterales (X=-100 y X=+100). **Colisionan con el jugador → GAME OVER.** Se reinician cada 120s. |
| **Alerta final** | Últimos 20 segundos: pantalla pulsa en rojo, niebla se tiñe de sangre, overlay de advertencia titila. |
| **Pintura** | DecalGeometry + goteo. Mismo sistema de NYC pero optimizado. |
| **Audio** | Sistema dual: streams HTML5 Audio en local (`file://`) + YouTube IFrame en servidor. |
| **Brush** | 0.1 a 5.0. Menú bilingüe ES/EN con controles, misión y advertencias. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-tren-3) | [Gameplay](https://www.youtube.com/watch?v=dHxB3NoJs1k)

---

### 🏭 4. CONTAINER 1 — Astillero Industrial / Bodegas de Noche

> *Seis complejos de galpones, un parque de parkour con pilas de containers, calles en cruz y tuberías subterráneas. Sin enemigos — solo vos y la lata.*

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjQzLmdpZg==/original/NQSFlF.gif" width="48%" alt="Container gif 1">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjUxLmdpZg==/original/%2BjKqLa.gif" width="48%" alt="Container gif 2">
</p>

| | |
|---|---|
| **Ambientación** | 6 galpones (50×12×60m c/u), 2×3 grilla, con columnas internas. Zona de parkour con 12 pilas de cajas. Calles en forma de cruz. Tuberías subterráneas. |
| **Iluminación** | Luz de luna `#556677` + PointLights RGB: verde `#39ff14`, magenta `#ff00ff`, cian `#00ffff`. Sombras activadas. |
| **Trenes** | No hay. Simulación libre — *rayalo hasta que el juego se rompa.* |
| **Pintura** | CircleGeometry decals, `polygonOffset factor: -4`, `renderOrder` por capa. Goteo con anti-constante (movimiento de mouse resetea acumulación). |
| **Brush** | 0.05 a 0.8. Movimiento 0.28, salto 0.24. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-containers-1)

---

### 💡 5. BODEGA FLUOR — Laberinto Neón

> *El más minimalista. 365 líneas. Un laberinto oscuro con una sola luz rojiza. La UI brilla en verde neón. Experiencia horror-graffiti.*

| | |
|---|---|
| **Ambientación** | Laberinto hardcodeado de 15×20 celdas (120×160m). Pasillos de 1 celda de ancho. Sin salidas fáciles. |
| **Iluminación** | Una sola `AmbientLight #704045` (rojo apagado) a intensidad 1.2. Oscuridad casi total. |
| **Pintura** | CircleGeometry decals, rango 6. El goteo se acumula más rápido si no movés al jugador. |
| **Soundtrack** | Radio YouTube con música para perderse en la oscuridad. |
| **Brush** | Movimiento lento (0.20). Sin sprint, sin sombras, sin enemigos. Puro mood. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/)

---

### 🏬 6. EDIFICIO ABANDONADO

> *El único con luz de día. Cinco pisos de un edificio tomado, rampas entre niveles, ventanales de vidrio azul translúcido y 50 rascacielos en el horizonte.*

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQwLmdpZg==/original/DaJkjS.gif" width="32%" alt="Edificio gif 1">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQxLmdpZg==/original/JpuipW.gif" width="32%" alt="Edificio gif 2">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQ3LmdpZg==/original/UD6LMn.gif" width="32%" alt="Edificio gif 3">
</p>

| | |
|---|---|
| **Ambientación** | Edificio de 5 pisos (altura de piso: 7), grilla 8×10 por planta. Rampas alternadas entre pisos. Ventanas cada 3 celdas en el perímetro. 50 rascacielos aleatorios alrededor. |
| **Iluminación** | **Luz de día:** `AmbientLight 0.6` + `DirectionalLight` (sol) `0.9` desde (100, 200, 100). Cielo azul `#87CEEB`. |
| **Estructura** | Hormigón gris, pisos oscuros, vidrio translúcido `#add8e6` con opacidad 0.3. |
| **Pintura** | CircleGeometry decals, rango 6, `polygonOffset` variable por conteo de capas. |
| **Brush** | 0.05 a 0.6. Movimiento 0.25. Sin goteo. Verticalidad pura. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado)

---

### 🚪 7. LABERINTO DE NOCHE

> *Laberinto exterior amurallado con un tren estático al centro, bloques para parkour y containers dinámicos en el perímetro. La pintura se adhiere a los objetos.*

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY1LmdpZg==/original/2TtbmH.gif" width="32%" alt="Laberinto gif 1">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzcxLmdpZg==/original/QzmamK.gif" width="32%" alt="Laberinto gif 2">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="32%" alt="Laberinto gif 3">
</p>

| | |
|---|---|
| **Ambientación** | Grilla 8×10 (mismo layout que un piso del Edificio), muros de altura 6. Tren estático negro en el centro. Bloques escalonados para parkour. Containers dinámicos alrededor. |
| **Iluminación** | Luz de día: `AmbientLight 0.7` + sol `0.8`. Cielo azul. Niebla más densa que Edificio (`0.02`). |
| **Pintura** | CircleGeometry decals, rango 6. **Único mapa donde la pintura se adhiere como hijo del objeto** (`hit.object.add(mark)`), no de la escena. Si el objeto se moviera, la pintura se movería con él. |
| **Brush** | Movimiento más lento (0.18). Sin goteo. |

[▶ JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) | [itch.io](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche)

---

## 📊 COMPARATIVA DE ESCENARIOS

| Característica | Metro | NYC | BA Subte | Container | Bodega Fluor | Edificio | Laberinto |
|---|---|---|---|---|---|---|---|
| **Líneas de código** | 533 | 666 | 990 | 504 | 365 | 486 | 511 |
| **DecalGeometry** | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sistema goteo** | ❌ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Trenes en movimiento** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Game Over** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Alerta 20s** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sprint** | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sombras** | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| **Múltiples pisos** | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| **Pintura adherida a objetos** | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| **Luz de día** | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ |
| **Audio dual (local+remoto)** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |

---

## 🔧 CONTROLES UNIVERSALES

<div align="center">

| TECLA | ACCIÓN |
|---|---|
| `W A S D` / `↑ ← ↓ →` | Movimiento |
| `SHIFT` | Correr (Metro, NYC, BA Subte) |
| `ESPACIO` | Saltar |
| `MOUSE` | Mirar alrededor |
| `CLICK IZQUIERDO` | Pintar spray |
| `P` | 📸 Captura de pantalla (PNG) |
| `R` | Respawn |
| `ESC` | Soltar puntero |

</div>

---

## 🛠️ ESPECIFICACIONES TÉCNICAS

```
┌────────────────────────────────────────────────────┐
│                                                    │
│   MOTOR        Custom Engine sobre Three.js WebGL  │
│   LENGUAJE     JavaScript Vanilla (JS Puro)        │
│   PESO         15-50 KB por mapa                   │
│   DEPENDENCIAS CERO — sin bundlers, sin frameworks │
│   RENDERIZADO  requestAnimationFrame 60fps target  │
│   COLABORACIÓN aceleración GPU del navegador       │
│   COMPATIBLE   Chrome, Edge, Firefox, Opera, Brave │
│                                                    │
└────────────────────────────────────────────────────┘
```

### Características del Motor

| Sistema | Implementación |
|---|---|
| **Detección de superficies** | `Raycaster` de Three.js con origen en la cámara |
| **Aplicación de pintura** | `DecalGeometry` (NYC, BA) o `CircleGeometry` con `polygonOffset` |
| **Colisiones** | `Box3` para paredes/muros, AABB para trenes en movimiento |
| **Niebla** | `FogExp2` con color y densidad configurables por escenario |
| **Iluminación** | `AmbientLight` + `DirectionalLight` + `PointLight` en posiciones clave |
| **Radio** | YouTube IFrame API con detección de protocolo (local vs servidor) |
| **Captura** | `canvas.toDataURL('image/png')` con descarga automática |

> ⚠️ **Recomendación:** Usar navegadores basados en **Chromium** para rendimiento óptimo. Los FPS dependen directamente de la aceleración de hardware por GPU.

---

## 🎯 FUNDAMENTO ARTÍSTICO

> *"WDL Master Tagger no es un juego para ganar. Es un juego para ESTAR — para meterse en la atmósfera de un subte abandonado, sentir la presión del reloj, escuchar el zumbido de los rieles y saber que en cualquier momento un tren te puede borrar."*

Este proyecto nace como una **herramienta de práctica y visualización** para escritores de graffiti, diseñadores y artistas visuales. No es un juego de puntuación — es un **espacio de simulación estética** donde probar combinaciones de colores, composiciones y estilos antes de llevarlos al mundo real.

- 🖌️ Experimentá con _tags_, _throw-ups_ y _piezas_ sin riesgo.
- 🌃 Disfrutá del flujo creativo en un ambiente industrial atmosférico.
- 📸 Documentá y compartí tus obras en redes sociales.
- 🎵 Escuchá música original mientras pintás.

---

## 🚀 HOJA DE RUTA

- [x] ~~7 escenarios jugables vía navegador~~
- [x] ~~Sistema de pintura con DecalGeometry y goteo~~
- [x] ~~Trenes en movimiento con colisión (BA Subte)~~
- [x] ~~Radio YouTube integrada~~
- [x] ~~Snapshot mode~~
- [x] ~~Menú principal con acceso a todos los mapas~~
- [ ] Compilación nativa `.exe` (Standalone) para eliminar limitaciones de memoria del navegador
- [ ] Mejora de post-procesamiento visual (bloom, SSAO)
- [ ] Nuevos mapas: fábrica abandonada, puente ferroviario, depósito de containers 2

---

## 🔗 ENLACES OFICIALES

<p align="center">

[![GitHub Pages](https://img.shields.io/badge/JUGAR_AHORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/www.fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</p>

### Por escenario en itch.io:

| Escenario | itch.io |
|---|---|
| Metro/Tren Santiago | [fierroduque.itch.io/wdl-master-tagger](https://fierroduque.itch.io/wdl-master-tagger) |
| NYC Subway | [fierroduque.itch.io/wdl-master-tagger-ny-subway](https://fierroduque.itch.io/wdl-master-tagger-ny-subway) |
| BA Subte | [fierroduque.itch.io/wdl-master-tagger-tren-3](https://fierroduque.itch.io/wdl-master-tagger-tren-3) |
| Container 1 / Bodega | [fierroduque.itch.io/wdl-master-tagger-containers-1](https://fierroduque.itch.io/wdl-master-tagger-containers-1) |
| Edificio Abandonado | [fierroduque.itch.io/wdl-master-tagger-edificio-abandonado](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado) |
| Laberinto de Noche | [fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche) |

### Videos en YouTube:

| Video | Link |
|---|---|
| 🎬 Trailer Oficial | [youtu.be/KE8L0RL6YC8](https://youtu.be/KE8L0RL6YC8) |
| 🎮 Gameplay Metro/Tren | [youtube.com/watch?v=dHxB3NoJs1k](https://www.youtube.com/watch?v=dHxB3NoJs1k) |

---

## 📦 ESTRUCTURA DEL REPOSITORIO

```
WDL-MASTER-TAGGER-VERSION-METRO-/
├── index.html                          ← Menú principal con acceso a los 7 mapas
├── README.md                           ← Este documento
├── juego graffiti METRO/               ← Maestranza Metro/Tren (Santiago)
│   └── index.html
├── juego graffiti trenes 2/            ← NYC Subway Edition
│   └── index.html
├── juego graffiti trenes 3/            ← BA Subte Edition (el más completo)
│   └── index.html
├── juego grafiti BODEGA/               ← Container 1 / Bodegas de Noche
│   └── index.html
├── juego grafiti BODEGA FLUOR/         ← Laberinto Neón
│   └── index.html
├── juego grafiti EDIFICIO/             ← Edificio Abandonado (5 pisos)
│   └── index.html
└── juego grafiti LABERINTO/            ← Laberinto de Noche
    └── index.html
```

Cada carpeta contiene un único archivo `index.html` autónomo. **Cero dependencias, peso ultraligero.** Abrí cualquier `index.html` en tu navegador y empezá a pintar.

---

<p align="center">
  <em>WDL — De la calle al código.</em><br>
  <strong>© 2025-2026 Eduardo Fierro — fierroduque.com</strong><br><br>
  <sub>No se utilizó IA generativa en la creación de assets visuales. Hecho a mano, línea por línea.</sub>
</p>
