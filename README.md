# Configurar-n8n-Mac-ARM

### 1. Instala Docker Desktop para Mac (Apple Silicon/M1)
1.	Ve a: https://www.docker.com/products/docker-desktop
2.	Descarga la versión para Mac con chip Apple.
3.	Instálalo y sigue los pasos iniciales (permite permisos y reinicia si lo pide).

### 2. Lanza n8n con Docker (sin Node.js ni instalar nada global)
1.	Crea una carpeta para tus datos de n8n:
```bash
mkdir -p ~/n8n/data
```
2.	Crea y lanza el contenedor de n8n:
```bash
docker run -it --rm \
  -p 5678:5678 \
  -v ~/n8n/data:/home/node/.n8n \
  n8nio/n8n
```
Esto hará lo siguiente:
* Abre el puerto 5678, que es donde corre la interfaz web de n8n.
* Monta una carpeta local para que tus datos persistan.
* Corre n8n temporalmente (se borrará cuando cierres).

> [!TIP]
> Si quieres que n8n quede corriendo siempre, podemos usar un docker-compose.yml.
