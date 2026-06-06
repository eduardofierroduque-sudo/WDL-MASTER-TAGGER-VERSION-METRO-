<p align="center">
  <img width="800" src="https://img.itch.zone/aW1nLzI3MTIwODUyLnBuZw==/original/YlguIp.png" alt="WDL MASTER TAGGER">
</p>

<div align="center">

# WDL MASTER TAGGER

**Simulador de graffiti em primeira pessoa. HTML5, WebGL, Three.js. JavaScript puro.**

*Nao e um jogo de tiro. E um jogo de marcar territorio: conquiste o espaco e deixe sua assematura.*

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

[![Jogar Agora](https://img.shields.io/badge/JOGAR_AGORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</div>

<img width="1920" height="1080" alt="WDL MASTER TAGGER Banner" src="https://github.com/user-attachments/assets/e36704b2-a72d-4af0-9d15-818dddf80608" />

---

## A Colecao -- 7 Cenarios Jogaveis pelo Navegador

<div align="center">

| # | Cenario | Tipo | Estilo | Jugar |
|---|---|---|---|---|
| 1 | **Maestranza Metro/Tren** | Oficinas Ferroviarias, Santiago | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) |
| 2 | **NYC Subway** | Metro de Nova York | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) |
| 3 | **BA Subte** | Metro Buenos Aires | Perigo | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) |
| 4 | **Container 1** | Estaleiro Industrial | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) |
| 5 | **Bodega Fluor** | Labirinto Escuro | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/) |
| 6 | **Edificio Abandonado** | Arranha-ceu, 5 Andares | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) |
| 7 | **Labirinto Noturno** | Labirinto Externo Murado | Livre | [JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) |

</div>

> Todos os mapas incluem radio integrada com musica produzida por Eduardo Fierro, via YouTube IFrame API. Cada mapa e um unico arquivo HTML que carrega instantaneamente. Sem downloads, sem instalacoes.

---

## Trailer

<p align="center">
  <a href="https://youtu.be/KE8L0RL6YC8">
    <img src="https://img.youtube.com/vi/KE8L0RL6YC8/0.jpg" alt="Trailer WDL MASTER TAGGER" width="600">
  </a>
  <br>
  <a href="https://youtu.be/KE8L0RL6YC8">VER TRAILER NO YOUTUBE</a>
</p>

---

## O Motor -- Componentes e Sistemas

Tudo foi escrito em JavaScript Vanilla sobre Three.js r128+, carregado via CDN. Sem bundlers, sem frameworks, sem dependencias npm. Um unico arquivo HTML por cenario contendo todo CSS, JS e a cena 3D inline. O tamanho por mapa varia de 15 KB a 50 KB.

### Sistema de Pintura por DecalGeometry

Nos mapas NYC Subway e BA Subte, a pintura e aplicada usando `DecalGeometry` de Three.js. Uma textura procedural de spray radial e gerada em um canvas 2D offscreen, usando gradientes radiais com diferentes niveis de opacidade e dispersao. Essa textura e passada como `map` a un `MeshBasicMaterial` configurado com `alphaTest: 0.1`, `polygonOffset: true`, `polygonOffsetFactor: -4` y `depthWrite: false`. Isso elimina o Z-fighting entre camadas de pintura sobrepostas sem precisar modificar a geometria da parede.

El `Raycaster` e lancado da posicao da camera em direcao ao centro da tela, com alcance configuravel de 6 a 15 unidades dependendo do mapa. Se o raio atingir uma superficie, um `DecalGeometry` e colocado no ponto de impacto, orientado conforme a normal da face atingida. O tamanho do decal e controlado pela valvula (slider en UI).

Nos demais mapas usa-se `CircleGeometry` con `MeshBasicMaterial`, aplicando `renderOrder` incremental e `polygonOffset` com fator variavel por camada. E mais leve mas nao tem a mesma fidelidade de textura de aerosol.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="32%" alt="Decal spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="32%" alt="Decal example">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="32%" alt="Decal result">
</p>

### Sistema de Gotejamento Procedural

Quando o jogador mantem o spray no mesmo ponto, um contador interno `dripCounter` incrementa. Ao ultrapassar o limite `DRIP_THRESHOLD` (15 na maioria dos mapas), o motor gera gotas na posicao de impacto. Cada gota e um `BoxGeometry` muito fino e alongado, com material semitransparente da mesma cor do traco ativo.

Cada gota tem propriedades aleatorias geradas ao ser criada: velocidade de queda (`dripSpeed`, entre 0.08 e 0.25 unidades por frame), comprimento inicial (`dripLength`, entre 0.05 e 0.3), e um offset lateral aleatorio para evitar que todas as gotas caiam em linha perfeita. A gota se estica progressivamente no eixo Y (`scale.y += dripSpeed * 0.1`) e se desloca para baixo (`position.y -= dripSpeed`). Cuando `scale.y` ultrapassa um maximo ou a gota sai do alcance visivel, ela e removida do array `activeDrips`.

Ha um limite de gotas ativas (300 a 400 dependendo do mapa). Quando atingido, as gotas mais antigas sao removidas primeiro (FIFO). Nos mapas Bodega e Bodega Fluor, o contador de gotejamento reseta ou desacelera se o jogador mover o mouse, simulando o spray se espalhando por uma superficie maior em vez de acumular em um ponto.

Especificamente no Bodega Fluor, se a distancia percorrida pelo mouse entre frames for menor que 0.05 unidades, `dripCounter` incrementa em 2 por frame (acumulacao rapida). Se o mouse se mover mais, incrementa apenas 0.5.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzA0LmdpZg==/original/HdS8d7.gif" width="24%" alt="Drip system">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="24%" alt="Drip detail">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzk5LmdpZg==/original/5%2BWVx7.gif" width="24%" alt="Drip paint">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="24%" alt="Drip result">
</p>

### Trens em Movimento e Colisao AABB

Exclusivo do mapa BA Subte. Ha duas formacoes que circulam por trilhos laterais fixos (X = -100 y X = +100). Cada formacao tem 4 vagoes montados com `BoxGeometry`, totalizando aproximadamente 300 unidades de comprimento. Carregam um `PointLight` frontal que atua como farol (`color: #ffeecc, intensity: 3, distance: 400`), visivel atraves da neblina.

A logica de movimento e linear e deterministica: o trem 1 avanca na direcao +Z de Z = -550 ate desaparecer em Z > 650. O trem 2 avanca na direcao -Z de Z = +550 ate Z < -650. A velocidade e de 3.0 unidades por frame (a 60fps, cerca de 180 metros virtuais por segundo). Ao desaparecer, um respawn e programado com `setTimeout`: trem 1 a cada 120 segundos exatos, trem 2 a cada 120 segundos mas defasado (inicia 75s depois do primeiro). O primeiro trem aparece aos 15 segundos de partida, o segundo aos 75 segundos.

A deteccao de colisao e por AABB (Axis-Aligned Bounding Box). Nao se usa `Box3` do Three.js para isso, mas uma comparacao direta de faixas: se a faixa Z do trem (posicao Z mais/menos metade do comprimento) se sobrepoe a faixa Z do jogador, e ambos compartilham o mesmo eixo X do trilho, ha colisao. A tela fica preta, um overlay vermelho aparece com o texto ATROPELADO PELO TREM em fonte sans-serif, e um link de recarga. Sem respawn, sem continuar.

Nos ultimos 20 segundos do timer, o fundo da cena (`scene.background`) comeca a oscilar entre preto e vermelho escuro, a neblina `FogExp2` muda sua cor para `#330000`, e um overlay HTML com o texto ALERTA DE SEGURANCA -- ABANDONE A AREA IMEDIATAMENTE pisca sobre o canvas. Isso e implementado com `setInterval` a 500ms que alterna classes CSS e modifica as propriedades de cor da cena em tempo real.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="32%" alt="Tren moving">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="32%" alt="Game Over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="32%" alt="Alerta roja">
</p>

### Sistema de Audio e Radio

Todos os mapas integram a YouTube IFrame API. Um elemento iframe oculto e criado que carrega o player do YouTube sem interface e comeca a reproduzir uma playlist com musica original produzida por Eduardo Fierro.

No mapa BA Subte ha um sistema dual de audio. Quando o HTML e carregado de um servidor web (HTTP/HTTPS), a YouTube IFrame API e usada normalmente. Mas quando aberto de `file://` (duplo clique local), o navegador bloqueia a IFrame API do YouTube por politicas de mesma origem. Nesse caso, o codigo comuta automaticamente para streams de audio HTML5 usando o elemento `<audio>` nativo, com URLs diretas para arquivos MP3. Isso permite que o jogo funcione mesmo executado localmente sem servidor.

A deteccao e feita verificando `window.location.protocol`: si es `file:`, o fallback de audio local e ativado. Si es `http:` o `https:`, o YouTube e usado. O volume do player do YouTube e ajustado via `player.setVolume()` e o elemento de audio nativo via `audio.volume`.

### Modo Snapshot -- Captura de Tela

Ao pressionar a tecla `P`, e executado `renderer.render(scene, camera)` para garantir que o buffer esteja atualizado, entao o conteudo do canvas e extraido com `canvas.toDataURL('image/png')`. Um elemento ancora temporario e criado com `download = 'wdl-snapshot.png'`, o data URL e atribuido como `href` e um clique programatico e disparado. O resultado e um PNG na resolucao nativa do canvas, baixado diretamente.

### Renderizacao e Neblina

Todos os mapas usam `FogExp2` do Three.js, que implementa neblina exponencial quadratica: a visibilidade decai conforme `exp(-density * distance^2)`. A densidade varia entre mapas:

| Mapa | Densidad | Cor da Neblina |
|---|---|---|
| Metro | 0.008 | #020202 |
| NYC Subway | 0.012 | #020202 |
| BA Subte | 0.008 | #020202 (muda para #330000 em alerta) |
| Bodega | 0.004 | #0a0a0b |
| Bodega Fluor | 0.03 | #020202 |
| Edificio | 0.01 | #87CEEB (ceu) |
| Laberinto | 0.02 | #87CEEB (ceu) |

NYC tem a neblina mais densa (0.012) para acentuar o ambiente fechado de tunel. Bodega Fluor tem 0.03, quase opaca a 50 metros. Bodega tem a mais leve (0.004), permitindo ver os galpoes a distancia. Edificio y Laberinto usan color azul ceu por ser mapas diurnos.

### Iluminacao por Cenario

Cada mapa tem uma configuracao de luzes pensada para sua ambientacao:

- **Metro:** `AmbientLight(0xffffff, 0.3)` base, `DirectionalLight(0xffffff, 0.4)`, `PointLight(#ff3300, 2, 80)` vermelhas nos tuneis.
- **NYC Subway:** `AmbientLight(0xffffff, 0.08)` minimo, `PointLight(#dcf0f7, 0.15, 200)` frias na estacao, `PointLight(#ffb84d, 0.1, 180)` quentes nos tubos.
- **BA Subte:** `AmbientLight(0xffffff, 0.08)`, `PointLight(#ffddaa, 0.2, 200)` calidas, `PointLight(#ffb84d, 0.1, 180)` nas intersecoes.
- **Bodega:** `AmbientLight(0xffffff, 1.5)`, `DirectionalLight(#556677, 1.5)` luna, `PointLight` RGB (verde, magenta, ciano) + sombras `PCFSoftShadowMap`.
- **Bodega Fluor:** Solo `AmbientLight(#704045, 1.2)`. Uma unica luz avermelhada. E o mapa mais escuro.
- **Edificio:** `AmbientLight(0xffffff, 0.6)`, `DirectionalLight(0xffffff, 0.9)` sol diurno.
- **Laberinto:** `AmbientLight(0xffffff, 0.7)`, `DirectionalLight(0xffffff, 0.8)` sol diurno.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njc5LmdpZg==/original/TYMWnA.gif" width="23%" alt="Luz Metro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA2LmdpZg==/original/VWu641.gif" width="23%" alt="Luz NYC">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODk4LnBuZw==/original/uPh9Ab.png" width="23%" alt="Luz BA Subte">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="23%" alt="Luz Container">
</p>

### Movimento do Jogador e Fisica

O movimento em primeira pessoa e implementado sem usar `PointerLockControls` do Three.js. A camera gira diretamente conforme `movementX` y `movementY` do evento `mousemove`. O pitch (Y) e limitado entre -PI/2 e PI/2.

O movimento WASD e relativo a orientacao da camera. Um vetor forward e calculado a partir de `camera.rotation.y` usando `sem/cos`, e um vetor right perpendicular. O pulo usa `playerVelocity.y` que diminui por gravidade a cada frame. Uma verificacao de chao mantem o jogador em Y = playerHeight.

Parametros por mapa:

| Mapa | Velocidade | Sprint | Gravidade | Pulo | Altura |
|---|---|---|---|---|---|
| Metro | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| NYC | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| BA Subte | 0.45 | 0.75 | 0.012 | 0.32 | 2.4 |
| Bodega | 0.28 | -- | 0.009 | 0.24 | 2.5 |
| Bodega Fluor | 0.20 | -- | 0.008 | 0.18 | 2.0 |
| Edificio | 0.25 | -- | 0.008 | 0.22 | 2.0 |
| Laberinto | 0.18 | -- | 0.008 | 0.22 | 2.0 |

Os mapas de trem compartilham parametros ageis com sprint. Os demais sao mais lentos, pensados para exploracao tranquila.

### Deteccao de Colisoes com o Ambiente

As colisoes contra paredes e objetos sao tratadas com `Box3` de Three.js. Cada geometria estatica recebe um bounding box via `computeBoundingBox()`. Antes de aplicar o movimento do jogador, um temporario `Box3` e criado ao redor da posicao futura e testado com `intersectsBox()` contra todos os colisores. Se houver intersecao, o movimento nesse eixo e cancelado.

No Bodega Fluor, a deteccao e mais simples: `Math.abs` contra as coordenadas do grid do labirinto. No BA Subte, as paredes do labirinto sao centenas de `BoxGeometry` individuais, cada uma com seu `Box3`.

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

## Os Mapas

<img width="144" height="68" alt="metro1" src="https://github.com/user-attachments/assets/9ae73a9b-e3a8-447a-b50f-269e039a506a" />
<img width="144" height="68" alt="metro2" src="https://github.com/user-attachments/assets/62368dac-d8d3-49ea-9a60-97818bd30655" />
<img width="144" height="68" alt="metro3" src="https://github.com/user-attachments/assets/65f23e73-9763-432e-983f-bdd13f1a3b4b" />
<img width="144" height="68" alt="metro4" src="https://github.com/user-attachments/assets/5f0d1497-100b-4477-9db0-f27bf182eeca" />
<img width="144" height="68" alt="metro5" src="https://github.com/user-attachments/assets/493d1c9b-94b0-4f5c-8f58-f91cd6acfef9" />

---

### 1. Maestranza Metro/Trem -- Santiago, Oficinas L2

O original. O que comecou tudo. Escrevi pensando nas oficinas da Linha 2 do Metro de Santiago, um hangar industrial enorme com formacoes NS-74 estacionadas em via morta. Sao 22 trens azuis `#00a9e0` com cabine, vidros, engates metalicos e luzes de posicao.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA0LmdpZg==/original/J3NJWn.gif" width="30%" alt="Metro tren">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA4LmdpZg==/original/aQxVgp.gif" width="30%" alt="Metro pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2ODA5LmdpZg==/original/5dwhdf.gif" width="30%" alt="Metro tunel">
</p>

O mapa e um hangar de 400 por 600 metros com altura 50. Tres tuneis para os lados, plataformas elevadas, colunas de ferro a cada 40 metros e cerca de 40 caixas de pecas. As luzes dos tuneis sao vermelhas `#ff3300`, intensidade 2, alcance 80. A neblina e `FogExp2(0x020202, 0.008)`. A pintura usa `CircleGeometry` con `MeshBasicMaterial`. Sem sistema de gotejamento -- esta versao e anterior a esse desenvolvimento. Sem trens em movimento.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTE0LnBuZw==/original/xtXMwi.png" width="48%" alt="Metro snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MTIxLnBuZw==/original/yQMlWG.png" width="48%" alt="Metro accion">
</p>

O timer marca 1200 segundos. Ao chegar a zero chama `location.reload()`. Se cair abaixo de Y = -40, respawn automatico.

- Movimento: 0.45 andando, 0.75 correndo (Shift)
- Gravidade: 0.012, salto: 0.32, altura do jogador: 2.4
- Alcance do spray: 15 unidades
- Valvula: 0.1 a 1.4, passo 0.05, padrao 0.4
- 533 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20METRO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger)

---

### 2. NYC Subway -- Nova York

A versao nova-iorquina. Estacao central de 400 por 100 metros com quatro trilhos que se estendem em tuneis para o norte e sul. Corredores transversais a cada 120 metros. Paredes de azulejo branco `#dddddd`, colunas de aco verde NYC `#123524`. Tuneis em tubo fechado com teto, piso e paredes curvas.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTMyLnBuZw==/original/aR5DO4.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="30%" alt="NYC Subway">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTMwLnBuZw==/original/9Uouzu.png" width="30%" alt="NYC Subway">
</p>

14 trens estilo NYC estacionados: metal prateado, teto preto, luzes LED vermelhas na traseira. Os trens sao estaticos mas a ambientacao e tensa: escuridao quase total, luzes minimas, neblina densa (0.012). Primeiro mapa a implementar `DecalGeometry` para a pintura e o sistema de gotejamento completo. Valvula de 0.1 a 5.0, permitindo de tags finissimos ate throw-ups que cobrem um trem em segundos.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="24%" alt="NYC interior">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTg3LnBuZw==/original/f8PbmW.png" width="24%" alt="NYC pintura">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTkwLnBuZw==/original/I4hjrd.png" width="24%" alt="NYC spray">
  <img src="https://img.itch.zone/aW1nLzI3MTM3OTk1LnBuZw==/original/Kesm02.png" width="24%" alt="NYC gameplay">
</p>

- Movimento: 0.45 / 0.75 (sprint)
- Gravidade: 0.012, salto: 0.32, altura: 2.4
- Alcance do spray: 15, Valvula: 0.1 a 5.0, padrao 1.0
- Gotejamento: DRIP_THRESHOLD 15, max 400 gotas ativas
- 666 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%202/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-ny-subway)

---

### 3. BA Subte -- Buenos Aires (o mais completo)

990 linhas. O mapa mais extenso e mais trabalhado. Labirinto em grade de 11 por 11 blocos, 1100 por 1100 metros. Blocos de 70m com corredores de 30m. Estacao central vazia de 100 por 300 metros. Paredes bege creme `#e6dec3`, colunas de ferro escuro `#2a302d`, paineis publicitarios coloridos.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzEyLnBuZw==/original/3mj0P3.png" width="24%" alt="BA Subte">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="24%" alt="BA Subte trenes">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTg0LnBuZw==/original/EKymke.png" width="24%" alt="BA Subte laberinto">
  <img src="https://img.itch.zone/aW1nLzI3NTIzNzk2LnBuZw==/original/XvZrkX.png" width="24%" alt="BA Subte gameplay">
</p>

Unico mapa com trens em movimento. Duas formacoes de 4 vagoes com farois dianteiros visiveis atraves da neblina. Circulam por trilhos fixos em X = -100 e X = +100. Se voce ficar no trilho, Game Over sem respawn. Nos ultimos 20 segundos, a tela pulsa em vermelho, a neblina fica cor de sangue e um aviso de alerta pisca.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODA1LnBuZw==/original/0ejzuP.png" width="30%" alt="BA Subte tren movil">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODEzLnBuZw==/original/69ayyr.png" width="30%" alt="BA Subte game over">
  <img src="https://img.itch.zone/aW1nLzI3NTIzODc1LnBuZw==/original/XOo7nC.png" width="30%" alt="BA Subte menu">
</p>

Menu bilingue ES/EN com controles, missao e avisos. Audio Dual (YouTube no servidor, HTML5 Audio localmente). Gerenciamento avancado de eventos: prevencao de menu contextual, reset em mouseleave/blur, primeiro mousemove ignorado.

- Movimento: 0.45 / 0.75 (sprint)
- Gravidade: 0.012, salto: 0.32, altura: 2.4
- Alcance do spray: 15, Valvula: 0.1 a 5.0, padrao 1.0
- Gotejamento: DRIP_THRESHOLD 15, max 400 gotas
- Timer: 1200s com alerta visual nos 20s finais
- Trens: 2 en movimiento, colision AABB, Game Over
- Audio: dual YouTube + HTML5 Audio fallback
- 990 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20graffiti%20trenes%203/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-tren-3) | [Gameplay](https://www.youtube.com/watch?v=dHxB3NoJs1k)

---

### 4. Container 1 / Galpoes Noturnos

Seis galpoes em grade 2 por 3, cada um 50x12x60m, com colunas internas e mezaninos parciais. Ruas em cruz, zona de parkour com 12 pilhas de caixas, tubulacoes subterraneas.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NTQxLmpwZw==/original/uyrEEi.jpg" width="30%" alt="Container">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Njk4LmdpZg==/original/ClpUdF.gif" width="30%" alt="Container gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="30%" alt="Container parkour">
</p>

Unico mapa com sombras ativadas por hardware. Luar `DirectionalLight #556677` projetando sombras de galpoes e caixas. Tres PointLights gigantes: verde `#39ff14`, magenta `#ff00ff`, ciano `#00ffff`. E o mapa noturno mais luminoso (AmbientLight 1.5). Sem inimigos, sem perigo. A ideia e percorrer, escalar e pintar.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjQzLmdpZg==/original/NQSFlF.gif" width="23%" alt="Container pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjUxLmdpZg==/original/%2BjKqLa.gif" width="23%" alt="Container spray">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjU5LmdpZg==/original/LwEjno.gif" width="23%" alt="Container luces">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NjcyLmdpZg==/original/6Z4zsW.gif" width="23%" alt="Container sombras">
</p>

- Movimento: 0.28 (sem sprint)
- Gravidade: 0.009, salto: 0.24, altura: 2.5
- Alcance do spray: 12, Valvula: 0.05 a 0.8, padrao 0.25
- Gotejamento: DRIP_THRESHOLD 15, max 400 gotas, anti-estatico por movimento do mouse
- Sombras: PCFSoftShadowMap activado
- 504 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-containers-1)

---

### 5. Bodega Fluor

O menor. 365 lineas. Labirinto de 15 por 20 celulas (120x160m) com corredores de um bloco de largura. Escuridao quase total -- apenas `AmbientLight #704045` a intensidade 1.2. UI verde neon sobre preto.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY4LmdpZg==/original/DevNdf.gif" width="30%" alt="Fluor oscuro">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="30%" alt="Fluor maze">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzcxLmdpZg==/original/QzmamK.gif" width="30%" alt="Fluor gameplay">
</p>

Labirinto hardcoded como matriz 2D, nao procedural. Paredes sao `BoxGeometry` de 8 unidades, altura 6. Colisao via `Math.abs`, sem `Box3`. Gotejamento agressivo: se voce nao mover o mouse, o contador sobe ao dobro da velocidade. Projetado para se perder no labirinto, pintar na escuridao e deixar as paredes cheias de escorrimentos.

- Movimento: 0.20 (el mas lento)
- Gravidade: 0.008, salto: 0.18, altura: 2.0
- Alcance do spray: 6
- Gotejamento: DRIP_THRESHOLD 20, max 300 gotas, acumulacao acelerada
- Iluminacao: solo AmbientLight rojiza
- 365 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20BODEGA%20FLUOR/)

---

### 6. Edificio Abandonado

O unico diurno. Cinco andares, grade 8x10 por planta, altura do andar 7. Rampas alternadas: andar 1 sobe no canto A, andar 2 no canto B, forcando percorrer cada andar. Janeloes a cada 3 celulas, vidro azul translucido `#add8e6` con opacidad 0.3. Piso 5 sem ventanas exteriores.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDczLmpwZw==/original/xtwulo.jpg" width="30%" alt="Edificio">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQwLmdpZg==/original/DaJkjS.gif" width="30%" alt="Edificio vista">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQxLmdpZg==/original/JpuipW.gif" width="30%" alt="Edificio rampas">
</p>

50 rascaceus aleatorios alrededor: posicion, altura y dimensiones al azar. Forman un skyline envolvente. Luz do Dia: `AmbientLight` 0.6, `DirectionalLight` 0.9 sol. Ceu e neblina azuis `#87CEEB`. Paredes cinza concreto `#999999`, pisos cinza escuro `#222222`. Sin goteo, sem enemigos.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzQ3LmdpZg==/original/UD6LMn.gif" width="45%" alt="Edificio pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzUwLmdpZg==/original/BJfE9R.gif" width="45%" alt="Edificio skyline">
</p>

- Movimento: 0.25
- Gravidade: 0.008, salto: 0.22, altura: 2.0
- Alcance do spray: 6, Valvula: 0.05 a 0.6, padrao 0.25
- 5 andares com rampas alternadas, 50 rascaceus procedurales
- 486 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20EDIFICIO/) | [itch.io](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado)

---

### 7. Labirinto Noturno

Labirinto Externo Murado. Grilla 8x10 (mismo layout que un piso del Edificio), muros altura 6. Trem estatico preto ao centro -- obstaculo que divide o labirinto. Blocos escalonados de 3 alturas para parkour.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NDg2LmpwZw==/original/IUC3Wb.jpg" width="24%" alt="Laberinto">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzY1LmdpZg==/original/2TtbmH.gif" width="24%" alt="Laberinto gameplay">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzc5LmdpZg==/original/p73fq%2B.gif" width="24%" alt="Laberinto pintura">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="24%" alt="Laberinto parkour">
</p>

Containers dinamicos no perimetro: caixas coloridas `#ff9900, #ffcc00, #39ff14, #ff00ff, #00ffff` com alturas entre 2 e 8, distribuidas nos 4 lados. Unico mapa onde a pintura se fixa como filha do objeto `hit.object.add(mark)`, nao da cena. A posicao do decal e convertida para coordenadas locais com `worldToLocal`. Luz do dia, neblina mais densa que o Edificio (0.02), velocidade mais lenta (0.18).

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjA4LnBuZw==/original/RGgx6G.png" width="30%" alt="Laberinto snapshot">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjEwLnBuZw==/original/fjeoxH.png" width="30%" alt="Laberinto detalle">
  <img src="https://img.itch.zone/aW1nLzI3MTM4MjE1LnBuZw==/original/NxTraS.png" width="30%" alt="Laberinto accion">
</p>

- Movimento: 0.18 (el mas lento del set)
- Gravidade: 0.008, salto: 0.22, altura: 2.0
- Alcance do spray: 6, Valvula: 0.05 a 0.6, padrao 0.25
- Pintura fixada a objetos (hit.object.add + worldToLocal)
- Trem estatico central + parkour + containers perimetrales
- 511 linhas de codigo

[JOGAR](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/juego%20grafiti%20LABERINTO/) | [itch.io](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche)

---

## Comparativo de Cenarios

| Caracteristica | Metro | NYC | BA Subte | Container | Fluor | Edificio | Laberinto |
|---|---|---|---|---|---|---|---|
| Lineas de codigo | 533 | 666 | 990 | 504 | 365 | 486 | 511 |
| DecalGeometry | No | Si | Si | No | No | No | No |
| Sist. Gotejamento | No | Si | Si | Si | Si | No | No |
| Trens em Movimento | No | No | Si | No | No | No | No |
| Game Over | No | No | Si | No | No | No | No |
| Alerta 20s | No | No | Si | No | No | No | No |
| Sprint | Si | Si | Si | No | No | No | No |
| Sombras | No | No | No | Si | No | No | No |
| Multiplos Andares | No | No | No | No | No | Si | No |
| Pintura Fixada | No | No | No | No | No | No | Si |
| Luz do Dia | No | No | No | No | No | Si | Si |
| Audio Dual | No | No | Si | No | No | No | No |
| Velocidade mov | 0.45 | 0.45 | 0.45 | 0.28 | 0.20 | 0.25 | 0.18 |

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MTk1LnBuZw==/original/9pwbF5.png" width="18%" alt="Comp 1">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTE5LnBuZw==/original/smTjIS.png" width="18%" alt="Comp 2">
  <img src="https://img.itch.zone/aW1nLzI3NTI0MTcxLnBuZw==/original/TzYang.png" width="18%" alt="Comp 3">
  <img src="https://img.itch.zone/aW1nLzI2ODY2NzEzLmdpZg==/original/ikkq4n.gif" width="18%" alt="Comp 4">
  <img src="https://img.itch.zone/aW1nLzI2ODY2Nzg0LmdpZg==/original/aVHe9T.gif" width="18%" alt="Comp 5">
</p>

---

## Controles

| Tecla | Acao |
|---|---|
| `W A S D` / setas | Movimento |
| `SHIFT` | Correr (apenas em Metro, NYC, BA Subte) |
| `ESPACO` | Pular |
| `MOUSE` | Olhar ao redor |
| `CLIQUE ESQUERDO` | Pintar spray |
| `P` | Captura de Tela (PNG) |
| `R` | Respawn |
| `ESC` | Soltar ponteiro |

---

## Especificacoes Tecnicas Gerais

- **Motor:** Three.js WebGL, carregado via CDN (jsdelivr/unpkg)
- **Linguagem:** JavaScript Vanilla, sem TypeScript ni transpiladores
- **Tamanho por mapa:** 15 KB a 50 KB (CSS + JS inline)
- **Dependencias externas:** Three.js r128+ y YouTube IFrame API
- **Renderizacao:** `WebGLRenderer` con `requestAnimationFrame`, target 60fps
- **Compatibilidade:** Chrome, Edge, Firefox, Opera, Brave
- **Controles:** Pointer Lock API + eventos de teclado/mouse nativos
- **Formato:** un solo archivo HTML autonomo por escenario

### Arquitetura do Codigo

Cada arquivo HTML segue a mesma estrutura:

1. Metadados e CSS inline (primeras 100-200 lineas)
2. Declaracao de constantes: velocidades, gravidade, timer, cores, dimensoes
3. Setup do Three.js: cena, camera, renderizador, neblina, luzes
4. Construcao de geometria: paredes, pisos, trens, colunas, objetos
5. Configuracao de eventos: teclado, mouse, pointer lock, visibilidade, resize
6. Game loop: `requestAnimationFrame` com movimento, fisica, colisoes, gotejamento, trens, timer e UI
7. Utilitarios: spawn, respawn, captura, game over, alerta

---

## Fundamento Artistico

WDL Master Tagger nao e um jogo para vencer. E um jogo para estar -- para mergulhar na atmosfera de um metro abandonado, sentir a pressao do relogio, ouvir o zumbido dos trilhos e saber que a qualquer momento um trem pode te apagar.

Este projeto nasce como uma ferramenta de pratica e visualizacao para escritores de graffiti, designers e artistas visuais. Nao tem pontuacao, nao tem niveis, nao tem conquistas. E um espaco de simulacao estetica onde testar combinacoes de cores, composicoes e estilos antes de leva-los ao mundo real, ou simplesmente desfrutar do fluxo criativo em um ambiente industrial atmosferico.

<p align="center">
  <img src="https://img.itch.zone/aW1nLzI3MTM4NTM5LnBuZw==/original/SJWreF.png" width="32%" alt="Arte 1">
  <img src="https://img.itch.zone/aW1nLzI3NTIzOTA2LnBuZw==/original/Ocdn3F.png" width="32%" alt="Arte 2">
  <img src="https://img.itch.zone/aW1nLzI3MTM3MjAxLnBuZw==/original/ixdXIK.png" width="32%" alt="Arte 3">
</p>

---

## Roadmap

- [x] 7 cenarios jogaveis via navegador
- [x] Sistema de pintura con DecalGeometry y goteo procedural
- [x] Trens em Movimento con colision AABB (BA Subte)
- [x] Radio YouTube integrada con musica original
- [x] Snapshot mode (captura PNG)
- [x] Menu principal con acceso a todos los mapas
- [x] Audio Dual con fallback para ejecucion local
- [x] Sombras proyectadas (Container 1)
- [ ] Compilacao nativa .exe (Standalone)
- [ ] Post-procesamiento visual: bloom, SSAO, motion blur
- [ ] Novos mapas: fabrica abandonada, ponte ferroviaria, deposito containers 2
- [ ] Suporte para gamepad
- [ ] Multijogador local (tela dividida)

---

## Links

<p align="center">

[![GitHub Pages](https://img.shields.io/badge/JOGAR_AGORA-FF9900?style=for-the-badge&logo=github&logoColor=black)](https://eduardofierroduque-sudo.github.io/WDL-MASTER-TAGGER-VERSION-METRO-/)
[![itch.io](https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://fierroduque.itch.io/)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@WDLMASTERTAGGER)
[![Website](https://img.shields.io/badge/fierroduque.com-000000?style=for-the-badge&logo=safari&logoColor=white)](https://fierroduque.com)

</p>

### Por cenario no itch.io:

| Cenario | itch.io |
|---|---|
| Metro/Tren Santiago | [fierroduque.itch.io/wdl-master-tagger](https://fierroduque.itch.io/wdl-master-tagger) |
| NYC Subway | [fierroduque.itch.io/wdl-master-tagger-ny-subway](https://fierroduque.itch.io/wdl-master-tagger-ny-subway) |
| BA Subte | [fierroduque.itch.io/wdl-master-tagger-tren-3](https://fierroduque.itch.io/wdl-master-tagger-tren-3) |
| Container 1 / Bodega | [fierroduque.itch.io/wdl-master-tagger-containers-1](https://fierroduque.itch.io/wdl-master-tagger-containers-1) |
| Edificio Abandonado | [fierroduque.itch.io/wdl-master-tagger-edificio-abandonado](https://fierroduque.itch.io/wdl-master-tagger-edificio-abandonado) |
| Labirinto Noturno | [fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche](https://fierroduque.itch.io/wdl-master-taggerlaberinto-de-noche) |

### Videos:

| Video | Link |
|---|---|
| Trailer Oficial | [youtu.be/KE8L0RL6YC8](https://youtu.be/KE8L0RL6YC8) |
| Gameplay Metro/Tren | [youtube.com/watch?v=dHxB3NoJs1k](https://www.youtube.com/watch?v=dHxB3NoJs1k) |

---

## Estrutura do Repositorio

```
WDL-MASTER-TAGGER-VERSION-METRO-/
├── index.html                          # Menu principal com acesso aos 7 mapas
├── README.md                           # Este documento
├── juego graffiti METRO/               # Maestranza Metro/Tren (Santiago)
│   └── index.html
├── juego graffiti trenes 2/            # NYC Subway Edition
│   └── index.html
├── juego graffiti trenes 3/            # BA Subte Edition
│   └── index.html
├── juego grafiti BODEGA/               # Container 1 / Galpoes Noturnos
│   └── index.html
├── juego grafiti BODEGA FLUOR/         # Laberinto Neon
│   └── index.html
├── juego grafiti EDIFICIO/             # Edificio Abandonado (5 andares)
│   └── index.html
└── juego grafiti LABERINTO/            # Labirinto Noturno
    └── index.html
```

Cada pasta contem um unico `index.html` autonomo. Sin dependencias, sem instalacion. Abri cualquiera en tu navegador y empeza a pintar.

---

<p align="center">
  <em>WDL -- Da rua ao codigo.</em><br>
  <strong>(c) 2025-2026 Eduardo Fierro -- fierroduque.com</strong><br><br>
  <sub>Nao foi utilizada IA generativa na criacao de assets visuais. Feito a mao, linha por linha.</sub>
</p>
