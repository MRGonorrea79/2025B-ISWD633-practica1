<img width="1868" height="875" alt="image" src="https://github.com/user-attachments/assets/f97776eb-e89e-4094-8691-02841354c638" /># Mapeo de puertos
El mapeo de puertos es un mecanismo que permite redirigir el tráfico de red desde un puerto en el host (tu máquina local o servidor) hacia un puerto específico en un contenedor Docker.
Por ejemplo, supongamos que tienes un contenedor que ejecuta un servidor web en el puerto 80 dentro del contenedor, pero quieres acceder a ese servidor desde tu navegador en la máquina host. Puedes usar el mapeo de puertos para redirigir el tráfico del puerto 80 del contenedor al puerto 3000 en el host. De esta manera, cuando accedas a http://localhost:3000 en tu navegador, el tráfico se dirigirá al servidor web dentro del contenedor en el puerto 80.

![mapeo](mapeoPuertos.PNG)

### Para crear un mapeo de puertos (puerto host y puerto contenedor)
El mapeo de puertos se especifica al ejecutar un contenedor Docker utilizando la opción -p o --publish seguida de los puertos que deseas mapear
```
docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>

```
Crear un contenedor a partir de la imagen nginx version alpine con el mapeo de puertos del ejemplo gráfico, host 3000 y contenedor 80
# COMPLETAR
docker run -d --name serverWeb -p 3000:80 nginx:alpine
# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:3000
<img width="955" height="805" alt="image" src="https://github.com/user-attachments/assets/4e488381-d2ae-493f-ab6c-90c53213bcdf" />

### Para mapear más de un puerto

```
docker run -d --name <nombre contenedor> -p <puerto host 01>:<puerto contenedor 01> -p <puerto host 02>:<puerto contenedor 02> <nombre imagen>:<tag>
```

Crear un contenedor a partir de la imagen rabbitmq version management-alpine, para este mapeo de puertos usar en el host los mismos puertos del contenedor.
# COMPLETAR
docker run -d --name srv-rabbit -p 5672:5672 -p 15672:15672 rabbitmq:management-alpine

### Usando una forma más semántica cuando se especifican puertos

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> <nombre imagen>:<tag> 
```
### Publicando todos los puertos
```
docker run -P -d --name <nombre contenedor> <nombre imagen>:<tag> 
```

-P: le indica a Docker que asigne automáticamente puertos aleatorios en tu host para todos los puertos expuestos por el contenedor.

**Recordar**
No puedes mapear puertos a un contenedor existente directamente después de su creación con Docker. El mapeo de puertos debe especificarse en el momento de crear y ejecutar el contenedor.

### Crear contenedor de Jenkins puertos contenedor: 8080 (interface web) y 50000 (comunicación entre nodos) imagen: jenkins/jenkins:alpine3.18-jdk11
# COMPLETAR
docker run -d --name srv-jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:alpine3.18-jdk11
# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:8080
<img width="1569" height="861" alt="image" src="https://github.com/user-attachments/assets/6ea45d48-0395-400e-963e-dff378e3016c" />

### ¿Cómo obtener la contraseña solicitada?
Para obtener la contraseña solicitada es necesario ingresar al contenedor.
docker exec -it srv-jenkins cat /var/jenkins_home/secrets/initialAdminPassword
7eca5003800a44fdbe4f86ce7b0a9638
7eca5003800a44fdbe4f86ce7b0a9638

![Imagen](jenkins.PNG)

