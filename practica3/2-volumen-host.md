# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name contVolum -p 8080:80 -v C:/Users/Usuario/OneDrive/Documentos/carpetahost:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
```
nos sale un error de codigo 403 ya que el acceso esta prohibido.
```
### ¿Qué pasa con el archivo index.html del contenedor?
```
no encuentra el archivo index.html ya que no existe en la carpeta del contenedor y por lo tanto tampoco en la copia local
```
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/abf730c7-9d27-4a8c-b935-5cc809445ee6)

### ¿Qué sucede al ingresar al servidor de nginx?
```
ya se puede visualizar la pagina que se creo a partir del template
```
### Eliminar el contenedor 
```
docker rm contVolum
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
```
ahora si se puede ver la pagina como anteiormente ya se veia con el template escogido.
```

### ¿Qué hace el comando pwd?
```
imprimir la ruta completa del directorio de trabajo actual
```
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

