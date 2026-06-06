<p align="center">
  <img width="800" src="https://img.itch.zone/aW1nLzI3MTIwODUyLnBuZw==/original/YlguIp.png" alt="WDL MASTER TAGGER">
</p>

<div align="center">

# WDL MASTER TAGGER

**Di yi ren cheng tu ya mo ni qi. HTML5, WebGL, Three.js. Chun JavaScript.**

*Zhe bu shi yi ge she ji you xi. Zhe shi yi ge tu ya you xi: biao ji ling di, liu xia ni de yin ji.*

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTI1LnBuZw==/original/KQLcWZ.png" width="30%" alt="Metro">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTI5LnBuZw==/original/ayoYfT.png" width="30%" alt="Metro">
  <img src="https://img.itch.zone/aW1nLzI3MTIxMDM5LmpwZw==/original/cZboip.jpg" width="30%" alt="Metro">
  <br>
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzk0LmdpZg==/original/eBr%2FpG.gif" width="30%" alt="Metro gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzk4LmdpZg==/original/rjXKCU.gif" width="30%" alt="Metro gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA2LmdpZg==/original/VWu641.gif" width="30%" alt="Metro gameplay">
</p>

---

[![Li Ji Wan](https://img.shields.io/badge/LIJI_WAN-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</div>

<img width="1920" height="1080" alt="WDL MASTER TAGGER Banner" src="https://github.com/user-attachments/assets/e36704b2-a72d-4af0-9d15-818dddf80608" />

---

## He Ji -- 7 Ge Ke Zai Liu Lan Qi Wan De Chang Jing

<div align="center">

| # | Chang Jing | Lei Xing | Feng Ge | Play |
|---|---|---|---|---|
| 1 | **Maestranza Metro/Tren** | Sheng Di Ya Ge Tie Lu Gong Chang | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) |
| 2 | **NYC Subway** | Niu Yue Di Tie | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) |
| 3 | **BA Subte** | Bu Yi Nuo Si Ai Li Si Di Tie | Wei Xian | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) |
| 4 | **Container 1** | Gong Ye Chuan Wu | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) |
| 5 | **Bodega Fluor** | Hei An Mi Gong | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/) |
| 6 | **Fei Qi Da Lou** | Mo Tian Da Lou, 5 Ceng | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) |
| 7 | **Ye Jian Mi Gong** | Shi Wai Wei Qiang Mi Gong | Zi You | [WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) |

</div>

> Suo you di tu jun pei bei tong guo YouTube IFrame API bo fang de Eduardo Fierro zhi zuo yin yue dian tai. Mei ge di tu dou shi yi ge ji shi jia zai de du li HTML wen jian. Wu xu xia zai, wu xu an zhuang.

---

## Trailer

<p align="center">
  <a href="https://youtu.be/KE8L0RL6YC8">
    <img src="https://img.youtube.com/vi/KE8L0RL6YC8/0.jpg" alt="Trailer WDL MASTER TAGGER" width="600">
  </a>
  <br>
  <a href="https://youtu.be/KE8L0RL6YC8">ZAI YOUTUBE GUAN KAN YU GAO PIAN</a>
</p>

---

## Yin Qing -- Zu Jian Yu Xi Tong

Everything is written in Vanilla JavaScript on top of Three.js r128+, loaded via CDN. No bundlers, no frameworks, no npm dependencies. A single HTML file per scenario withtaining all CSS, JS, and the 3D scene inline. File size per map ranges from 15 KB to 50 KB.

### DecalGeometry Pen Qi Xi Tong

In the NYC Subway and BA Subte maps, paint is applied unog `DecalGeometry` de Three.js. A procedural radial spray texture is generated on an offscreen 2D canvas, unog radial gradients with varying opacity and dispersion levels. That texture is passed as `map` a un `MeshBasicMaterial` withfigured with `alphaTest: 0.1`, `polygonOffset: true`, `polygonOffsetFactor: -4` y `depthWrite: false`. This eliminates Z-fighting between overlapping paint layers without modifying the wall geometry.

El `Raycaster` is cast from the camera position toward the center of the screen, with a withfigurable range of 6 to 15 dan wei depending on the map. If the ray hits a surface, a `DecalGeometry` is placed at the impact point, oriented according to the intersected face normal. Decal size is withtrolled with the valve (slider en UI).

The remaining maps use `CircleGeometry` with `MeshBasicMaterial`, applying `renderOrder` incremental and `polygonOffset` with variable factor per layer. It's lighter but lacks the same spray texture fidelity.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="32%" alt="Decal spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="32%" alt="Decal example">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="32%" alt="Decal result">
</p>

### Cheng Xu Hua Di Luo Xi Tong

When the player holds the spray on the same spot, an internal counter `dripCounter` increments. Upon exceeding the `DRIP_THRESHOLD` (15 threshold on most maps), the engine spawns drips at the impact position. Each drip is a `BoxGeometry` very thin and elongated, with a semi-transparent material matching the active stroke color.

Each drip has randomized properties generated at spawn: fall speed (`dripSu Du`, between 0.08 and 0.25 dan wei per frame), initial length (`dripLength`, between 0.05 and 0.3), and a random lateral offset to prevent all drips from falling in a perfect line. The drip stretches progressively on the Y axis (`scale.y += dripSu Du * 0.1`) and displaces downward (`position.y -= dripSu Du`). Cuando `scale.y` exceeds a maximum or the drip leaves the visible range, it is removed from the `activeDrips`.

There is an active drip limit (300 a 400 depending on the map). When reached, the oldest drips are removed first (FIFO). In the Bodega and Bodega Fluor maps, the drip counter resets or slows down if the player moves the mouse, simulating spray spreading over a wider surface instead of accumulating in one spot.

Specifically in Bodega Fluor, if the distance the mouse travels between frames is less than 0.05 dan wei, `dripCounter` increments by 2 per frame (fast accumulation). If the mouse moves more, it jin zaicrements by 0.5.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzA0LmdpZg==/original/HdS8d7.gif" width="24%" alt="Drip system">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="24%" alt="Drip detail">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzk5LmdpZg==/original/5%2BWVx7.gif" width="24%" alt="Drip paint">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="24%" alt="Drip result">
</p>

### Yi Dong Lie Che Yu AABB Peng Zhuang

Exclusive to the BA Subte map. Two trains run on fixed side tracks (X = -100 y X = +100). Each train has 4 cars assembled with `BoxGeometry`, totaling approximately 300 dan wei in length. They carry a `PointLight` headlight acting as a beawith (`color: #ffeecc, intensity: 3, distance: 400`), visible through the fog.

The movement logic is linear and deterministic: Train 1 moves in the +Z direction from Z = -550 until it disappears at Z > 650. Train 2 moves in the -Z direction from Z = +550 until Z < -650. Su Du is 3.0 dan wei per frame (at 60fps, roughly 180 virtual meters per sewithd). Upon disappearing, a respawn is scheduled with `setTimeout`: Train 1 every 120 sewithds exactly, Train 2 every 120 sewithds but offset (starts 75s after the first). The first train appears 15 sewithds after the game starts, the sewithd at 75 sewithds.

Collision detection uses AABB (Axis-Aligned Bounding Box). It does not use `Box3` from Three.js for this, but a direct range comparison: if the train's Z range (Z position plus/minus half its length) overlaps the player's Z range, and both share the same track X axis, there's a collision. The screen goes black, a red overlay appears with the text HIT BY THE TRAIN in sans-serif font, and a reload link. No respawn, no withtinue.

In the last 20 sewithds of the timer, the scene background (`scene.background`) begins to oscillate between black and dark red, the fog `FogExp2` shifts its color to `#330000`, and an HTML overlay with the text SECURITY ALERT -- LEAVE THE AREA IMMEDIATELY flashes over the canvas. This is implemented with `setInterval` at 500ms that toggles CSS classes and modifies scene color properties in real time.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="32%" alt="Tren moving">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="32%" alt="Game Over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="32%" alt="Alerta roja">
</p>

### Yin Pin Yu Dian Tai Xi Tong

All maps integrate the YouTube IFrame API. A hidden iframe element is created that loads the YouTube player without UI and starts playing a playlist with original music produced by Eduardo Fierro.

The BA Subte map has a dual audio system. When the HTML is loaded from a web server (HTTP/HTTPS), the YouTube IFrame API is used normally. But when opened from `file://` (local double click), the browser blocks the YouTube IFrame API due to same-origin policies. In that case, the code automatically switches to HTML5 audio streams unog the `<audio>` element, with direct URLs to MP3 files. This allows the game to be functional even when run locally without a server.

Detection is done by checking `window.location.protocol`: si es `file:`, the local audio fallback is activated. Si es `http:` o `https:`, YouTube is used. YouTube player volume is adjusted via `player.setVolume()` and the native audio element via `audio.volume`.

### Kuai Zhao Mo Shi -- Jie Tu Gong Neng

When presnog the `P`, key, `renderer.render(scene, camera)` is called to ensure the buffer is up to date, then the canvas withtent is extracted with `canvas.toDataURL('image/png')`. A temporary anchor element is created with `download = 'wdl-snapshot.png'`, the data URL is assigned as `href` and a programmatic click is triggered. The result is a PNG at the canvas native resolution, downloaded directly.

### Xuan Ran Yu Wu Qi

All maps use `FogExp2` from Three.js, which implements quadratic exponential fog: visibility decays according to `exp(-density * distance^2)`. Density varies between maps:

| Mapa | Densidad | Wu Qi Yan Se |
|---|---|---|
| Metro | 0.008 | #020202 |
| NYC Subway | 0.012 | #020202 |
| BA Subte | 0.008 | #020202 (zhuan bian wei #330000 jing bao shi) |
| Bodega | 0.004 | #0a0a0b |
| Bodega Fluor | 0.03 | #020202 |
| Edificio | 0.01 | #87CEEB (cielo) |
| Laberinto | 0.02 | #87CEEB (cielo) |

NYC has the densest fog (0.012) to accentuate the enclosed tunnel atmosphere. Bodega Fluor has 0.03, nearly opaque at 50 meters. Bodega has the lightest (0.004), allowing the warehouses to be seen at a distance. Edificio y Laberinto use tian kong-blue color as they are daytime maps.

### Per-Chang Jing Lighting

Each map has a lighting setup designed for its atmosphere:

- **Metro:** `AmbientLight(0xffffff, 0.3)` base, `DirectionalLight(0xffffff, 0.4)`, `PointLight(#ff3300, 2, 80)` red lights in the tunnels.
- **NYC Subway:** `AmbientLight(0xffffff, 0.08)` minimo, `PointLight(#dcf0f7, 0.15, 200)` cool lights in the station, `PointLight(#ffb84d, 0.1, 180)` warm lights in the tunnel tubes.
- **BA Subte:** `AmbientLight(0xffffff, 0.08)`, `PointLight(#ffddaa, 0.2, 200)` calidas, `PointLight(#ffb84d, 0.1, 180)` at intersections.
- **Bodega:** `AmbientLight(0xffffff, 1.5)`, `DirectionalLight(#556677, 1.5)` luna, `PointLight` RGB (verde, magenta, cian) + sombras `PCFSoftShadowMap`.
- **Bodega Fluor:** Solo `AmbientLight(#704045, 1.2)`. A single reddish light. It's the darkest map.
- **Edificio:** `AmbientLight(0xffffff, 0.6)`, `DirectionalLight(0xffffff, 0.9)` daylight sun.
- **Laberinto:** `AmbientLight(0xffffff, 0.7)`, `DirectionalLight(0xffffff, 0.8)` daylight sun.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="23%" alt="Luz Metro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA2LmdpZg==/original/VWu641.gif" width="23%" alt="Luz NYC">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODk4LnBuZw==/original/uPh9Ab.png" width="23%" alt="Luz BA Subte">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="23%" alt="Luz Container">
</p>

### Wan Jia Yi Dong Yu Wu Li

First-person movement is implemented without unog `PointerLockCao Zuo` from Three.js. The camera rotates directly based on `movementX` y `movementY` from the `mousemove`. Pitch (Y) is clamped between -PI/2 and PI/2.

WASD movement is relative to the camera orientation. A forward vector is calculated from `camera.rotation.y` usando `no/cos`, and a perpendicular right vector. Tiao Yueing uses `playerVelocity.y` which decreases by gravity each frame. A ground check keeps the player at Y = playerGao Du.

Parameters by map:

| Mapa | Su Du | Sprint | Zhong Li | Tiao Yue | Gao Du |
|---|---|---|---|---|---|
| Metro | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| NYC | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| BA Subte | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| Bodega | 0.28 | -- | 0.009 | 0.24 | 2.5 |
| Bodega Fluor | 0.20 | -- | 0.008 | 0.18 | 2.0 |
| Edificio | 0.25 | -- | 0.008 | 0.22 | 2.0 |
| Laberinto | 0.18 | -- | 0.008 | 0.22 | 2.0 |

The train maps share agile parameters with sprint. The rest are slower, designed for unhurried exploration.

### Huan Jing Peng Zhuang Jian Ce

Collisions against walls and objects are handled with `Box3` de Three.js. Each static geometry gets a bounding box via `computeBoundingBox()`. Before applying player movement, a temporary `Box3` is created around the future position and tested with `intersectsBox()` against all colliders. If there's an intersection, movement on that axis is cancelled.

In Bodega Fluor, detection is simpler: `Math.abs` against the maze grid coordinates. In BA Subte, the maze walls are hundreds of individual `BoxGeometry` each with its own `Box3`.

---

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTI1LnBuZw==/original/u76WYF.png" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MjAxLnBuZw==/original/ixdXIK.png" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk3LnBuZw==/original/8hWBY6.png" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODk4LnBuZw==/original/uPh9Ab.png" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI3NTIzOTA2LnBuZw==/original/Ocdn3F.png" width="18%" alt="Gameplay">
  <br>
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjY1LmdpZg==/original/DqZYnd.gif" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjY5LmdpZg==/original/%2FJ%2B96w.gif" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzI5LmdpZg==/original/%2BVEOzt.gif" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="18%" alt="Gameplay">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTM5LnBuZw==/original/SJWreF.png" width="18%" alt="Gameplay">
</p>

---

## Di Tu Yi Lan

<img width="144" height="68" alt="metro1" src="https://github.com/user-attachments/assets/9ae73a9b-e3a8-447a-b50f-269e039a506a" />
<img width="144" height="68" alt="metro2" src="https://github.com/user-attachments/assets/62368dac-d8d3-49ea-9a60-97818bd30655" />
<img width="144" height="68" alt="metro3" src="https://github.com/user-attachments/assets/65f23e73-9763-432e-983f-bdd13f1a3b4b" />
<img width="144" height="68" alt="metro4" src="https://github.com/user-attachments/assets/5f0d1497-100b-4477-9db0-f27bf182eeca" />
<img width="144" height="68" alt="metro5" src="https://github.com/user-attachments/assets/493d1c9b-94b0-4f5c-8f58-f91cd6acfef9" />

---

### 1. Maestranza Di Tie/Lie Che -- Sheng Di Ya Ge L2 Gong Chang

The original. The one that started it all. I wrote it thinking about the Line 2 workshops of the Santiago Metro, a massive industrial hangar with NS-74 trains parked on dead tracks. There are 22 blue trains `#00a9e0` with cabins, glass windows, metal couplers, and position lights.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="30%" alt="Metro tren">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA4LmdpZg==/original/aQxVgp.gif" width="30%" alt="Metro pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA5LmdpZg==/original/5dwhdf.gif" width="30%" alt="Metro tunel">
</p>

The map is a 400 by 600 meter hangar with a height of 50. Three side tunnels, elevated platforms, iron columns every 40 meters, and about 40 spare parts crates. The tunnel lights are red `#ff3300`, intensity 2, range 80. The fog is `FogExp2(0x020202, 0.008)`. The paint uses `CircleGeometry` with `MeshBasicMaterial`. No drip system -- this version predates that development. No moving trains.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTE0LnBuZw==/original/xtXMwi.png" width="48%" alt="Metro snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTIxLnBuZw==/original/yQMlWG.png" width="48%" alt="Metro accion">
</p>

The timer runs 1200 sewithds. When it reaches zero it calls `location.reload()`. If you fall below Y = -40, automatic respawn.

- Yi Dong: 0.45 caminando, 0.75 corriendo (Shift)
- Zhong Li: 0.012, salto: 0.32, altura jugador: 2.4
- Spray range: 15 dan wei
- Valve: 0.1 a 1.4, step 0.05, default 0.4
- 533 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger)

---

### 2. NYC Subway -- New York City

The New York version. A 400 by 100 meter central station with four tracks extending in tunnels to the north and south. Cross-passages every 120 meters. White tile walls `#dddddd`, NYC green steel columns `#123524`. Tunnels in closed tube with ceiling, floor, and curved walls.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTMyLnBuZw==/original/aR5DO4.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTMwLnBuZw==/original/9Uouzu.png" width="30%" alt="NYC Subway">
</p>

14 NYC-style trains parked: silver metal, black roof, red LED tail lights. The trains are static but the atmosphere is tense: near-total darkness, minimal lights, dense fog (0.012). First map to implement `DecalGeometry` for painting and the complete drip system. Valve from 0.1 to 5.0, allowing from ultra-fine tags to throw-ups that cover a train in sewithds.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="24%" alt="NYC interior">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="24%" alt="NYC pintura">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="24%" alt="NYC spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="24%" alt="NYC gameplay">
</p>

- Yi Dong: 0.45 / 0.75 (sprint)
- Zhong Li: 0.012, salto: 0.32, altura: 2.4
- Spray range: 15, Valve: 0.1 a 5.0, default 1.0
- Goteo: DRIP_THRESHOLD 15, max 400 gotas activas
- 666 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-ny-subway)

---

### 3. BA Subte -- Bu Yi Nuo Si Ai Li Si (zui wan zheng)

990 lines. The largest and most polished map. A grid maze of 11 por 11 blocks, 1100 por 1100 metros. 70m blocks with 30m passages. Empty central station of 100 by 300 meters. Cream beige walls `#e6dec3`, dark iron columns `#2a302d`, colored advertinog panels.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzEyLnBuZw==/original/3mj0P3.png" width="24%" alt="BA Subte">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="24%" alt="BA Subte trenes">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTg0LnBuZw==/original/EKymke.png" width="24%" alt="BA Subte laberinto">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzk2LnBuZw==/original/XvZrkX.png" width="24%" alt="BA Subte gameplay">
</p>

The only map with moving trains. Two 4-car trains with front headlights visible through the fog. They run on fixed tracks at X = -100 and X = +100. If you stay on the track, Game Over with no respawn. In the last 20 sewithds, the screen pulses red, the fog turns blood-colored, and a warning sign flashes.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="30%" alt="BA Subte tren movil">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="30%" alt="BA Subte game over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="30%" alt="BA Subte menu">
</p>

Bilingual ES/EN menu with withtrols, mission, and warnings. Dual audio (YouTube on server, HTML5 Audio locally). Advanced event handling: withtext menu prevention, mouseleave/blur resets, first mousemove ignored.

- Yi Dong: 0.45 / 0.75 (sprint)
- Zhong Li: 0.012, salto: 0.32, altura: 2.4
- Spray range: 15, Valve: 0.1 a 5.0, default 1.0
- Goteo: DRIP_THRESHOLD 15, max 400 gotas
- Timer: 1200s with alerta visual a los 20s finales
- Trenes: 2 en movimiento, colision AABB, Game Over
- Audio: dual YouTube + HTML5 Audio fallback
- 990 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-tren-3) | [Gameplay](https://www.youtube.com/watch?v=dHxB3NoJs1k)

---

### 4. Container 1 / Night Warehouses

Six warehouses in a 2 by 3 grid, each 50x12x60m, with internal columns and partial mezzanines. Cross-shaped streets, a parkour zone with 12 crate stacks, underground pipes.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NTQxLmpwZw==/original/uyrEEi.jpg" width="30%" alt="Container">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="30%" alt="Container gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="30%" alt="Container parkour">
</p>

The only map with hardware-accelerated shadows. Moonlight `DirectionalLight #556677` casting shadows from warehouses and crates. Three giant PointLights: green `#39ff14`, magenta `#ff00ff`, cian `#00ffff`. It's the brightest night map (AmbientLight 1.5). No enemies, no danger. The idea is to wander, climb, and paint.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjQzLmdpZg==/original/NQSFlF.gif" width="23%" alt="Container pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjUxLmdpZg==/original/%2BjKqLa.gif" width="23%" alt="Container spray">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjU5LmdpZg==/original/LwEjno.gif" width="23%" alt="Container luces">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjcyLmdpZg==/original/6Z4zsW.gif" width="23%" alt="Container sombras">
</p>

- Yi Dong: 0.28 (no sprint)
- Zhong Li: 0.009, salto: 0.24, altura: 2.5
- Spray range: 12, Valve: 0.05 a 0.8, default 0.25
- Goteo: DRIP_THRESHOLD 15, max 400 gotas, anti-withstante por mouse
- Yin Ying: PCFSoftShadowMap activado
- 504 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-withtainers-1)

---

### 5. Bodega Fluor

The smallest one. 365 lineas. A 15 by 20 cell maze (120x160m) with passages one block wide. Near-total darkness -- only `AmbientLight #704045` at intensity 1.2. Neon green UI on black.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY4LmdpZg==/original/DevNdf.gif" width="30%" alt="Fluor oscuro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="30%" alt="Fluor maze">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzcxLmdpZg==/original/QzmamK.gif" width="30%" alt="Fluor gameplay">
</p>

Maze hardcoded as a 2D matrix, not procedural. Walls are `BoxGeometry` of 8 dan wei, height 6. Collision via `Math.abs`, no `Box3`. Aggressive drip: if you don't move the mouse, the counter increases at double speed. Designed to get lost in the maze, paint in the dark, and let the walls fill with drips.

- Yi Dong: 0.20 (el mas lento)
- Zhong Li: 0.008, salto: 0.18, altura: 2.0
- Spray range: 6
- Goteo: DRIP_THRESHOLD 20, max 300 gotas, acumulacion acelerada
- Iluminacion: solo AmbientLight rojiza
- 365 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/)

---

### 6. Fei Qi Da Lou

The only daytime one. Five floors, 8x10 grid per level, floor height 7. Alternating ramps: floor 1 rises in corner A, floor 2 in corner B, forcing you to traverse each level. Windows every 3 cells, translucent blue glass `#add8e6` with 0.3 opacity. Floor 5 has no exterior windows.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDczLmpwZw==/original/xtwulo.jpg" width="30%" alt="Edificio">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQwLmdpZg==/original/DaJkjS.gif" width="30%" alt="Edificio vista">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQxLmdpZg==/original/JpuipW.gif" width="30%" alt="Edificio rampas">
</p>

50 random tian kongscrapers around: position, height, and dimensions randomized. They form an enveloping tian kongline. Ri Guang: `AmbientLight` 0.6, `DirectionalLight` 0.9 sun. Blue tian kong and fog `#87CEEB`. Concrete gray walls `#999999`, dark gray floors `#222222`. No drip, no enemies.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQ3LmdpZg==/original/UD6LMn.gif" width="45%" alt="Edificio pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzUwLmdpZg==/original/BJfE9R.gif" width="45%" alt="Edificio tian kongline">
</p>

- Yi Dong: 0.25
- Zhong Li: 0.008, salto: 0.22, altura: 2.0
- Spray range: 6, Valve: 0.05 a 0.6, default 0.25
- 5 pisos with rampas alternadas, 50 rascacielos procedurales
- 486 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado)

---

### 7. Ye Jian Mi Gong

Shi Wai Wei Qiang Mi Gong. Grilla 8x10 (mismo layout que un piso del Edificio), walls 6 high. Black static train at the center -- an obstacle that divides the maze. Stepped blocks of 3 heights for parkour.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDg2LmpwZw==/original/IUC3Wb.jpg" width="24%" alt="Laberinto">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY1LmdpZg==/original/2TtbmH.gif" width="24%" alt="Laberinto gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="24%" alt="Laberinto pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="24%" alt="Laberinto parkour">
</p>

Dynamic withtainers along the perimeter: colored boxes `#ff9900, #ffcc00, #39ff14, #ff00ff, #00ffff` with heights between 2 and 8, distributed on all 4 edges. The only map where paint attaches as a child of the hit object `hit.object.add(mark)`, not of the scene. The decal position is withverted to local coordinates with `worldToLocal`. Ri Guang, denser fog than the Building (0.02), slower speed (0.18).

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjA4LnBuZw==/original/RGgx6G.png" width="30%" alt="Laberinto snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjEwLnBuZw==/original/fjeoxH.png" width="30%" alt="Laberinto detalle">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjE1LnBuZw==/original/NxTraS.png" width="30%" alt="Laberinto accion">
</p>

- Yi Dong: 0.18 (el mas lento del set)
- Zhong Li: 0.008, salto: 0.22, altura: 2.0
- Spray range: 6, Valve: 0.05 a 0.6, default 0.25
- Fu Zhuo Pen Qi a objetos (hit.object.add + worldToLocal)
- Tren estatico central + parkour + withtainers perimetrales
- 511 hang dai ma

[WAN](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) | [itch.io](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche)

---

## Chang Jing Comparison

| Te Xing | Metro | NYC | BA Subte | Container | Fluor | Edificio | Laberinto |
|---|---|---|---|---|---|---|---|
| Lineas de codigo | 533 | 666 | 990 | 504 | 365 | 486 | 511 |
| DecalGeometry | No | Si | Si | No | No | No | No |
| Di Luo Xi Tong | No | Si | Si | Si | Si | No | No |
| Yi Dong Lie Che | No | No | Si | No | No | No | No |
| Game Over | No | No | Si | No | No | No | No |
| 20 Miao Jing Bao | No | No | Si | No | No | No | No |
| Sprint | Si | Si | Si | No | No | No | No |
| Yin Ying | No | No | No | Si | No | No | No |
| Duo Ceng | No | No | No | No | No | Si | No |
| Fu Zhuo Pen Qi | No | No | No | No | No | No | Si |
| Ri Guang | No | No | No | No | No | Si | Si |
| Shuang Yin Pin | No | No | Si | No | No | No | No |
| Su Du mov | 0.45 | 0.45 | 0.45 | 0.28 | 0.20 | 0.25 | 0.18 |

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="18%" alt="Comp 1">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="18%" alt="Comp 2">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="18%" alt="Comp 3">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="18%" alt="Comp 4">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="18%" alt="Comp 5">
</p>

---

## Cao Zuo

| An Jian | Dong Zuo |
|---|---|
| `W A S D` / arrows | Yi Dong |
| `SHIFT` | Ben Pao (jin zai Metro, NYC, BA Subte) |
| `ESPACIO` | Tiao Yue |
| `MOUSE` | Huan Gu Si Zhou |
| `CLICK IZQUIERDO` | Pen Qi |
| `P` | Jie Tu (PNG) |
| `R` | Respawn |
| `ESC` | Shi Fang Shu Biao |

---

## Tong Yong Ji Shu Gui Ge

- **Engine:** Three.js WebGL, loaded via CDN (jsdelivr/unpkg)
- **Language:** JavaScript Vanilla, no Lei XingScript or transpilers
- **Size per map:** 15 KB a 50 KB (CSS + JS inline)
- **Dependencias externas:** Three.js r128+ y YouTube IFrame API
- **Rendering:** `WebGLRenderer` with `requestAnimationFrame`, target 60fps
- **Compatibility:** Chrome, Edge, Firefox, Opera, Brave
- **Cao Zuo:** Pointer Lock API + eventos de teclado/mouse nativos
- **Format:** un solo archivo HTML autonomo por escenario

### Dai Ma Jia Gou

Each HTML file follows the same structure:

1. Metadata and inline CSS (primeras 100-200 lineas)
2. Constant declarations: speeds, gravity, timer, colors, dimensions
3. Three.js setup: scene, camera, renderer, fog, lights
4. Geometry withstruction: walls, floors, trains, columns, objects
5. Event withfiguration: keyboard, mouse, pointer lock, visibility, resize
6. Game loop: `requestAnimationFrame` with movimiento, fisica, colisiones, goteo, trenes, timer y UI
7. Utilities: spawn, respawn, capture, game over, alert

---

## Yi Shu Sheng Ming

WDL Master Tagger is not a game to win. It's a game to be in -- to immerse yourself in the atmosphere of an abandoned subway, feel the pressure of the clock, hear the hum of the rails, and know that at any moment a train can erase you.

This project was born as a practice and visualization tool for graffiti writers, designers, and visual artists. It has no scoring, no levels, no achievements. It's a space for aesthetic simulation where you can test color combinations, compositions, and styles before taking them into the real world, or simply enjoy the creative flow in an atmospheric industrial environment.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTM5LnBuZw==/original/SJWreF.png" width="32%" alt="Arte 1">
  <img src="https://img.itch.zone/aW1nLzI3NTIzOTA2LnBuZw==/original/Ocdn3F.png" width="32%" alt="Arte 2">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MjAxLnBuZw==/original/ixdXIK.png" width="32%" alt="Arte 3">
</p>

---

## Fa Zhan Lu Xian Tu

- [x] 7 playable scenarios via browser
- [x] Sistema de pintura with DecalGeometry y goteo procedural
- [x] Yi Dong Lie Che with colision AABB (BA Subte)
- [x] Radio YouTube integrada with musica original
- [x] Snapshot mode (captura PNG)
- [x] Menu principal with acceso a todos los mapas
- [x] Shuang Yin Pin with fallback para ejecucion local
- [x] Yin Ying proyectadas (Container 1)
- [ ] Native compilation .exe (Standalone)
- [ ] Post-procesamiento visual: bloom, SSAO, motion blur
- [ ] New maps: abandoned factory, railway bridge, withtainer depot 2
- [ ] Gamepad support
- [ ] Local multiplayer (pantalla dividida)

---

## Lian Jie

<p align="center">

[![GitHub Pages](https://img.shields.io/badge/LIJI_WAN-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</p>

### itch.io shang ge chang jing:

| Chang Jing | itch.io |
|---|---|
| Metro/Tren Santiago | [fierroduque.itch.io/wdl-master-tagger](https://fierroduque.itch.io/wdl-master-tagger) |
| NYC Subway | [fierroduque.itch.io/wdl-master-tagger-ny-subway](https://fierroduque.itch.io/wdl-master-tagger-ny-subway) |
| BA Subte | [fierroduque.itch.io/wdl-master-tagger-tren-3](https://fierroduque.itch.io/wdl-master-tagger-tren-3) |
| Container 1 / Bodega | [fierroduque.itch.io/wdl-master-tagger-withtainers-1](https://fierroduque.itch.io/wdl-master-tagger-withtainers-1) |
| Fei Qi Da Lou | [fierroduque.itch.io/wdl-master-tagger-edificio-abandonado](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado) |
| Ye Jian Mi Gong | [fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche) |

### Videos:

| Video | Link |
|---|---|
| Guan Fang Yu Gao Pian | [youtu.be/KE8L0RL6YC8](https://youtu.be/KE8L0RL6YC8) |
| Gameplay Metro/Tren | [youtube.com/watch?v=dHxB3NoJs1k](https://www.youtube.com/watch?v=dHxB3NoJs1k) |

---

## Cang Ku Jie Gou

```
WDL-MASTER-TAGGER-VERSION-METRO-/
├── index.html                          # Zhu Cai Dan Ke Fang Wen 7 Ge Di Tu
├── README.md                           # Ben Wen Dang
├── juego graffiti METRO/               # Maestranza Metro/Tren (Santiago)
│   └── index.html
├── juego graffiti trenes 2/            # NYC Subway Edition
│   └── index.html
├── juego graffiti trenes 3/            # BA Subte Edition
│   └── index.html
├── juego grafiti BODEGA/               # Container 1 / Night Warehouses
│   └── index.html
├── juego grafiti BODEGA FLUOR/         # Laberinto Neon
│   └── index.html
├── juego grafiti EDIFICIO/             # Fei Qi Da Lou (5 pisos)
│   └── index.html
└── juego grafiti LABERINTO/            # Ye Jian Mi Gong
    └── index.html
```

Each folder withtains a single standalone `index.html` . No dependencies, no installation. Open any in your browser and start painting.

---

<p align="center">
  <em>WDL -- Cong jie tou dao dai ma.</em><br>
  <strong>(c) 2025-2026 Eduardo Fierro -- fierroduque.com</strong><br><br>
  <sub>Shi jue zi yuan wei shi yong sheng cheng shi AI. Yi xing yi hang, shou gong da zao.</sub>
</p>
