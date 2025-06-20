# davidmetienesloquito from pathlib import Path
import shutil
import zipfile

# Ruta del archivo MP3 subido
mp3_path = Path("/mnt/data/Soñé.mp3")

# Crear el archivo HTML con el reproductor
html_content = """<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi Página con Música</title>
</head>
<body>
  <h1>Bienvenido a mi página</h1>
  <p>Reproduciendo la canción "Soñé":</p>

  <audio controls autoplay loop>
    <source src="Soñé.mp3" type="audio/mpeg">
    Tu navegador no soporta el elemento de audio.
  </audio>
</body>
</html>
"""

# Guardar el archivo index.html
html_path = Path("/mnt/data/index.html")
html_path.write_text(html_content, encoding="utf-8")

# Crear un archivo ZIP con el MP3 y el HTML
zip_path = Path("/mnt/data/pagina_con_musica.zip")
with zipfile.ZipFile(zip_path, 'w') as zipf:
    zipf.write(mp3_path, arcname="Soñé.mp3")
    zipf.write(html_path, arcname="index.html")

zip_path.name  # Nombre del archivo ZIP generado
