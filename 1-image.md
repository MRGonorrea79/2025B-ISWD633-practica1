# Imagen
### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
# COMPLETAR
docker pull hello-world

**¿Qué es nginx**
# COMPLETAR 
NGINX (se pronuncia engine-x) es un servidor web de alto rendimiento que también puede funcionar como:

* Proxy inverso: recibe solicitudes de clientes y las redirige a uno o varios servidores backend.
* Balanceador de carga: distribuye el tráfico entre varios servidores para mejorar rendimiento y disponibilidad.
* Proxy de correo (IMAP, POP3, SMTP).
* Caché HTTP: almacena contenido en caché para reducir la carga en los servidores y acelerar las respuestas.

Fue creado en 2004 por el desarrollador ruso Igor Sysoev y es software libre bajo la licencia BSD de 2 cláusulas.

Hoy en día, NGINX es uno de los servidores web más utilizados en el mundo, tanto para servir directamente contenido estático (imágenes, HTML, CSS, etc.), como para trabajar junto con aplicaciones web (Node.js, Django, Flask, PHP, etc.) y mejorar escalabilidad.

Descargar la imagen  **nginx** en la versión **alpine**
# COMPLETAR
docker pull nginx:alpine
### Listar imágenes

```
docker images
```

# COLOCAR UNA CAPTURA DE PANTALLA DEL RESULTADO 
<img width="736" height="84" alt="image" src="https://github.com/user-attachments/assets/fb159322-1202-41e1-92cb-cc72ea7a2a3e" />

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
# COMPLETAR
docker inspect hello-world

**¿Con qué algoritmo se está generando el ID de la imagen**
# COMPLETAR
El ID de una imagen en Docker se genera utilizando el algoritmo SHA-256 (Secure Hash Algorithm 256 bits).
* Cada capa de la imagen se identifica mediante un digest único en formato sha256:<hash>.

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
# COMPLETAR
docker rmi hello-world:latest

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```
docker rmi -f hello-world:latest
