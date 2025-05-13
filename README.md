# Configurar-n8n-Mac-ARM

### 1. Instala Docker Desktop para Mac (Apple Silicon/M1)
1.	Ve a: https://www.docker.com/products/docker-desktop
2.	Descarga la versión para Mac con chip Apple.
3.	Instálalo y sigue los pasos iniciales (permite permisos y reinicia si lo pide).

## PASOS para guardar todo y que funcione siempre
1. Crea una carpeta para n8n
  ```bash
  mkdir -p ~/n8n-server
  cd ~/n8n-server
  ```
2. Crea un archivo llamado docker-compose.yml
 ```bash
  nano docker-compose.yml
  ```
Y pega esto:
 ```bash
version: '3.1'

services:
  n8n:
    image: n8nio/n8n
    restart: always
    ports:
      - 5678:5678
    volumes:
      - ./data:/home/node/.n8n
    environment:
      - N8N_SECURE_COOKIE=false
      - TZ=Europe/Madrid
  ```
Esto guarda todos tus proyectos en ~/n8n-server/data y arranca n8n automáticamente incluso tras reiniciar el Mac o Docker.

3. Inicia n8n con (la primera vez):
    ```bash
    docker compose up -d
    ```
4. Accede a la interfaz en:
   ```bash
    https://localhost:5678
    ```
5. Para detenerlo o reiniciarlo:

    ```bash
    docker compose stop     # Detener
    docker compose start    # Iniciar de nuevo
    docker compose down     # Apagar y borrar contenedor (los datos se conservan)
    ```
