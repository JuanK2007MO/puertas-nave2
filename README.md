# Volver a generar el archivo después del reinicio de entorno

html_content = """
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Monitor de Puertas - Nave 2</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: url('https://i.postimg.cc/VLJ28D37/PLno-1.jpg') no-repeat center center fixed;
      background-size: cover;
      font-family: Arial, sans-serif;
    }

    .puerta {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      position: absolute;
      border: 2px solid #333;
      background-color: grey;
    }

    .abierta {
      background-color: red;
    }

    .cerrada {
      background-color: green;
    }
  </style>
</head>
<body>

  <!-- Indicadores -->
  <div id="p1" class="puerta" style="top: 50%; right: 5%;"></div>
  <div id="p2" class="puerta" style="top: 10%; left: 25%;"></div>
  <div id="p3" class="puerta" style="top: 55%; left: 5%;"></div>

  <!-- Ventanas inferiores: v1.1 a v3.3 -->
  <div id="v1" class="puerta" style="bottom: 15%; right: 5%;"></div>
  <div id="v2" class="puerta" style="bottom: 15%; right: 20%;"></div>
  <div id="v3" class="puerta" style="bottom: 15%; right: 35%;"></div>
  <div id="v4" class="puerta" style="bottom: 15%; right: 50%;"></div>
  <div id="v5" class="puerta" style="bottom: 15%; right: 65%;"></div>
  <div id="v6" class="puerta" style="bottom: 15%; right: 80%;"></div>

  <script>
    const FEEDS = {
      p1: "puerta1",
      p2: "puerta2",
      p3: "puerta3",
      v1: "puerta4",
      v2: "puerta5",
      v3: "puerta6",
      v4: "puerta7",
      v5: "puerta8",
      v6: "puerta9"
    };

    const AIO_USER = "Monitoreo_nave2";
    const AIO_KEY = "aio_Kivk92HR4NOpKVtlhjV5ZuuCQY9y";

    function actualizarPuertas() {
      for (const id in FEEDS) {
        const feed = FEEDS[id];
        fetch(`https://io.adafruit.com/api/v2/${AIO_USER}/feeds/${feed}/data/last`, {
          headers: { "X-AIO-Key": AIO_KEY }
        })
        .then(r => r.json())
        .then(data => {
          const valor = data.value === "1" ? "cerrada" : "abierta";
          const el = document.getElementById(id);
          el.classList.remove("abierta", "cerrada");
          el.classList.add(valor);
        })
        .catch(e => console.error("Error con", feed, e));
      }
    }

    actualizarPuertas();
    setInterval(actualizarPuertas, 5000);
  </script>
</body>
</html>
"""

file_path = "/mnt/data/index.html"
with open(file_path, "w", encoding="utf-8") as f:
    f.write(html_content)

file_path
