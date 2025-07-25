
# Iniciar-Servidor-Ngrok

## Descargar e Instalar Ngrok para Linux

Puedes descargar Ngrok desde el sitio oficial: [https://ngrok.com/downloads/linux](https://ngrok.com/downloads/linux)

Ejecuta el siguiente comando para agregar la clave GPG, añadir el repositorio y luego instalar Ngrok:

```bash
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
  | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
  && echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
  | sudo tee /etc/apt/sources.list.d/ngrok.list \
  && sudo apt update \
  && sudo apt install ngrok
```

## Configurar Ngrok con Token

Para autenticar tu cuenta, ve a: [https://dashboard.ngrok.com/get-started/setup/linux](https://dashboard.ngrok.com/get-started/setup/linux)

Y usa tu token de autenticación:

```bash
ngrok config add-authtoken <TOKEN>
```

## Iniciar Servicios

Abre dos terminales o pestañas separadas para ejecutar los siguientes comandos:

1. **Iniciar túnel con Ngrok en el puerto 80:**

```bash
ngrok http 80
```

2. **Iniciar servidor web en el puerto 80:**

```bash
python3 -m http.server 80
```
3. **Visualizar Interfaz Web**

http://127.0.0.1:4040

---

### Ejemplo de uso

```bash
┌──(kali㉿kali)-[~/Desktop/Servidor_XXS]
└─$ ls
test.php   test.txt

┌──(kali㉿kali)-[~/Desktop/Servidor_XXS]
└─$ curl -k https://xxxxx.ngrok-free.app/test.php
Hola mundo

┌──(kali㉿kali)-[~/Desktop/Servidor_XXS]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
127.0.0.1 - - [25/Jul/2025 15:35:06] "GET /test.txt HTTP/1.1" 200 -
127.0.0.1 - - [25/Jul/2025 15:35:51] "GET /test.php HTTP/1.1" 200 -
```

---

## Resultado

En este punto ya se ha creado un servidor web local expuesto a internet mediante Ngrok. Este servidor puede ser utilizado para cargar un payload y realizar peticiones desde un entorno de Cross Site Scripting (XSS).
