<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Puertas Nave 2</title>
  <style>
    body {
      margin: 0;
      background: url("https://i.postimg.cc/VLJ28D37/PLno-1.jpg") no-repeat center center;
      background-size: contain;
      background-color: #000;
      height: 100vh;
      position: relative;
      font-family: sans-serif;
    }
    .led {
      width: 20px;
      height: 20px;
      border-radius: 50%;
      background-color: gray;
      position: absolute;
      box-shadow: 0 0 8px rgba(0, 0, 0, 0.5);
    }
    /* Posiciones aproximadas */
    #p1 { top: 45%; left: 85%; }
    #p2 { top: 5%; left: 25%; }
    #p3 { top: 35%; left: 10%; }
    #p4 { bottom: 15%; right: 0%; }
    #p5 { bottom: 15%; right: 7%; }
    #p6 { bottom: 15%; right: 14%; }
    #p7 { bottom: 15%; right: 21%; }
    #p8 { bottom: 15%; right: 28%; }
    #p9 { bottom: 15%; right: 35%; }
  </style>
</head>
<body>
  <div id="p1" class="led"></div>
  <div id="p2" class="led"></div>
  <div id="p3" class="led"></div>
  <div id="p4" class="led"></div>
  <div id="p5" class="led"></div>
  <div id="p6" class="led"></div>
  <div id="p7" class="led"></div>
  <div id="p8" class="led"></div>
  <div id="p9" class="led"></div>

  <script>
    const username = "Monitoreo_nave2";
    const total = 9;

    async function actualizarEstados() {
      for (let i = 1; i <= total; i++) {
        try {
          const res = await fetch(`https://io.adafruit.com/api/v2/${username}/feeds/puerta${i}/data/last`);
          const data = await res.json();
          const estado = parseInt(data.value);
          const led = document.getElementById(`p${i}`);
          if (led) led.style.backgroundColor = estado ? "red" : "lime";
        } catch (e) {
          console.error("Error al obtener puerta" + i, e);
        }
      }
    }

    actualizarEstados();
    setInterval(actualizarEstados, 5000); // Actualiza cada 5 seg
  </script>
</body>
</html>
