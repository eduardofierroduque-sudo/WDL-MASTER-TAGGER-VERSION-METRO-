<p align="center">
  <img width="800" src="https://img.itch.zone/aW1nLzI3MTIwODUyLnBuZw==/original/YlguIp.png" alt="WDL MASTER TAGGER">
</p>

<div align="center">

# WDL MASTER TAGGER

**Simulateur de graffiti en vue subjective. HTML5, WebGL, Three.js. JavaScript pur.**

*Ce n'est pas un jeu de tir. C'est un jeu de marquage : avecquis ton territoire et laisse ta signature.*

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

[![Jouer](https://img.shields.io/badge/JOUER-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</div>

<img width="1920" height="1080" alt="WDL MASTER TAGGER Banner" src="https://github.com/user-attachments/assets/e36704b2-a72d-4af0-9d15-818dddf80608" />

---

## La Collection -- 7 scenarios jouables depuis le navigateur

<div align="center">

| # | Scenario | Type | Style | Jugar |
|---|---|---|---|---|
| 1 | **Maestranza Metro/Tren** | Ateliers ferroviaires, Santiago | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) |
| 2 | **NYC Subway** | Metro de New York | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) |
| 3 | **BA Subte** | Metro Buenos Aires | Danger | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) |
| 4 | **Container 1** | Chantier naval | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) |
| 5 | **Bodega Fluor** | Labyrinthe obscur | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/) |
| 6 | **Batiment Abandonne** | Gratte-ciel, 5 etages | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) |
| 7 | **Labyrinthe de Nuit** | Labyrinthe exterieur | Libre | [JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) |

</div>

> Toutes les cartes integrent une radio avec la musique d'Eduardo Fierro, via l'API YouTube IFrame. Chaque carte est un seul fichier HTML a chargement instantane. Sans telechargement, sans installation.

---

## Trailer

<p align="center">
  <a href="https://youtu.be/KE8L0RL6YC8">
    <img src="https://img.youtube.com/vi/KE8L0RL6YC8/0.jpg" alt="Trailer WDL MASTER TAGGER" width="600">
  </a>
  <br>
  <a href="https://youtu.be/KE8L0RL6YC8">VOIR LE TRAILER</a>
</p>

---

## Le Moteur -- composants et systemes

Tout est ecrit en JavaScript Vanilla sur Three.js r128+, charge via CDN. Sans bundler, sans framework, sans dependance npm. Un seul fichier HTML par scenario avectenant tout le CSS, le JS et la scene 3D inline. Poids par carte : de 15 Ko a 50 Ko.

### Systeme de peinture par DecalGeometry

Sur les cartes NYC Subway et BA Subte, la peinture est appliquee avec `DecalGeometry` de Three.js. Une texture procedurale de spray radial est generee sur un canvas 2D hors ecran, avec des degradEs radiaux a differents niveaux d'opacite et de dispersion. Cette texture est passee comme `map` a un `MeshBasicMaterial` avecfigure avec `alphaTest: 0.1`, `polygonOffset: true`, `polygonOffsetFactor: -4` y `depthWrite: false`. Cela elimine le Z-fighting entre les couches de peinture superposees sans modifier la geometrie du mur.

El `Raycaster` est lance depuis la camera vers le centre de l'ecran, avec une portee de 6 a 15 unites selon la carte. Si le rayon touche une surface, un `DecalGeometry` est place au point d'impact, oriente selon la normale de la face touchee. La taille du decal est avectrolee par la valve (slider en UI).

Sur les autres cartes on utilise `CircleGeometry` avec `MeshBasicMaterial`, en appliquant `renderOrder` incremental et `polygonOffset` avec facteur variable par couche. C'est plus leger mais sans la meme fidelite de texture aerosol.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="32%" alt="Decal spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="32%" alt="Decal example">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="32%" alt="Decal result">
</p>

### Systeme de gouttes procedurales

Quand le joueur maintient le spray au meme endroit, un compteur interne `dripCounter` s'incremente. Au-dela du seuil `DRIP_THRESHOLD` (15 sur la plupart des cartes), le moteur genere des gouttes au point d'impact. Chaque goutte est un `BoxGeometry` tres fin et allonge, avec un materiau semi-transparent de la couleur du trait actif.

Chaque goutte a des proprietes aleatoires : vitesse de chute (`dripSpeed`, entre 0.08 et 0.25 unites par frame), longueur initiale (`dripLength`, entre 0.05 et 0.3), et un decalage lateral aleatoire. La goutte s'etire progressivement sur l'axe Y (`scale.y += dripSpeed * 0.1`) et descend (`position.y -= dripSpeed`). Cuando `scale.y` depasse un max ou sort du champ, elle est retiree du tableau `activeDrips`.

Il y a une limite de gouttes actives (300 a 400 selon la carte). Quand elle est atteinte, les plus anciennes sont retirees d'abord (FIFO). Sur Bodega et Bodega Fluor, le compteur de gouttes se reinitialise ou ralentit si la souris bouge, simulant la dispersion de l'aerosol.

Specifiquement sur Bodega Fluor, si la distance souris entre frames est < 0.05 unites, `dripCounter` incremente de 2 par frame (accumulation rapide). Si la souris bouge plus, incremente seulement de 0.5.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzA0LmdpZg==/original/HdS8d7.gif" width="24%" alt="Drip system">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="24%" alt="Drip detail">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzk5LmdpZg==/original/5%2BWVx7.gif" width="24%" alt="Drip paint">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="24%" alt="Drip result">
</p>

### Trains en mouvement et collision AABB

Exclusif a BA Subte. Deux rames circulent sur des voies laterales fixes (X = -100 y X = +100). Chaque rame a 4 voitures assemblees avec `BoxGeometry`, totalisant environ 300 unites de long. Elles portent un `PointLight` phare frontal (`color: #ffeecc, intensity: 3, distance: 400`), visible a travers le brouillard.

Le mouvement est lineaire : le train 1 avance en +Z de Z=-550 jusqu'a disparaitre a Z > 650. Le train 2 avance en -Z de Z=+550 jusqu'a Z < -650. Vitesse : 3.0 unites par frame (a 60fps, environ 180 m/s virtuels). A la disparition, un respawn est programme avec `setTimeout`: train 1 chaque 120s, train 2 chaque 120s decale (demarre 75s apres le premier). Train 1 apparait a 15s, train 2 a 75s.

Detection de collision par AABB (Axis-Aligned Bounding Box). On n'utilise pas `Box3` Three.js mais une comparaison directe : si la plage Z du train (position Z +/- moitie longueur) chevauche celle du joueur sur le meme axe X, collision. Ecran noir, overlay rouge +-PERCUTE PAR LE TRAIN-+ en sans-serif, lien de rechargement. Pas de respawn.

Dans les 20 dernieres seavecdes, le fond de la scene (`scene.background`) oscille entre noir et rouge sombre, le brouillard `FogExp2` passe au `#330000`, et un overlay HTML -+ALERTE SECURITE -- EVACUEZ LA ZONE-+ clignote. Implemente avec `setInterval` a 500ms qui alterne des classes CSS et modifie les couleurs de la scene.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="32%" alt="Tren moving">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="32%" alt="Game Over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="32%" alt="Alerta roja">
</p>

### Systeme audio et radio

Toutes les cartes integrent l'API YouTube IFrame. Un iframe cache charge le player YouTube et lance une playlist avec la musique d'Eduardo Fierro.

BA Subte a un systeme audio dual. Quand le HTML est charge depuis un serveur (HTTP/HTTPS), l'API YouTube est utilisee. Mais ouvert depuis `file://` (un double-clic local), le navigateur bloque YouTube. Le code bascule sur des streams HTML5 avec l'element `<audio>` natif, avec des URLs MP3 directes. Le jeu fonctionne meme en local sans serveur.

Detection par verification de `window.location.protocol`: si es `file:`, activation du fallback audio local. Si es `http:` o `https:`, YouTube est utilise. Volume via `player.setVolume()` et l'element audio natif via `audio.volume`.

### Mode Snapshot -- capture d'ecran

En appuyant sur `P`, est appele `renderer.render(scene, camera)` pour garantir le buffer a jour, puis extraction du canvas avec `canvas.toDataURL('image/png')`. Un element temporaire est cree avec `download = 'wdl-snapshot.png'`, la data URL est assignee comme `href` et un clic programme est declenche. Resultat : PNG a la resolution native, telecharge directement.

### Rendu et brouillard

Toutes les cartes utilisent `FogExp2` de Three.js, brouillard exponentiel quadratique : visibilite decroit selon `exp(-density * distance^2)`. Densite par carte :

| Mapa | Densidad | Couleur brouillard |
|---|---|---|
| Metro | 0.008 | #020202 |
| NYC Subway | 0.012 | #020202 |
| BA Subte | 0.008 | #020202 (passe au #330000 en alerte) |
| Bodega | 0.004 | #0a0a0b |
| Bodega Fluor | 0.03 | #020202 |
| Edificio | 0.01 | #87CEEB (ciel) |
| Laberinto | 0.02 | #87CEEB (ciel) |

NYC a le brouillard le plus dense (0.012) pour l'atmosphere de tunnel. Bodega Fluor a 0.03, quasi opaque a 50m. Bodega a le plus leger (0.004), permettant de voir les hangars au loin. Edificio y Laberinto usan color azul ciel por ser mapas diurnos.

### Eclairage par scenario

Chaque carte a un eclairage aveccu pour son ambiance :

- **Metro:** `AmbientLight(0xffffff, 0.3)` base, `DirectionalLight(0xffffff, 0.4)`, `PointLight(#ff3300, 2, 80)` rouges dans les tunnels.
- **NYC Subway:** `AmbientLight(0xffffff, 0.08)` minimo, `PointLight(#dcf0f7, 0.15, 200)` froides en station, `PointLight(#ffb84d, 0.1, 180)` chaudes dans les tubes.
- **BA Subte:** `AmbientLight(0xffffff, 0.08)`, `PointLight(#ffddaa, 0.2, 200)` calidas, `PointLight(#ffb84d, 0.1, 180)` aux intersections.
- **Bodega:** `AmbientLight(0xffffff, 1.5)`, `DirectionalLight(#556677, 1.5)` luna, `PointLight` RGB (verde, magenta, cyan) + sombras `PCFSoftShadowMap`.
- **Bodega Fluor:** Solo `AmbientLight(#704045, 1.2)`. Une seule lumiere rougeatre. La carte la plus sombre.
- **Edificio:** `AmbientLight(0xffffff, 0.6)`, `DirectionalLight(0xffffff, 0.9)` soleil diurne.
- **Laberinto:** `AmbientLight(0xffffff, 0.7)`, `DirectionalLight(0xffffff, 0.8)` soleil diurne.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="23%" alt="Luz Metro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA2LmdpZg==/original/VWu641.gif" width="23%" alt="Luz NYC">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODk4LnBuZw==/original/uPh9Ab.png" width="23%" alt="Luz BA Subte">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="23%" alt="Luz Container">
</p>

### Mouvement joueur et physique

Le mouvement FPS est implemente sans `PointerLockControls` de Three.js. La camera tourne selon `movementX` y `movementY` de l'evenement `mousemove`. Le pitch (Y) est clampe entre -PI/2 et PI/2.

Le mouvement WASD est relatif a la camera. Vecteur forward depuis `camera.rotation.y` usando `sans/cos`, et un vecteur right perpendiculaire. Le saut utilise `playerVelocity.y` qui decroit par gravite. Le sol maintient le joueur a Y = playerHeight.

Parametres par carte :

| Mapa | Vitesse | Sprint | Gravite | Saut | Hauteur |
|---|---|---|---|---|---|
| Metro | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| NYC | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| BA Subte | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| Bodega | 0.28 | -- | 0.009 | 0.24 | 2.5 |
| Bodega Fluor | 0.20 | -- | 0.008 | 0.18 | 2.0 |
| Edificio | 0.25 | -- | 0.008 | 0.22 | 2.0 |
| Laberinto | 0.18 | -- | 0.008 | 0.22 | 2.0 |

Les cartes train partagent des parametres agiles avec sprint. Les autres sont plus lentes.

### Detection de collisions

Collisions avec murs et objets gerees par `Box3` de Three.js. Chaque geometrie statique recoit un bounding box via `computeBoundingBox()`. Avant le mouvement, un temporaire `Box3` est cree autour de la position future et teste avec `intersectsBox()` avectre tous les colliders. Si intersection, mouvement annule sur cet axe.

Sur Bodega Fluor, detection simplifiee : `Math.abs` avectre les coordonnees de la grille. Sur BA Subte, les murs sont des centaines de `BoxGeometry` individuels, chacun avec son `Box3`.

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

## Les cartes

<img width="144" height="68" alt="metro1" src="https://github.com/user-attachments/assets/9ae73a9b-e3a8-447a-b50f-269e039a506a" />
<img width="144" height="68" alt="metro2" src="https://github.com/user-attachments/assets/62368dac-d8d3-49ea-9a60-97818bd30655" />
<img width="144" height="68" alt="metro3" src="https://github.com/user-attachments/assets/65f23e73-9763-432e-983f-bdd13f1a3b4b" />
<img width="144" height="68" alt="metro4" src="https://github.com/user-attachments/assets/5f0d1497-100b-4477-9db0-f27bf182eeca" />
<img width="144" height="68" alt="metro5" src="https://github.com/user-attachments/assets/493d1c9b-94b0-4f5c-8f58-f91cd6acfef9" />

---

### 1. Maestranza Metro/Train -- Santiago, Ateliers L2

L'original. Celui qui a tout commence. Je l'ai ecrit en pensant aux ateliers de la Ligne 2 du Metro de Santiago, un immense hangar avec des rames NS-74 sur voie de garage. 22 trains bleus `#00a9e0` avec cabine, vitres, attelages et feux de position.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="30%" alt="Metro tren">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA4LmdpZg==/original/aQxVgp.gif" width="30%" alt="Metro pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA5LmdpZg==/original/5dwhdf.gif" width="30%" alt="Metro tunel">
</p>

Le hangar fait 400x600m, hauteur 50. Trois tunnels lateraux, quais sureleves, colonnes en fer tous les 40m, 40 caisses de pieces. Eclairage tunnel rouge `#ff3300`, intensite 2, portee 80. Brouillard : `FogExp2(0x020202, 0.008)`. La peinture utilise `CircleGeometry` avec `MeshBasicMaterial`. Sans systeme de gouttes -- version anterieure. Pas de trains en mouvement.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTE0LnBuZw==/original/xtXMwi.png" width="48%" alt="Metro snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTIxLnBuZw==/original/yQMlWG.png" width="48%" alt="Metro accion">
</p>

Timer de 1200s. A zero, `location.reload()`. Chute sous Y=-40, respawn automatique.

- Deplacement: 0.45 marche, 0.75 course (Shift)
- Gravite: 0.012, salto: 0.32, hauteur : 2.4
- Portee spray : 15 unites
- Valve : 0.1 a 1.4, pas 0.05, defaut 0.4
- 533 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger)

---

### 2. NYC Subway -- New York

Version new-yorkaise. Station centrale 400x100m, 4 voies en tunnels nord/sud. Passages transversaux tous les 120m. Murs en faience blanche `#dddddd`, colonnes acier vert NYC `#123524`. Tunnels en tube ferme avec plafond, sol et murs courbes.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTMyLnBuZw==/original/aR5DO4.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTMwLnBuZw==/original/9Uouzu.png" width="30%" alt="NYC Subway">
</p>

14 14 trains NYC stationnes : metal argente, toit noir, feux LED rouges. Statiques mais ambiance tendue : obscurite quasi totale, eclairage minimal, brouillard dense (0.012). Premiere carte a implementer `DecalGeometry` pour la peinture et le systeme de gouttes. Valve 0.1 a 5.0, des tags les plus fins aux throw-ups couvrant un train en seavecdes.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="24%" alt="NYC interior">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="24%" alt="NYC pintura">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="24%" alt="NYC spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="24%" alt="NYC gameplay">
</p>

- Deplacement: 0.45 / 0.75 (sprint)
- Gravite: 0.012, salto: 0.32, altura: 2.4
- Portee spray : 15, Valve : 0.1 a 5.0, defaut 1.0
- Gouttes : DRIP_THRESHOLD 15, max 400 gouttes actives
- 666 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-ny-subway)

---

### 3. BA Subte -- Buenos Aires (le plus complet)

990 lignes. La carte la plus grande et aboutie. Labyrinthe en grille de 11 por 11 blocs, 1100 por 1100 metros. Blocs de 70m, passages de 30m. Station centrale vide 100x300m. Murs beige creme `#e6dec3`, colonnes fer sombre `#2a302d`, panneaux publicitaires colores.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzEyLnBuZw==/original/3mj0P3.png" width="24%" alt="BA Subte">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="24%" alt="BA Subte trenes">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTg0LnBuZw==/original/EKymke.png" width="24%" alt="BA Subte laberinto">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzk2LnBuZw==/original/XvZrkX.png" width="24%" alt="BA Subte gameplay">
</p>

Seule carte avec trains en mouvement. Deux rames de 4 voitures avec phares visibles dans le brouillard. Voies fixes en X=-100 et X=+100. Reste sur la voie, Game Over sans respawn. 20 dernieres seavecdes : ecran rouge pulsant, brouillard sang, alerte clignotante.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="30%" alt="BA Subte tren movil">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="30%" alt="BA Subte game over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="30%" alt="BA Subte menu">
</p>

Menu bilingue ES/EN. Audio dual (YouTube sur serveur, HTML5 Audio en local). Gestion evenements avancee : prevention menu avectextuel, reset mouseleave/blur, premier mousemove ignore.

- Deplacement: 0.45 / 0.75 (sprint)
- Gravite: 0.012, salto: 0.32, altura: 2.4
- Portee spray : 15, Valve : 0.1 a 5.0, defaut 1.0
- Gouttes : DRIP_THRESHOLD 15, max 400 gotas
- Timer : 1200s alerte visuelle 20s finales
- Trains : 2 en movimiento, colision AABB, Game Over
- Audio: dual YouTube + HTML5 Audio fallback
- 990 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-tren-3) | [Gameplay](https://www.youtube.com/watch?v=dHxB3NoJs1k)

---

### 4. Container 1 / Entrepots de Nuit

Six hangars en grille 2x3, 50x12x60m chacun, avec colonnes et mezzanines. Rues en croix, zone parkour avec 12 piles de caisses, canalisations souterraines.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NTQxLmpwZw==/original/uyrEEi.jpg" width="30%" alt="Container">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="30%" alt="Container gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="30%" alt="Container parkour">
</p>

Seule carte avec ombres hardware. Lune `DirectionalLight #556677` projetant les ombres. Trois PointLights geants : vert `#39ff14`, magenta `#ff00ff`, cyan `#00ffff`. La carte nocturne la plus lumineuse (AmbientLight 1.5). Sans ennemis, sans danger. L'idee : parcourir, grimper, peindre.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjQzLmdpZg==/original/NQSFlF.gif" width="23%" alt="Container pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjUxLmdpZg==/original/%2BjKqLa.gif" width="23%" alt="Container spray">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjU5LmdpZg==/original/LwEjno.gif" width="23%" alt="Container luces">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjcyLmdpZg==/original/6Z4zsW.gif" width="23%" alt="Container sombras">
</p>

- Deplacement: 0.28 (sans sprint)
- Gravite: 0.009, salto: 0.24, altura: 2.5
- Portee spray : 12, Valve : 0.05 a 0.8, defaut 0.25
- Gouttes : DRIP_THRESHOLD 15, max 400 gotas, anti-statique souris
- Ombres: PCFSoftShadowMap activado
- 504 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-avectainers-1)

---

### 5. Bodega Fluor

La plus petite. 365 lineas. Labyrinthe 15x20 cellules (120x160m) couloirs d'un bloc de large. Obscurite quasi totale -- `AmbientLight #704045` intensite 1.2. UI vert neon sur noir.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY4LmdpZg==/original/DevNdf.gif" width="30%" alt="Fluor oscuro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="30%" alt="Fluor maze">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzcxLmdpZg==/original/QzmamK.gif" width="30%" alt="Fluor gameplay">
</p>

Labyrinthe hardcode en matrice 2D. Murs `BoxGeometry` 8 unites, hauteur 6. Collision par `Math.abs`, sans `Box3`. Gouttes agressives : sans bouger la souris, compteur double. Concu pour se perdre, peindre dans le noir, laisser les murs degouliner.

- Deplacement: 0.20 (el mas lento)
- Gravite: 0.008, salto: 0.18, altura: 2.0
- Portee spray : 6
- Gouttes : DRIP_THRESHOLD 20, max 300 gotas, accumulation acceleree
- Eclairage : solo AmbientLight rojiza
- 365 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/)

---

### 6. Batiment Abandonne

Le seul de jour. Cinq etages, grille 8x10, hauteur 7. Rampes alternees forcant le parcours. Vitres bleues translucides `#add8e6` opacite 0.3. Etage 5 sans fenetres.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDczLmpwZw==/original/xtwulo.jpg" width="30%" alt="Edificio">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQwLmdpZg==/original/DaJkjS.gif" width="30%" alt="Edificio vista">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQxLmdpZg==/original/JpuipW.gif" width="30%" alt="Edificio rampas">
</p>

50 rascaciels aleatorios alrededor: posicion, altura y dimensiones al azar. Forman un skyline envolvente. Lumiere jour: `AmbientLight` 0.6, `DirectionalLight` 0.9 soleil. Ciel et brouillard bleus `#87CEEB`. Murs gris beton `#999999`, sols gris fonce `#222222`. Sans gouttes, sans ennemis.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQ3LmdpZg==/original/UD6LMn.gif" width="45%" alt="Edificio pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzUwLmdpZg==/original/BJfE9R.gif" width="45%" alt="Edificio skyline">
</p>

- Deplacement: 0.25
- Gravite: 0.008, salto: 0.22, altura: 2.0
- Portee spray : 6, Valve : 0.05 a 0.6, defaut 0.25
- 5 etages rampes alternees, 50 rascaciels procedurales
- 486 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado)

---

### 7. Labyrinthe de Nuit

Labyrinthe exterieur. Grilla 8x10 (mismo layout que un piso del Edificio), murs hauteur 6. Train noir au centre. Blocs a 3 hauteurs pour parkour.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDg2LmpwZw==/original/IUC3Wb.jpg" width="24%" alt="Laberinto">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY1LmdpZg==/original/2TtbmH.gif" width="24%" alt="Laberinto gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="24%" alt="Laberinto pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="24%" alt="Laberinto parkour">
</p>

Containers dynamiques en perimetre `#ff9900, #ffcc00, #39ff14, #ff00ff, #00ffff` hauteurs 2 a 8. Seule carte ou la peinture s'attache a l'objet `hit.object.add(mark)`, pas a la scene. Position decal en coordonnees locales via `worldToLocal`. Lumiere jour, brouillard plus dense (0.02), plus lent (0.18).

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjA4LnBuZw==/original/RGgx6G.png" width="30%" alt="Laberinto snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjEwLnBuZw==/original/fjeoxH.png" width="30%" alt="Laberinto detalle">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjE1LnBuZw==/original/NxTraS.png" width="30%" alt="Laberinto accion">
</p>

- Deplacement: 0.18 (el mas lento del set)
- Gravite: 0.008, salto: 0.22, altura: 2.0
- Portee spray : 6, Valve : 0.05 a 0.6, defaut 0.25
- Peint. attachee a objetos (hit.object.add + worldToLocal)
- Train statique central + parkour + avectainers perimetrales
- 511 lignes de code

[JOUER](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) | [itch.io](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche)

---

## Comparatif

| Caracteristique | Metro | NYC | BA Subte | Container | Fluor | Edificio | Laberinto |
|---|---|---|---|---|---|---|---|
| Lineas de codigo | 533 | 666 | 990 | 504 | 365 | 486 | 511 |
| DecalGeometry | No | Si | Si | No | No | No | No |
| Gouttes | No | Si | Si | Si | Si | No | No |
| Trains mobiles | No | No | Si | No | No | No | No |
| Game Over | No | No | Si | No | No | No | No |
| Alerte 20s | No | No | Si | No | No | No | No |
| Sprint | Si | Si | Si | No | No | No | No |
| Ombres | No | No | No | Si | No | No | No |
| Etages | No | No | No | No | No | Si | No |
| Peint. attachee | No | No | No | No | No | No | Si |
| Lumiere jour | No | No | No | No | No | Si | Si |
| Audio dual | No | No | Si | No | No | No | No |
| Vitesse mov | 0.45 | 0.45 | 0.45 | 0.28 | 0.20 | 0.25 | 0.18 |

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="18%" alt="Comp 1">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="18%" alt="Comp 2">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="18%" alt="Comp 3">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="18%" alt="Comp 4">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="18%" alt="Comp 5">
</p>

---

## Controles

| Touche | Action |
|---|---|
| `W A S D` / fleches | Deplacement |
| `SHIFT` | Courir (seulement sur Metro, NYC, BA Subte) |
| `ESPACE` | Sauter |
| `SOURIS` | Regarder |
| `CLIC GAUCHE` | Peindre |
| `P` | Capture ecran (PNG) |
| `R` | Respawn |
| `ESC` | Liberer pointeur |

---

## Specifications techniques

- **Moteur :** Three.js WebGL, charge via CDN (jsdelivr/unpkg)
- **Langage :** JavaScript Vanilla, sans TypeScript
- **Poids par carte :** 15 KB a 50 KB (CSS + JS inline)
- **Dependances externes :** Three.js r128+ y YouTube IFrame API
- **Rendu :** `WebGLRenderer` avec `requestAnimationFrame`, target 60fps
- **Compatibilite :** Chrome, Edge, Firefox, Opera, Brave
- **Controles:** Pointer Lock API + eventos de teclado/mouse nativos
- **Formato:** un solo archivo HTML autonomo por escenario

### Architecture du code

Chaque HTML suit cette structure :

1. Metadonnees et CSS inline (primeras 100-200 lineas)
2. Declaration avecstantes : vitesses, gravite, timer, couleurs, dimensions
3. Setup Three.js : scene, camera, renderer, brouillard, lumieres
4. Construction geometrie : murs, sols, trains, colonnes, objets
5. Config evenements : clavier, souris, pointer lock, visibilite, resize
6. Game loop : `requestAnimationFrame` avec mouvement, physique, collisions, gouttes, trains, timer et UI
7. Utilitaires : spawn, respawn, capture, game over, alerte

---

## Demarche artistique

WDL Master Tagger n'est pas un jeu pour gagner. C'est un jeu pour etre la -- s'immerger dans un metro abandonne, sentir la pression du temps, entendre le bourdonnement des rails et savoir qu'a tout moment un train peut t'effacer.

Ce projet est un outil de pratique et visualisation pour graffeurs, designers et artistes visuels. Sans score, sans niveaux, sans succes. Un espace de simulation esthetique pour tester couleurs, compositions et styles avant de les sortir dans le monde reel.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTM5LnBuZw==/original/SJWreF.png" width="32%" alt="Arte 1">
  <img src="https://img.itch.zone/aW1nLzI3NTIzOTA2LnBuZw==/original/Ocdn3F.png" width="32%" alt="Arte 2">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MjAxLnBuZw==/original/ixdXIK.png" width="32%" alt="Arte 3">
</p>

---

## Feuille de route

- [x] 7 scenarios jouables via navigateur
- [x] Sistema de pintura avec DecalGeometry y goteo procedural
- [x] Trains mobiles avec colision AABB (BA Subte)
- [x] Radio YouTube integrada avec musica original
- [x] Snapshot mode (captura PNG)
- [x] Menu principal avec acceso a todos los mapas
- [x] Audio dual avec fallback para ejecucion local
- [x] Ombres proyectadas (Container 1)
- [ ] Compilation native .exe .exe (Standalone)
- [ ] Post-procesamiento visual: bloom, SSAO, motion blur
- [ ] Nouvelles cartes : usanse abandonnee, pont ferroviaire, depot avectainers 2
- [ ] Support gamepad
- [ ] Multijoueur local (ecran partage)

---

## Liens

<p align="center">

[![GitHub Pages](https://img.shields.io/badge/JOUER-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</p>

### Par scenario sur itch.io :

| Scenario | itch.io |
|---|---|
| Metro/Tren Santiago | [fierroduque.itch.io/wdl-master-tagger](https://fierroduque.itch.io/wdl-master-tagger) |
| NYC Subway | [fierroduque.itch.io/wdl-master-tagger-ny-subway](https://fierroduque.itch.io/wdl-master-tagger-ny-subway) |
| BA Subte | [fierroduque.itch.io/wdl-master-tagger-tren-3](https://fierroduque.itch.io/wdl-master-tagger-tren-3) |
| Container 1 / Bodega | [fierroduque.itch.io/wdl-master-tagger-avectainers-1](https://fierroduque.itch.io/wdl-master-tagger-avectainers-1) |
| Batiment Abandonne | [fierroduque.itch.io/wdl-master-tagger-edificio-abandonado](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado) |
| Labyrinthe de Nuit | [fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche) |

### Videos :

| Video | Link |
|---|---|
| Bande-annonce | [youtu.be/KE8L0RL6YC8](https://youtu.be/KE8L0RL6YC8) |
| Gameplay Metro/Tren | [youtube.com/watch?v=dHxB3NoJs1k](https://www.youtube.com/watch?v=dHxB3NoJs1k) |

---

## Structure du depot

```
WDL-MASTER-TAGGER-VERSION-METRO-/
├── index.html                          # Menu principal avec acces aux 7 cartes
├── README.md                           # Ce document
├── juego graffiti METRO/               # Maestranza Metro/Tren (Santiago)
│   └── index.html
├── juego graffiti trenes 2/            # NYC Subway Edition
│   └── index.html
├── juego graffiti trenes 3/            # BA Subte Edition
│   └── index.html
├── juego grafiti BODEGA/               # Container 1 / Entrepots de Nuit
│   └── index.html
├── juego grafiti BODEGA FLUOR/         # Laberinto Neon
│   └── index.html
├── juego grafiti EDIFICIO/             # Batiment Abandonne (5 pisos)
│   └── index.html
└── juego grafiti LABERINTO/            # Labyrinthe de Nuit
    └── index.html
```

Chaque dossier avectient un seul `index.html` autonome. Sans dependance, sans installation. Ouvre n'importe lequel dans ton navigateur et commence a peindre.

---

<p align="center">
  <em>WDL -- De la rue au code.</em><br>
  <strong>(c) 2025-2026 Eduardo Fierro -- fierroduque.com</strong><br><br>
  <sub>Aucune IA generative pour les assets visuels. Fait main, ligne par ligne.</sub>
</p>
