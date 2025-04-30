<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Racing+Sans+One&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Racing+Sans+One&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Racing+Sans+One&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<script>
  import * as d3 from "d3";
  let contenedorPilotos;

  function getFixedOffset(i, amplitud, base) {
  const patrones = [0, 1.2, -1.3, 2.1, -2.2, 3, -3.1, 4.2, -4.3, 5.2];
  return base + patrones[i % patrones.length] * amplitud;
}

function getDispersedOffset(i, base, amplitud) {
  const salto = [0, 1.7, -2.2, 2.5, -1.3, 3.3, -2.6, 4.1, -3.2, 2.9];
  return base + salto[i % salto.length] * amplitud;
}

  import { onMount } from "svelte";

  onMount(() => {
  if (contenedorPilotos) {
    contenedorPilotos.scrollLeft = contenedorPilotos.scrollWidth;
  }
});
  let datos = [
    { categoria: "Max Verstappen", valor: 24 },
    { categoria: "Jim Clark", valor: 33 },
    { categoria: "Niki Lauda", valor: 42 },
    { categoria: "Fernando Alonso", valor: 54 },
    { categoria: "Sebastian Vettel", valor: 63 },
    { categoria: "Alain Prost", valor: 71 },
    { categoria: "Ayrton Senna", valor: 77 },
    { categoria: "Juan Manuel Fangio", valor: 87 },
    { categoria: "Michael Schumacher", valor: 92 },
    { categoria: "Lewis Hamilton", valor: 98 },

    { categoria: "Esteban Ocon", valor: 23 },
    { categoria: "Oscar Piastri", valor: 25 },
    { categoria: "Carlos Sainz", valor: 28 },
    { categoria: "Sergio Pérez", valor: 32 },
    { categoria: "George Russell", valor: 35 },
    { categoria: "Lando Norris", valor: 38 },
    { categoria: "Charles Leclerc", valor: 43 },
    { categoria: "Fernando Alonso", valor: 45 },
    { categoria: "Max Verstappen", valor: 50 },
    { categoria: "Lewis Hamilton", valor: 56 }
  ];

  const maxValor = Math.max(...datos.map(d => d.valor));

  const colorScale = d3.scaleLinear()
    .domain([0, 100])
    .range(["yellow", "red"]);

  const sizeScale = d3.scaleLinear()
    .domain([0, 100])
    .range([10, 25]);

  function getColor(n) {
    return colorScale(n);
  }

  function getSize(n) {
    return sizeScale(n);
  }

  function getRandomY() {
    return Math.floor(Math.random() * 450);
  }

  function scrollTabla(direccion) {
  const anchoCelda = 202;
  contenedorPilotos.scrollLeft += direccion * anchoCelda * 2;
}
</script>

<header class="f1-header">
  <div class="header-content">
    <div class="logo-section">
      <div class="f1-logo-wrapper">
        <a href="https://www.formula1.com" target="_blank" rel="noopener noreferrer">
          <img src="/images/f1_logo.png" alt="F1 Logo" class="f1-logo" />
        </a>
      </div>
    </div>
    <div class="container">
      <nav class="nav-menu">
        <a href="#comparacion">COMPARACIÓN</a>
        <a href="#analisis">ANÁLISIS</a>
        <a href="#integrantes">INTEGRANTES</a>
      </nav>
    </div>
  </div>
</header>

<main>

  <h1 id="comparacion" class="main-title">LOS MEJORES DE LA HISTORIA</h1>
  <h3 class="subtitulo">
    La <span class="resaltado">GRANDEZA</span> en la Fórmula 1 se construye en la consistencia, la presión y la capacidad de evolucionar. A continuación, se presenta una visualización comparativa que reúne a los principales referentes históricos y actuales de este deporte. Su propósito es ilustrar el impacto relativo de cada piloto en función de sus campeonatos mundiales ganados.
  </h3>
  
  <div class="tabla-pilotos-con-flechas">
    <div class="flecha izquierda" on:click={() => scrollTabla(-1)}>‹</div>
  
    <div class="tabla-pilotos" bind:this={contenedorPilotos}>
  
  <div class="celda">
    <img src="/images/ocon.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Esteban Ocon</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/pias.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Oscar Piastri</p>
    </div>
  </div>
  
  
  <div class="celda">
    <img src="/images/sainz.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Carlos Sainz</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/perez.webp" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Sergio Pérez</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/clark.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Jim Clark</p>
    </div>
  </div>
      
  <div class="celda">
    <img src="/images/russell.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">George Russell</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/norris.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Lando Norris</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/lauda.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Niki Lauda</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/leclerc.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Charles Leclerc</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/max.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Max Verstappen</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/alonso.avif" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Fernando Alonso</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/seba.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Sebastian Vettel</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/prost.webp" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Alain Prost</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/senna.webp" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Ayrton Senna</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/fangio.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Juan M. Fangio</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/schum.jpg" alt="Juan Manuel Fangio" class="imagen-piloto">
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Michael Schumacher</p>
    </div>
  </div>
  
  <div class="celda">
    <img src="/images/hamilton.avif" alt="Lewis Hamilton" class="imagen-piloto" />
    <div class="nombre-rectangulo">
      <p class="nombre-piloto-tabla">Lewis Hamilton</p>
    </div>
  </div>
  </div>
  
  
  
    <div class="flecha derecha" on:click={() => scrollTabla(1)}>›</div>
  </div>
  
  <h3 class="titulo-de-carrera">
  Qué pasaría si todos ellos compitiesen en una carrera...
  </h3>
  
  <div class="race-track">
    <div class="grupo-label historicos-label">HISTÓRICOS</div>
    <div class="grupo-label actuales-label">ACTUALES</div>
    <div class="finish-line">
  </div>
  
    {#each datos.slice(0, 10) as dato, i}
    <div class="car-container" style="left: {(dato.valor * 0.902)}%; top: {getFixedOffset(i, 15, 170)}px;">
        <svg width="60" height="60" class="circle-svg">
          <circle cx="30" cy="30" r="{getSize(dato.valor)}" fill="{getColor(dato.valor)}" />
          <text x="30" y="35" text-anchor="middle" fill="black" font-size="14px" font-weight="bold">
            {dato.valor}
          </text>
        </svg>
        <img class="car" src="/images/old.png" alt="Car" />
        <div class="nombre-piloto">{dato.categoria}</div>
        {#if dato.valor === maxValor}
          <div class="trophy">🏆</div>
        {/if}
      </div>
    {/each}
  
    {#each datos.slice(10, 20) as dato, i}
      <div class="car-container" style="left: {(dato.valor * 0.902)}%; top: {getDispersedOffset(i, 580, 35)}px;">
        <svg width="60" height="60" class="circle-svg">
          <circle cx="30" cy="30" r="{getSize(dato.valor)}" fill="{getColor(dato.valor)}" />
          <text x="30" y="35" text-anchor="middle" fill="black" font-size="14px" font-weight="bold">
            {dato.valor}
          </text>
        </svg>
        <img class="car" src="/images/new.png" alt="Car" />
        <div class="nombre-piloto">{dato.categoria}</div>
        {#if dato.valor === 56}
          <div class="trophy">🏆</div>
        {/if}
      </div>
    {/each}
  </div>
  
  <p class="interpretacion">
    Logramos ver que mientras los mejores pilotos de la actualidad demuestran un nivel similar entre sí, hay una gran disparidad
    entre los mejores pilotos de Fórmula 1 de la historia. Veámoslo mejor con <span class="resaltado">GRÁFICOS</span>...
  </p>
  
  <h3 class ="titulo-g1">
    DIAGRAMA DE DISPERSIÓN
  </h3>
  
  <div class="chart-wrapper">
    <div class="flourish-embed flourish-chart" data-src="visualisation/22677797">
      <script src="https://public.flourish.studio/resources/embed.js"></script>
      <noscript>
        <img src="https://public.flourish.studio/visualisation/22677797/thumbnail" width="100%" alt="Gráfico de Flourish" />
      </noscript>
    </div>
  </div>

  <h3 class ="titulo-g2">
    GRÁFICO DE BARRAS APILADAS HORIZONTALES
  </h3>
  
  <div class="chart-wrapper">
    <div class="flourish-embed flourish-chart" data-src="visualisation/22677872">
      <script src="https://public.flourish.studio/resources/embed.js"></script>
      <noscript>
        <img src="https://public.flourish.studio/visualisation/22677872/thumbnail" width="100%" alt="chart visualization" />
      </noscript>
    </div>
  </div>
</main>

<footer class="footer">
  <div class="footer-content"></div>
    <p>Proyecto para la materia <strong>Visualización de Datos</strong> – Universidad Torcuato Di Tella</p>
    <p>Carrera: <strong>Licenciatura en Tecnología Digital</strong></p>
    <div class="integrantes">
      <p><strong>Integrante/s:</strong></p>
      <ul>
        <li>
          Alexander Melnikov – 
          <a href>LinkedIn</a> | 
          <a href>GitHub</a>
        </li>
      </ul>
    </div>
</footer>

<style>
  html {
    scroll-behavior: smooth;
  }

  .main-title {
    text-align: center;
    font-family: 'Anton', sans-serif;
    font-size: 4.7rem;
    margin-top: 25px;
    color: #000000;
  }

  .titulo-de-carrera {
    text-align:center;
    font-size: 2.7rem;
    font-family: 'Anton', sans-serif;

    color: #000000;
    margin-top: 60px;
    margin-bottom: 25px;
  }

  .titulo-g1 {
    text-align:center;
    font-size: 2rem;
    font-family: 'Anton', sans-serif;
    font-style: italic;
    color: #000000;
    margin-top: 45px;
    margin-bottom: 25px;
  }

  .titulo-g2 {
    text-align:center;
    font-size: 2rem;
    font-family: 'Anton', sans-serif;
    font-style: italic;
    color: #000000;
    margin-top: 30px;
    margin-bottom: 25px;
  }

  .subtitulo {
    text-align:justify;
    font-size: 1.5rem;
    font-family: 'Arial', sans-serif;
    font-style: italic;
    color: #000000;
    margin-top: 30px;
    margin-bottom: 25px;
  }

  .race-track {
    position: relative;
    width: 100%;
    height: 800px;
    background: url('/images/HH.png') no-repeat center center;
    background-size: 100% 100%;
    border: 2px solid black;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 10%;
    margin-top: 5px;
  }

  .car-container {
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
  }

  .car {
    width: 90px;
    height: 50px;
    transform: rotate(0deg);
  }

  .nombre-piloto {
    margin-top: 4px;
    font-size: 0.77rem;
    font-weight: bold;
    color: white;
    text-shadow: 0 0 2px black;
  }

  .finish-line {
    position: absolute;
    right: 5%;
    width: 10px;
    height: 100%;
    background: repeating-linear-gradient(white, white 5px, black 5px, black 15px);
  }

  .trophy {
    font-size: 20px;
    margin-top: 5px;
  }

  .interpretacion {
    text-align:justify;
    font-size: 1.5rem;
    font-family: 'Arial', sans-serif;
    font-style: italic;
    color: #000000;
    margin-top: 45px;
    margin-bottom: 25px;
  }

  .resaltado {
    font-weight: bold;
    color:#e10600;
  }

  .chart-wrapper {
    max-width: 1100px;
    margin: 40px auto 60px auto;
    margin-top: -20px;
  }

  .cierre-final {
    max-width: 900px;
    margin: 60px auto 100px auto;
    text-align: center;
    font-size: 1.1rem;
    line-height: 1.6;
    font-family: 'Arial', sans-serif;
    color: #000000;
    background-color: #ffffff;
    padding: 20px 30px;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.3);
  }

  .footer {
    background-color: #222;
    color: #fff;
    padding: 30px 20px;
    text-align: center;
    font-family: 'Arial', sans-serif;
    font-size: 0.95rem;
    border-top: 2px solid #aaa;
    width: 100vw; /* Ocupa el 100% del viewport */
    position: relative;
    left: 50%; /* Centrado forzado */
    right: 50%; /* Centrado forzado */
    margin-left: -50.5vw; /* Compensa el desplazamiento */
    margin-right: -50.5vw; /* Compensa el desplazamiento */
    box-sizing: border-box; /* Evita que el padding afecte el ancho */
}

  .footer-content {
  max-width: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
}

  .footer a {
    color: #1e90ff;
    text-decoration: none;
  }

  .footer a:hover {
    text-decoration: underline;
  }

  .integrantes ul {
    list-style: none;
    padding: 0;
    margin-top: 10px;
  }

  .integrantes li {
    margin: 5px 0;
  }

  .f1-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 8.5%;
    background: #e10600;
    z-index: 1000;
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    color: white;
    margin-top: -4px;
  }

  .logo-section {
  display: flex;
  align-items: center;
  gap: 12px;
  }

  .f1-logo-wrapper {
    display: flex;
    align-items: center;
    height: 100%;
  }

  .f1-logo {
    width: 200px;
    height: auto;
    filter: brightness(0) invert(1); /* logo blanco */
    transition: opacity 0.3s ease;
    display: block;
    margin-left: 90px;
    margin-top: -2px;
  }

  .f1-logo:hover {
    opacity: 0.7;
  }

  .project-title {
    font-size: 1.6rem;
    color: white;
    text-shadow: 1px 1px 2px black;
  }

  .nav-menu a {
    color: white;
    text-decoration: none; /* ✅ quita subrayado nativo */
    margin-left: 10px;
    font-size: 1.15rem;
    position: relative;
    padding: 10px 25px;
    font-weight: 600;
  }

  .nav-menu a {
    position: relative;
    display: inline-block; /* ✅ clave para que el ancho sea el del texto */
    text-decoration: none;
    padding: 10px 0;        /* ✅ solo padding vertical */
    margin: 0 20px;         /* separación horizontal entre ítems */
    color: white;
    font-size: 1.15rem;
    font-weight: 600;
  }

  .nav-menu a::after {     /* BARRA GRUESAA */
    content: "";
    position: absolute;
    bottom: 7px;     /* separación con el texto */
    left: 0;         /* empieza justo donde empieza el texto */
    width: 100%;     /* ✅ exactamente mismo ancho que el texto */
    height: 4px;
    background-color: black;
    display: none;   /* aparece solo en hover/activo */
  }

/* Estilo al hacer hover o cuando está activo */
.nav-menu a:hover,
.nav-menu a.active {
  color: black;
}

.nav-menu a:hover::after,
.nav-menu a.active::after {
  display: block;
}

  .container {
  max-width: 1200px; /* o el ancho de tu rectángulo gris */
  margin: 0 auto; /* centra horizontalmente */
  padding: 0 30px; /* margen interno a izquierda y derecha */
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-right: 37px;
}

.tabla-pilotos-con-flechas {
  display: flex;
  align-items: stretch;
  justify-content: center;
  width: 1280px; /* mismo ancho que tu .container y .race-track */
  margin: 40px auto 0 auto;
  border: 4px solid black;
  background-color: #800000;
  box-sizing: border-box;
  height: 300px; /* Aumentada para dar más presencia */

}

.flecha {
  font-size: 60px;
  color: black;
  cursor: pointer;
  user-select: none;
  padding: 10px 20px;
  background-color: #e10600;

  font-weight: bold;
  transition: background-color 0.3s;
  display: flex;
  justify-content: center;
  align-items: center;
}

.flecha:hover {
  background-color: #c40000;
}

.tabla-pilotos {
  display: flex;
  overflow-x: hidden;
  scroll-behavior: smooth;
  height: 100%;
  width: 100%;
}

.celda {
  flex: 0 0 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  border-left: 2px solid black;
  padding: 0;
  box-sizing: border-box;
  position: relative; /* ✅ necesario para posicionar el rectángulo */
  overflow: hidden;   /* ✅ asegura que no se salga nada */
  height: 100%;       /* ✅ asegura altura consistente */
}

.celda:first-child {
  border-left: none; /* la primera no necesita borde izquierdo extra */
}

.imagen-piloto {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.nombre-rectangulo {
  background-color: black;
  padding: 5px 8px;           /* Reduce ancho del rectángulo negro */
  display: inline-block;       /* Para que el ancho se ajuste al contenido */
  position: absolute;
  bottom: 15px;                /* ✅ Subís el nombre más arriba */
  left: 50%;                   /* Centrado horizontal */
  transform: translateX(-50%); /* Centrado real */

}

.nombre-piloto-tabla {
  white-space: nowrap;
  font-family: 'Rajdhani', sans-serif;
  font-weight: 700;
  font-size: 1.2rem;
  text-align: center;
  color: white;
  margin: 0;
}

.grupo-label {
  position: absolute;
  font-size: 2.3rem;
  font-weight: bold;
  font-family: 'Anton', sans-serif;
  color: white;
  text-shadow: 2px 2px 5px black;
  background-color: rgba(0, 0, 0, 0.4);
  padding: 10px 20px;
  z-index: 5;
}

.historicos-label {
  top: 0px;
  left: 7.5%;
  transform: translateX(-50%);
}

.actuales-label {
  bottom: 0px;
  left: 6.8%;
  transform: translateX(-50%);
}
body {
  margin: 0;
  padding: 0;
  width: 100vw;
  overflow-x: hidden; /* evita scroll horizontal indeseado */
}
</style>

