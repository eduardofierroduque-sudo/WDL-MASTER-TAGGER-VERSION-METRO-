<p align="center">
  <img width="800" src="https://img.itch.zone/aW1nLzI3MTIwODUyLnBuZw==/original/YlguIp.png" alt="WDL MASTER TAGGER">
</p>

<div align="center">

# WDL MASTER TAGGER

**Simulador de graffiti en primera persona. HTML5, WebGL, Three.js. JavaScript sin frameworks.**

*No es un juego de disparos. Es un juego de trackear: marcar territorio y dejar tu firma.*

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

[![Jugar Ahora](https://img.shields.io/badge/JUGAR_AHORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</div>

<img width="1920" height="1080" alt="WDL MASTER TAGGER Banner" src="https://github.com/user-attachments/assets/e36704b2-a72d-4af0-9d15-818dddf80608" />

---

## La coleccion -- 7 escenarios jugables desde el navegador

<div align="center">

| # | Escenario | Tipo | Estilo | Jugar |
|---|---|---|---|---|
| 1 | **Maestranza Metro/Tren** | Talleres ferroviarios, Santiago | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) |
| 2 | **NYC Subway** | Metro de Nueva York | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) |
| 3 | **BA Subte** | Subte Buenos Aires | Con peligro | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) |
| 4 | **Container 1** | Astillero industrial | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) |
| 5 | **Bodega Fluor** | Laberinto oscuro | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/) |
| 6 | **Edificio Abandonado** | Rascacielos, 5 pisos | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) |
| 7 | **Laberinto de Noche** | Laberinto exterior amurallado | Libre | [JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) |

</div>

> Todos los mapas incluyen radio integrada con musica producida por Eduardo Fierro, via YouTube IFrame API. Cada mapa es un solo archivo HTML que carga al instante. Sin descargas, sin instalaciones.

---

## Trailer

<p align="center">
  <a href="https://youtu.be/KE8L0RL6YC8">
    <img src="https://img.youtube.com/vi/KE8L0RL6YC8/0.jpg" alt="Trailer WDL MASTER TAGGER" width="600">
  </a>
  <br>
  <a href="https://youtu.be/KE8L0RL6YC8">VER TRAILER EN YOUTUBE</a>
</p>

---

## El motor -- componentes y sistemas

Todo esta escrito en JavaScript Vanilla sobre Three.js r128 o superior, cargado via CDN. No hay bundlers, no hay frameworks, no hay dependencias de npm. Un solo archivo HTML por escenario que contiene todo el CSS, JS y la escena 3D inline. El peso por mapa va de 15 KB a 50 KB.

### Sistema de pintura por DecalGeometry

En los mapas NYC Subway y BA Subte, la pintura se aplica usando `DecalGeometry` de Three.js. Se genera una textura procedural de spray radial sobre un canvas 2D offscreen, usando degradados radiales con distintos niveles de opacidad y dispersion. Esa textura se pasa como `map` a un `MeshBasicMaterial` configurado con `alphaTest: 0.1`, `polygonOffset: true`, `polygonOffsetFactor: -4` y `depthWrite: false`. Esto elimina el Z-fighting entre capas de pintura superpuestas sin necesidad de modificar la geometria de la pared.

El `Raycaster` se lanza desde la posicion de la camara en direccion al centro de la pantalla, con un alcance configurable de 6 a 15 unidades segun el mapa. Si el rayo intersecta una superficie, se instancia un `DecalGeometry` en el punto de impacto, orientado segun la normal de la cara intersectada. El tamano del decal se controla con la valvula (slider en UI).

En el resto de los mapas se usa `CircleGeometry` con `MeshBasicMaterial`, aplicando `renderOrder` incremental y `polygonOffset` con factor variable por capa. Es mas ligero pero no tiene la misma fidelidad de textura de aerosol.

### Sistema de goteo procedural

Cuando el jugador mantiene el spray sobre un mismo punto, un contador interno `dripCounter` se incrementa. Al superar el umbral `DRIP_THRESHOLD` (15 en la mayoria de mapas), el motor genera gotas en la posicion de impacto. Cada gota es un `BoxGeometry` muy fino y alargado, con material semitransparente del mismo color que el trazo activo.

Cada gota tiene propiedades aleatorias generadas al instanciarse: velocidad de caida (`dripSpeed`, entre 0.08 y 0.25 unidades por frame), longitud inicial (`dripLength`, entre 0.05 y 0.3), y un offset lateral aleatorio para evitar que todas las gotas caigan en linea perfecta. La gota se estira progresivamente en el eje Y (`scale.y += dripSpeed * 0.1`) y se desplaza hacia abajo (`position.y -= dripSpeed`). Cuando `scale.y` supera un maximo o la gota sale del rango visible, se elimina del array `activeDrips`.

Hay un limite de gotas activas (300 a 400 segun el mapa). Cuando se alcanza, las gotas mas antiguas se eliminan primero (FIFO). En los mapas Bodega y Bodega Fluor, el contador de goteo se resetea o se ralentiza si el jugador mueve el mouse, simulando que el aerosol se distribuye sobre una superficie mas amplia en lugar de acumularse en un punto.

En Bodega Fluor especificamente, si la distancia recorrida por el mouse entre frames es menor a 0.05 unidades, `dripCounter` incrementa en 2 por frame (acumulacion rapida). Si el mouse se mueve mas, solo incrementa en 0.5.

### Trenes en movimiento y colision AABB

Exclusivo del mapa BA Subte. Hay dos formaciones que circulan por vias laterales fijas (X = -100 y X = +100). Cada formacion tiene 4 coches ensamblados con `BoxGeometry`, totalizando aproximadamente 300 unidades de largo. Llevan un `PointLight` frontal que actua como faro (`color: #ffeecc, intensity: 3, distance: 400`), visible a traves de la niebla.

La logica de movimiento es lineal y determinista: el tren 1 avanza en direccion +Z desde Z = -550 hasta desaparecer en Z > 650. El tren 2 avanza en direccion -Z desde Z = +550 hasta Z < -650. La velocidad es de 3.0 unidades por frame (a 60fps, unos 180 metros virtuales por segundo). Al desaparecer, se programa un respawn con `setTimeout`: tren 1 cada 120 segundos exactos, tren 2 cada 120 segundos pero desfasado (inicia 75s despues del primero). El primer tren aparece a los 15 segundos de iniciada la partida, el segundo a los 75 segundos.

La deteccion de colision es por AABB (Axis-Aligned Bounding Box). No se usa `Box3` de Three.js para esto, sino una comparacion directa de rangos: si el rango Z del tren (posicion Z mas/menos mitad del largo) se solapa con el rango Z del jugador, y ambos comparten el mismo eje X de via, hay colision. La pantalla se pone en negro, aparece un overlay rojo con el texto ATROPELLADO POR EL TREN en tipografia sans-serif, y un enlace de recarga. Sin respawn, sin continuar.

En los ultimos 20 segundos del timer, el fondo de la escena (`scene.background`) comienza a oscilar entre negro y rojo oscuro, la niebla `FogExp2` muta su color a `#330000`, y un overlay HTML con el texto ALERTA DE SEGURIDAD -- ABANDONE EL AREA INMEDIATAMENTE titila sobre el canvas. Esto esta implementado con `setInterval` a 500ms que alterna clases CSS y modifica las propiedades de color de la escena en tiempo real.

### Sistema de audio y radio

Todos los mapas integran la YouTube IFrame API. Se crea un elemento iframe oculto que carga el reproductor de YouTube sin interfaz y comienza a reproducir una playlist con musica original producida por Eduardo Fierro.

En el mapa BA Subte hay un sistema dual de audio. Cuando el HTML se carga desde un servidor web (HTTP/HTTPS), se usa la YouTube IFrame API normalmente. Pero cuando se abre desde `file://` (doble clic local), el navegador bloquea la IFrame API de YouTube por politicas de mismo origen. En ese caso, el codigo conmuta automaticamente a streams de audio HTML5 usando el elemento `<audio>` nativo, con URLs directas a archivos MP3. Esto permite que el juego sea funcional incluso ejecutado localmente sin servidor.

La deteccion se hace verificando `window.location.protocol`: si es `file:`, se activa el fallback de audio local. Si es `http:` o `https:`, se usa YouTube. El volumen del reproductor de YouTube se ajusta via `player.setVolume()` y el elemento de audio nativo via `audio.volume`.

### Snapshot mode -- captura de pantalla

Al presionar la tecla `P`, se ejecuta `renderer.render(scene, camera)` para asegurar que el buffer este actualizado, luego se extrae el contenido del canvas con `canvas.toDataURL('image/png')`. Se crea un elemento ancla temporal con `download = 'wdl-snapshot.png'`, se le asigna el data URL como `href` y se dispara un clic programatico. El resultado es un PNG a la resolucion nativa del canvas, descargado directamente.

### Renderizado y niebla

Todos los mapas usan `FogExp2` de Three.js, que implementa niebla exponencial cuadratica: la visibilidad decae segun `exp(-density * distance^2)`. La densidad varia entre mapas:

| Mapa | Densidad | Color niebla |
|---|---|---|
| Metro | 0.008 | #020202 |
| NYC Subway | 0.012 | #020202 |
| BA Subte | 0.008 | #020202 (cambia a #330000 en alerta) |
| Bodega | 0.004 | #0a0a0b |
| Bodega Fluor | 0.03 | #020202 |
| Edificio | 0.01 | #87CEEB (cielo) |
| Laberinto | 0.02 | #87CEEB (cielo) |

NYC tiene la niebla mas densa (0.012) para acentuar el ambiente cerrado de tunel. Bodega Fluor tiene 0.03, casi opaca a 50 metros. Bodega tiene la mas ligera (0.004), permitiendo ver los galpones a distancia. Edificio y Laberinto usan color azul cielo por ser mapas diurnos.

### Iluminacion por escenario

Cada mapa tiene una configuracion de luces pensada para su ambientacion:

- **Metro:** `AmbientLight(0xffffff, 0.3)` base, `DirectionalLight(0xffffff, 0.4)`, `PointLight(#ff3300, 2, 80)` rojas en los tuneles.
- **NYC Subway:** `AmbientLight(0xffffff, 0.08)` minimo, `PointLight(#dcf0f7, 0.15, 200)` frias en estacion, `PointLight(#ffb84d, 0.1, 180)` calidas en tubos.
- **BA Subte:** `AmbientLight(0xffffff, 0.08)`, `PointLight(#ffddaa, 0.2, 200)` calidas, `PointLight(#ffb84d, 0.1, 180)` en intersecciones.
- **Bodega:** `AmbientLight(0xffffff, 1.5)`, `DirectionalLight(#556677, 1.5)` luna, `PointLight` RGB (verde, magenta, cian) + sombras `PCFSoftShadowMap`.
- **Bodega Fluor:** Solo `AmbientLight(#704045, 1.2)`. Una unica luz rojiza. Es el mapa mas oscuro.
- **Edificio:** `AmbientLight(0xffffff, 0.6)`, `DirectionalLight(0xffffff, 0.9)` sol diurno.
- **Laberinto:** `AmbientLight(0xffffff, 0.7)`, `DirectionalLight(0xffffff, 0.8)` sol diurno.

### Movimiento del jugador y fisica

El movimiento en primera persona esta implementado sin usar `PointerLockControls` de Three.js. La camara se rota directamente segun `movementX` y `movementY` del evento `mousemove`. El pitch (Y) se clampanea entre -PI/2 y PI/2.

El movimiento WASD es relativo a la orientacion de la camara. Se calcula un vector forward a partir de `camera.rotation.y` usando `sin/cos`, y un vector right perpendicular. El salto usa `playerVelocity.y` que decrece por gravedad cada frame. Una comprobacion de piso mantiene al jugador en Y = playerHeight.

Parametros por mapa:

| Mapa | Velocidad | Sprint | Gravedad | Salto | Altura |
|---|---|---|---|---|---|
| Metro | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| NYC | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| BA Subte | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| Bodega | 0.28 | -- | 0.009 | 0.24 | 2.5 |
| Bodega Fluor | 0.20 | -- | 0.008 | 0.18 | 2.0 |
| Edificio | 0.25 | -- | 0.008 | 0.22 | 2.0 |
| Laberinto | 0.18 | -- | 0.008 | 0.22 | 2.0 |

Los mapas de tren comparten parametros agiles con sprint. Los demas son mas lentos, pensados para exploracion pausada.

### Deteccion de colisiones con el entorno

Las colisiones contra paredes y objetos se manejan con `Box3` de Three.js. Cada geometria estatica recibe un bounding box con `computeBoundingBox()`. Antes de aplicar el movimiento del jugador, se crea un `Box3` temporal alrededor de la posicion futura y se prueba con `intersectsBox()` contra todos los colisionadores. Si hay interseccion, el movimiento en ese eje se cancela.

En Bodega Fluor, la deteccion es mas simple: `Math.abs` contra las coordenadas del grid del laberinto. En BA Subte, las paredes del laberinto son cientos de `BoxGeometry` individuales, cada una con su `Box3`.

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

## Los mapas

<img width="144" height="68" alt="metro1" src="https://github.com/user-attachments/assets/9ae73a9b-e3a8-447a-b50f-269e039a506a" />
<img width="144" height="68" alt="metro2" src="https://github.com/user-attachments/assets/62368dac-d8d3-49ea-9a60-97818bd30655" />
<img width="144" height="68" alt="metro3" src="https://github.com/user-attachments/assets/65f23e73-9763-432e-983f-bdd13f1a3b4b" />
<img width="144" height="68" alt="metro4" src="https://github.com/user-attachments/assets/5f0d1497-100b-4477-9db0-f27bf182eeca" />
<img width="144" height="68" alt="metro5" src="https://github.com/user-attachments/assets/493d1c9b-94b0-4f5c-8f58-f91cd6acfef9" />

---

### 1. Maestranza Metro/Tren -- Santiago, Talleres L2

El original. El que empezo todo. Lo escribi pensando en los talleres de la Linea 2 del Metro de Santiago, un hangar industrial enorme con formaciones NS-74 estacionadas en via muerta. Son 22 trenes azules `#00a9e0` con cabina, vidrios, acoples metalicos y luces de posicion.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="30%" alt="Metro tren">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA4LmdpZg==/original/aQxVgp.gif" width="30%" alt="Metro pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA5LmdpZg==/original/5dwhdf.gif" width="30%" alt="Metro tunel">
</p>

El mapa es un hangar de 400 por 600 metros con altura 50. Tres tuneles hacia los lados, andenes elevados, columnas de hierro cada 40 metros y unas 40 cajas de repuestos. Las luces de los tuneles son rojas `#ff3300`, intensidad 2, alcance 80. La niebla es `FogExp2(0x020202, 0.008)`. La pintura usa `CircleGeometry` con `MeshBasicMaterial`. Sin sistema de goteo -- esta version es anterior a ese desarrollo. Sin trenes en movimiento.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTE0LnBuZw==/original/xtXMwi.png" width="48%" alt="Metro snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTIxLnBuZw==/original/yQMlWG.png" width="48%" alt="Metro accion">
</p>

El timer marca 1200 segundos. Al llegar a cero hace `location.reload()`. Si caes por debajo de Y = -40, respawn automatico.

- Movimiento: 0.45 caminando, 0.75 corriendo (Shift)
- Gravedad: 0.012, salto: 0.32, altura jugador: 2.4
- Alcance del spray: 15 unidades
- Valvula: 0.1 a 1.4, paso 0.05, default 0.4
- 533 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger)

---

### 2. NYC Subway -- New York City

La version neoyorquina. Estacion central de 400 por 100 metros con cuatro vias que se extienden en tuneles hacia el norte y el sur. Pasillos transversales cada 120 metros. Paredes de azulejo blanco `#dddddd`, columnas de acero verde NYC `#123524`. Tuneles en tubo cerrado con techo, piso y paredes curvas.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTMyLnBuZw==/original/aR5DO4.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTMwLnBuZw==/original/9Uouzu.png" width="30%" alt="NYC Subway">
</p>

14 trenes estilo NYC estacionados: metal plateado, techo negro, luces LED rojas en la cola. Los trenes son estaticos pero la ambientacion es tensa: oscuridad casi total, luces minimas, niebla densa (0.012). Primer mapa en implementar `DecalGeometry` para la pintura y el sistema de goteo completo. Valvula de 0.1 a 5.0, permitiendo desde tags finisimos hasta throw-ups que cubren un tren en segundos.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="24%" alt="NYC interior">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="24%" alt="NYC pintura">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="24%" alt="NYC spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="24%" alt="NYC gameplay">
</p>

- Movimiento: 0.45 / 0.75 (sprint)
- Gravedad: 0.012, salto: 0.32, altura: 2.4
- Alcance del spray: 15, Valvula: 0.1 a 5.0, default 1.0
- Goteo: DRIP_THRESHOLD 15, max 400 gotas activas
- 666 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-ny-subway)

---

### 3. BA Subte -- Buenos Aires (el mas completo)

990 lineas. El mapa mas grande y mas trabajado. Laberinto en grilla de 11 por 11 bloques, 1100 por 1100 metros. Bloques de 70m con pasillos de 30m. Estacion central vacia de 100 por 300 metros. Paredes beige crema `#e6dec3`, columnas de hierro oscuro `#2a302d`, paneles publicitarios en colores.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzEyLnBuZw==/original/3mj0P3.png" width="24%" alt="BA Subte">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="24%" alt="BA Subte trenes">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTg0LnBuZw==/original/EKymke.png" width="24%" alt="BA Subte laberinto">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzk2LnBuZw==/original/XvZrkX.png" width="24%" alt="BA Subte gameplay">
</p>

Unico mapa con trenes en movimiento. Dos formaciones de 4 coches con faros frontales visibles a traves de la niebla. Circulan por vias fijas en X = -100 y X = +100. Si te quedas en la via, Game Over sin respawn. En los ultimos 20 segundos, la pantalla pulsa en rojo, la niebla se vuelve sangre y un cartel de alerta titila.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="30%" alt="BA Subte tren movil">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="30%" alt="BA Subte game over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="30%" alt="BA Subte menu">
</p>

Menu bilingue ES/EN con controles, mision y advertencias. Audio dual (YouTube en servidor, HTML5 Audio en local). Manejo avanzado de eventos: prevencion de menu contextual, reseteo en mouseleave/blur, ignorancia del primer mousemove.

- Movimiento: 0.45 / 0.75 (sprint)
- Gravedad: 0.012, salto: 0.32, altura: 2.4
- Alcance del spray: 15, Valvula: 0.1 a 5.0, default 1.0
- Goteo: DRIP_THRESHOLD 15, max 400 gotas
- Timer: 1200s con alerta visual a los 20s finales
- Trenes: 2 en movimiento, colision AABB, Game Over
- Audio: dual YouTube + HTML5 Audio fallback
- 990 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-tren-3) | [Gameplay](https://www.youtube.com/watch?v=dHxB3NoJs1k)

---

### 4. Container 1 / Bodegas de Noche

Seis galpones en grilla 2 por 3, cada uno 50x12x60m, con columnas internas y entrepisos parciales. Calles en cruz, zona de parkour con 12 pilas de cajas, tuberias subterraneas.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NTQxLmpwZw==/original/uyrEEi.jpg" width="30%" alt="Container">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="30%" alt="Container gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="30%" alt="Container parkour">
</p>

Unico mapa con sombras activadas por hardware. Luna `DirectionalLight #556677` proyectando sombras de galpones y cajas. Tres PointLights gigantes: verde `#39ff14`, magenta `#ff00ff`, cian `#00ffff`. Es el mapa nocturno mas luminoso (AmbientLight 1.5). Sin enemigos, sin peligro. La idea es recorrer, trepar y pintar.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjQzLmdpZg==/original/NQSFlF.gif" width="23%" alt="Container pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjUxLmdpZg==/original/%2BjKqLa.gif" width="23%" alt="Container spray">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjU5LmdpZg==/original/LwEjno.gif" width="23%" alt="Container luces">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjcyLmdpZg==/original/6Z4zsW.gif" width="23%" alt="Container sombras">
</p>

- Movimiento: 0.28 (sin sprint)
- Gravedad: 0.009, salto: 0.24, altura: 2.5
- Alcance del spray: 12, Valvula: 0.05 a 0.8, default 0.25
- Goteo: DRIP_THRESHOLD 15, max 400 gotas, anti-constante por mouse
- Sombras: PCFSoftShadowMap activado
- 504 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-containers-1)

---

### 5. Bodega Fluor

El mas chico. 365 lineas. Laberinto de 15 por 20 celdas (120x160m) con pasillos de un bloque de ancho. Oscuridad casi total -- solo `AmbientLight #704045` a intensidad 1.2. UI verde neon sobre negro.

Laberinto hardcodeado como matriz 2D, no procedural. Paredes `BoxGeometry` de 8 unidades, altura 6. Colision por `Math.abs`, sin `Box3`.

Goteo agresivo: si no moves el mouse, el contador sube al doble de velocidad. Disenado para perderse en el laberinto, pintar en la oscuridad y que las paredes se llenen de chorreados.

- Movimiento: 0.20 (el mas lento)
- Gravedad: 0.008, salto: 0.18, altura: 2.0
- Alcance del spray: 6
- Goteo: DRIP_THRESHOLD 20, max 300 gotas, acumulacion acelerada
- Iluminacion: solo AmbientLight rojiza
- 365 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/)

---

### 6. Edificio Abandonado

El unico de dia. Cinco pisos, grilla 8x10 por planta, altura de piso 7. Rampas alternadas: piso 1 sube en esquina A, piso 2 en esquina B, forzando a recorrer cada planta. Ventanales cada 3 celdas, vidrio azul translucido `#add8e6` con opacidad 0.3. Piso 5 sin ventanas exteriores.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDczLmpwZw==/original/xtwulo.jpg" width="30%" alt="Edificio">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQwLmdpZg==/original/DaJkjS.gif" width="30%" alt="Edificio vista">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQxLmdpZg==/original/JpuipW.gif" width="30%" alt="Edificio rampas">
</p>

50 rascacielos aleatorios alrededor: posicion, altura y dimensiones al azar. Forman un skyline envolvente. Luz de dia: `AmbientLight` 0.6, `DirectionalLight` 0.9 sol. Cielo y niebla azules `#87CEEB`. Paredes gris hormigon `#999999`, pisos gris oscuro `#222222`. Sin goteo, sin enemigos.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQ3LmdpZg==/original/UD6LMn.gif" width="45%" alt="Edificio pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzUwLmdpZg==/original/BJfE9R.gif" width="45%" alt="Edificio skyline">
</p>

- Movimiento: 0.25
- Gravedad: 0.008, salto: 0.22, altura: 2.0
- Alcance del spray: 6, Valvula: 0.05 a 0.6, default 0.25
- 5 pisos con rampas alternadas, 50 rascacielos procedurales
- 486 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado)

---

### 7. Laberinto de Noche

Laberinto exterior amurallado. Grilla 8x10 (mismo layout que un piso del Edificio), muros altura 6. Tren estatico negro al centro -- obstaculo que divide el laberinto. Bloques escalonados de 3 alturas para parkour.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDg2LmpwZw==/original/IUC3Wb.jpg" width="24%" alt="Laberinto">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY1LmdpZg==/original/2TtbmH.gif" width="24%" alt="Laberinto gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="24%" alt="Laberinto pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="24%" alt="Laberinto parkour">
</p>

Containers dinamicos en el perimetro: cajas de colores `#ff9900, #ffcc00, #39ff14, #ff00ff, #00ffff` con alturas entre 2 y 8, distribuidas en los 4 bordes. Unico mapa donde la pintura se adhiere como hijo del objeto `hit.object.add(mark)`, no de la escena. La posicion del decal se convierte a coordenadas locales con `worldToLocal`. Luz de dia, niebla mas densa que Edificio (0.02), velocidad mas lenta (0.18).

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjA4LnBuZw==/original/RGgx6G.png" width="30%" alt="Laberinto snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjEwLnBuZw==/original/fjeoxH.png" width="30%" alt="Laberinto detalle">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjE1LnBuZw==/original/NxTraS.png" width="30%" alt="Laberinto accion">
</p>

- Movimiento: 0.18 (el mas lento del set)
- Gravedad: 0.008, salto: 0.22, altura: 2.0
- Alcance del spray: 6, Valvula: 0.05 a 0.6, default 0.25
- Pintura adherida a objetos (hit.object.add + worldToLocal)
- Tren estatico central + parkour + containers perimetrales
- 511 lineas de codigo

[JUGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) | [itch.io](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche)

---

## Comparativa de escenarios

| Caracteristica | Metro | NYC | BA Subte | Container | Fluor | Edificio | Laberinto |
|---|---|---|---|---|---|---|---|
| Lineas de codigo | 533 | 666 | 990 | 504 | 365 | 486 | 511 |
| DecalGeometry | No | Si | Si | No | No | No | No |
| Sistema goteo | No | Si | Si | Si | Si | No | No |
| Trenes en movimiento | No | No | Si | No | No | No | No |
| Game Over | No | No | Si | No | No | No | No |
| Alerta 20s | No | No | Si | No | No | No | No |
| Sprint | Si | Si | Si | No | No | No | No |
| Sombras | No | No | No | Si | No | No | No |
| Multiples pisos | No | No | No | No | No | Si | No |
| Pintura adherida | No | No | No | No | No | No | Si |
| Luz de dia | No | No | No | No | No | Si | Si |
| Audio dual | No | No | Si | No | No | No | No |
| Velocidad mov | 0.45 | 0.45 | 0.45 | 0.28 | 0.20 | 0.25 | 0.18 |

---

## Controles

| Tecla | Accion |
|---|---|
| `W A S D` / flechas | Movimiento |
| `SHIFT` | Correr (solo en Metro, NYC, BA Subte) |
| `ESPACIO` | Saltar |
| `MOUSE` | Mirar alrededor |
| `CLICK IZQUIERDO` | Pintar spray |
| `P` | Captura de pantalla (PNG) |
| `R` | Respawn |
| `ESC` | Soltar puntero |

---

## Especificaciones tecnicas generales

- **Motor:** Three.js WebGL, cargado via CDN (jsdelivr/unpkg)
- **Lenguaje:** JavaScript Vanilla, sin TypeScript ni transpiladores
- **Peso por mapa:** 15 KB a 50 KB (CSS + JS inline)
- **Dependencias externas:** Three.js r128+ y YouTube IFrame API
- **Renderizado:** `WebGLRenderer` con `requestAnimationFrame`, target 60fps
- **Compatibilidad:** Chrome, Edge, Firefox, Opera, Brave
- **Controles:** Pointer Lock API + eventos de teclado/mouse nativos
- **Formato:** un solo archivo HTML autonomo por escenario

### Arquitectura del codigo

Cada archivo HTML sigue la misma estructura:

1. Metadatos y CSS inline (primeras 100-200 lineas)
2. Declaracion de constantes: velocidades, gravedad, timer, colores, dimensiones
3. Setup de Three.js: escena, camara, renderer, niebla, luces
4. Construccion de geometria: paredes, pisos, trenes, columnas, objetos
5. Configuracion de eventos: teclado, mouse, pointer lock, visibilidad, resize
6. Game loop: `requestAnimationFrame` con movimiento, fisica, colisiones, goteo, trenes, timer y UI
7. Utilidades: spawn, respawn, captura, game over, alerta

---

## Fundamento artistico

WDL Master Tagger no es un juego para ganar. Es un juego para estar -- para meterse en la atmosfera de un subte abandonado, sentir la presion del reloj, escuchar el zumbido de los rieles y saber que en cualquier momento un tren te puede borrar.

Este proyecto nace como una herramienta de practica y visualizacion para escritores de graffiti, disenadores y artistas visuales. No tiene scoring, no tiene niveles, no tiene logros. Es un espacio de simulacion estetica donde probar combinaciones de colores, composiciones y estilos antes de llevarlos al mundo real, o simplemente disfrutar del flujo creativo en un ambiente industrial atmosferico.

---

## Hoja de ruta

- [x] 7 escenarios jugables via navegador
- [x] Sistema de pintura con DecalGeometry y goteo procedural
- [x] Trenes en movimiento con colision AABB (BA Subte)
- [x] Radio YouTube integrada con musica original
- [x] Snapshot mode (captura PNG)
- [x] Menu principal con acceso a todos los mapas
- [x] Audio dual con fallback para ejecucion local
- [x] Sombras proyectadas (Container 1)
- [ ] Compilacion nativa .exe (Standalone)
- [ ] Post-procesamiento visual: bloom, SSAO, motion blur
- [ ] Nuevos mapas: fabrica abandonada, puente ferroviario, deposito containers 2
- [ ] Soporte para gamepad
- [ ] Multijugador local (pantalla dividida)

---

## Enlaces

<p align="center">

[![GitHub Pages](https://img.shields.io/badge/JUGAR_AHORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

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

### Videos:

| Video | Link |
|---|---|
| Trailer Oficial | [youtu.be/KE8L0RL6YC8](https://youtu.be/KE8L0RL6YC8) |
| Gameplay Metro/Tren | [youtube.com/watch?v=dHxB3NoJs1k](https://www.youtube.com/watch?v=dHxB3NoJs1k) |

---

## Estructura del repositorio

```
WDL-MASTER-TAGGER-VERSION-METRO-/
├── index.html                          # Menu principal con acceso a los 7 mapas
├── README.md                           # Este documento
├── juego graffiti METRO/               # Maestranza Metro/Tren (Santiago)
│   └── index.html
├── juego graffiti trenes 2/            # NYC Subway Edition
│   └── index.html
├── juego graffiti trenes 3/            # BA Subte Edition
│   └── index.html
├── juego grafiti BODEGA/               # Container 1 / Bodegas de Noche
│   └── index.html
├── juego grafiti BODEGA FLUOR/         # Laberinto Neon
│   └── index.html
├── juego grafiti EDIFICIO/             # Edificio Abandonado (5 pisos)
│   └── index.html
└── juego grafiti LABERINTO/            # Laberinto de Noche
    └── index.html
```

Cada carpeta contiene un unico `index.html` autonomo. Sin dependencias, sin instalacion. Abri cualquiera en tu navegador y empeza a pintar.

---

<p align="center">
  <em>WDL -- De la calle al codigo.</em><br>
  <strong>(c) 2025-2026 Eduardo Fierro -- fierroduque.com</strong><br><br>
  <sub>No se utilizo IA generativa en la creacion de assets visuales. Hecho a mano, linea por linea.</sub>
</p>
