[js.$.html](https://github.com/user-attachments/files/22310208/js.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Sorpresa romántica hacker neon</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700&display=swap');

  html, body {
    margin: 0; padding: 0; height: 100%;
    overflow: hidden;
    font-family: 'Orbitron', monospace;
    background: #ffccdd;
    animation: bgColorChange 30s infinite alternate;
    display: flex;
    justify-content: center;
    align-items: center;
    user-select: none;
  }

  @keyframes bgColorChange {
    0% { background: #ffccdd; }
    50% { background: #000000; }
    100% { background: #ffccdd; }
  }

  #mensajeCentral {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #ff33cc;
    font-size: 3.5rem;
    text-align: center;
    text-shadow:
      0 0 8px #ff33cc,
      0 0 20px #ff66ff,
      0 0 30px #ff33cc,
      0 0 40px #ff66ff,
      0 0 50px #ff33cc;
    pointer-events: none;
    user-select: none;
    z-index: 1000;
    transition: opacity 0.8s ease;
  }

  .petalo {
    position: fixed;
    width: 14px;
    height: 20px;
    background: radial-gradient(circle at 30% 30%, #ff0044, #ff66aa);
    border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
    filter: drop-shadow(0 0 5px #ff3399);
    animation: caer 8s linear forwards;
    pointer-events: none;
    opacity: 0.9;
    mix-blend-mode: screen;
  }

  @keyframes caer {
    to {
      transform: translateY(110vh) rotate(720deg);
      opacity: 0;
    }
  }

  /* Textos "Te amo" que flotan */
  .textoFlotante {
    position: fixed;
    font-weight: 900;
    font-size: 1.8rem;
    color: #ff33cc;
    text-shadow:
      0 0 8px #ff33cc,
      0 0 15px #ff66ff,
      0 0 20px #ff33cc;
    pointer-events: none;
    user-select: none;
    animation: floatUp 3s forwards ease-out;
    mix-blend-mode: screen;
  }

  @keyframes floatUp {
    0% { opacity: 1; transform: translateY(0) scale(1); }
    100% { opacity: 0; transform: translateY(-100px) scale(1.3); }
  }

  /* Corazones y partículas en explosión */
  .particula {
    position: fixed;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    pointer-events: none;
    filter: drop-shadow(0 0 3px #ff66cc);
    mix-blend-mode: screen;
    animation: explotar 1.2s ease-out forwards;
  }

  .corazonParticula {
    width: 16px;
    height: 16px;
    background: red;
    transform: rotate(45deg);
    filter: drop-shadow(0 0 5px #ff0044);
    position: fixed;
  }
  .corazonParticula::before,
  .corazonParticula::after {
    content: "";
    position: absolute;
    width: 16px;
    height: 16px;
    background: red;
    border-radius: 50%;
  }
  .corazonParticula::before {
    top: -8px;
    left: 0;
  }
  .corazonParticula::after {
    top: 0;
    left: -8px;
  }

  @keyframes explotar {
    0% {
      opacity: 1;
      transform: translate(0, 0) scale(1);
    }
    100% {
      opacity: 0;
      transform: translate(var(--x), var(--y)) scale(0.4);
    }
  }
</style>
</head>
<body>

<div id="mensajeCentral"></div>

<script>
  // Frases bonitas para texto central rotativo
  const frases = [
    "Eres mi todo💖",
    "Contigo, cada día es un regalo.",
    "Eres mi luz en la oscuridad.",
    "Juntos somos invencibles.",
    "Tu sonrisa ilumina mi mundo.",
    "Eres mi sueño hecho realidad.",
    "Cada momento contigo es eterno.",
    "Amarte es mi mayor alegría.",
    "Eres mi paz y mi locura.",
    "Mi corazón late solo por ti.",
    "A tu lado todo es mejor.",
    "Eres mi inspiración diaria.",
    "Sin ti, no soy nada.",
    "Te amo más allá de las palabras.",
    "Eres mi razón para sonreír.",
    "En tus ojos veo mi futuro.",
    "Eres mi más dulce adicción.",
    "Amarte es respirar.",
    "Eres la melodía de mi vida.",
    "Contigo aprendí a amar sin miedo.",
    "Eres mi refugio y mi hogar.",
    "Cada día te quiero más.",
    "Eres mi alegría constante.",
    "Tu amor me hace fuerte.",
    "Eres la magia en mi realidad.",
    "Sin ti, el mundo no tiene color.",
    "Eres mi mitad perfecta.",
    "Amarte es mi destino.",
    "Eres mi razón para luchar.",
    "Juntos escribimos nuestra historia.",
    "Eres mi todo y más.",
    "En ti encontré mi paraíso.",
    "Tu amor es mi energía.",
    "Eres mi sol en días nublados.",
    "Cada instante contigo es único.",
    "Eres la luz que guía mi camino.",
    "Amarte es un hermoso viaje.",
    "Eres mi fuerza y mi debilidad.",
    "Contigo, el tiempo se detiene.",
    "Eres mi eterno verano.",
    "Tu sonrisa es mi felicidad.",
    "Eres el sueño que no quiero despertar.",
    "Amarte es mi aventura favorita.",
    "Eres mi calma y mi tormenta.",
    "Cada latido es por ti.",
    "Eres mi felicidad completa.",
    "Juntos somos infinito.",
    "Eres el amor que siempre esperé.",
    "Contigo todo tiene sentido.",
    "Eres mi razón de ser."
  ];

  const mensajeCentral = document.getElementById("mensajeCentral");
  let index = 0;

  function mostrarFrase() {
    mensajeCentral.style.opacity = 0;
    setTimeout(() => {
      mensajeCentral.textContent = frases[index];
      mensajeCentral.style.opacity = 1;
      index = (index + 1) % frases.length;
    }, 800);
  }

  mostrarFrase();
  setInterval(mostrarFrase, 5000); // Cambia frase cada 5 segundos

  // Crear lluvia de pétalos estilo hacker
  function crearPetalo() {
    const petalo = document.createElement("div");
    petalo.className = "petalo";

    // Posición horizontal aleatoria en toda la pantalla
    petalo.style.left = Math.random() * window.innerWidth + "px";
    petalo.style.top = "-30px";

    document.body.appendChild(petalo);

    // Animación caer definida en CSS, remover después de 8s
    setTimeout(() => {
      petalo.remove();
    }, 8000);
  }

  // Crear lluvia constante
  setInterval(crearPetalo, 180);

  // Texto "Te amo" flotante al arrastrar dedo o mouse
  function crearTextoFlotante(x, y) {
    const texto = document.createElement("div");
    texto.className = "textoFlotante";
    texto.textContent = "Te amo";
    texto.style.left = x + "px";
    texto.style.top = y + "px";

    document.body.appendChild(texto);

    setTimeout(() => {
      texto.remove();
    }, 3000);
  }

  // Explosión automática de partículas y corazones
  function crearParticula() {
    const particula = document.createElement("div");
    particula.className = "particula";

    // Colores alternados rojo/neon
    particula.style.background = `hsl(, 80%, 65%)`;

    // Posición central random (puedes ajustar)
    const x0 = window.innerWidth / 2 + (Math.random() - 0.5) * 200;
    const y0 = window.innerHeight / 2 + (Math.random() - 0.5) * 100;

    particula.style.left = x0 + "px";
    particula.style.top = y0 + "px";

    // Movimiento random con variables CSS
    const angle = Math.random() * 2 * Math.PI;
    const distance = 80 + Math.random() * 60;
    particula.style.setProperty("--x", `px`);
    particula.style.setProperty("--y", `px`);

    document.body.appendChild(particula);
    setTimeout(() => particula.remove(), 1200);

    // A veces crear corazón
    if (Math.random() < 0.3) {
      const corazon = document.createElement("div");
      corazon.className = "particula corazonParticula";
      corazon.style.left = x0 + "px";
      corazon.style.top = y0 + "px";
      corazon.style.setProperty("--x", `px`);
      corazon.style.setProperty("--y", `px`);
      document.body.appendChild(corazon);
      setTimeout(() => corazon.remove(), 1200);
    }
  }

  // Explosiones automáticas periódicas
  setInterval(crearParticula, 600);

  // Manejo de arrastre con mouse y touch para crear textos flotantes
  let isDragging = false;

  function onPointerDown(e) {
    isDragging = true;
    crearTextoFlotante(e.clientX, e.clientY);
  }

  function onPointerMove(e) {
    if (isDragging) {
      crearTextoFlotante(e.clientX, e.clientY);
    }
  }

  function onPointerUp(e) {
    isDragging = false;
  }

  window.addEventListener("mousedown", onPointerDown);
  window.addEventListener("mousemove", onPointerMove);
  window.addEventListener("mouseup", onPointerUp);

  window.addEventListener("touchstart", e => {
    onPointerDown(e.touches[0]);
  }, {passive:true});
  window.addEventListener("touchmove", e => {
    onPointerMove(e.touches[0]);
  }, {passive:true});
  window.addEventListener("touchend", onPointerUp);
</script>

</body>
</html>
