from pathlib import Path

# Nuevo contenido HTML con ajustes de posición para los indicadores
html_content = """
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Monitoreo Puertas y Ventanas</title>
  <style>
    body {
      margin: 0;
      background: url('https://i.postimg.cc/VLJ28D37/PLno-1.jpg') no-repeat center center fixed;
      background-size: cover;
    }
    .indicator {
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: green;
      border-radius: 50%;
      box-shadow: 0 0 5px black;
    }
    /* Puertas */
    #p1 { top: 72%; left: 95.5%; }
    #p2 { top: 19%; left: 17%; }
    #p3 { top: 88.5%; left: 5.3%; }
    /* Ventanas sobre los números */
    #v1_1 { bottom: 6.5%; left: 85%; }
    #v1_2 { bottom: 6.5%; left: 89%; }
    #v2_1 { bottom: 6.5%; left: 70%; }
    #v2_2 { bottom: 6.5%; left: 74%; }
    #v3_1 { bottom: 6.5%; left: 55%; }
    #v3_2 { bottom: 6.5%; left: 59%; }
  </style>
</head>
<body>
  <div class="indicator" id="p1"></div>
  <div class="indicator" id="p2"></div>
  <div class="indicator" id="p3"></div>
  <div class="indicator" id="v1_1"></div>
  <div class="indicator" id="v1_2"></div>
  <div class="indicator" id="v2_1"></div>
  <div class="indicator" id="v2_2"></div>
  <div class="indicator" id="v3_1"></div>
  <div class="indicator" id="v3_2"></div>
</body>
</html>
"""

# Guardar como index.html
output_path = Path("/mnt/data/index.html")
output_path.write_text(html_content, encoding="utf-8")
output_path

