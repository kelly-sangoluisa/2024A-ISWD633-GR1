# Mapeo de Puertos 
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
```
docker run -d --publish published=8080,target=8080 jenkins/jenkins:alpine3.18-jdk11
```
Acceso a http://localhost:8080
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/a36129c9-d926-467a-b4cd-72035563f0a1)



### ¿Cómo obtener la contraseña solicitada?
Para obtener la contraseña solicitada es necesario ingresar al contenedor.

![Imagen](imagenes/jenkins.PNG)

# Operaciones con contenedores

### Ejecutar un comando en un contenedor de Docker en ejecución
```
docker exec <nombre contenedor> <comando> <argumentos opcionales>
```

### ¿Para qué se usa el comando ls?
enlistar los archivos y directorios contenidos en un directorio. 

### ¿Para qué sirve el argumento -l junto al comando ls?
 listar el contenido de un directorio en formato de lista larga, proporcionando detalles adicionales sobre cada archivo o directorio.

### Usar el contenedor de jenkins creado previamente y ejecutar el comando ls con el argumento -l
```
docker exec a9a380cf34d8b95a150bca3b35a1ff08f8837a6ba215cf9fb8ec5ac866bea2e9 ls -l
```
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/528c3e0b-175c-4b0c-962d-57f3e9ad68f0)



### Para ejecutar un shell interactivo en un contenedor de Docker especificado.
El comando **docker exec** te permite acceder a la sesión shell de un contenedor en ejecución, estarás dentro del contenedor y podrás ejecutar comandos como si estuvieras en una terminal normal. 
Para saber qué comando utilizar para abrir una terminal dentro de un contenedor, es útil conocer la imagen base del contenedor, ya que diferentes imágenes pueden usar diferentes shells o comandos para abrir una terminal. Puedes verificar la documentación de la imagen del contenedor en Docker Hub o en el repositorio de la imagen para obtener información específica sobre cómo abrir una terminal en esa imagen.
- Para imágenes basadas en Debian o Ubuntu, puedes probar con bash.
- Para imágenes basadas en Alpine Linux, puedes probar con sh.
![Imagen](imagenes/jenkins-i.PNG)
```
docker exec -i <nombre contenedor> <programa o comando>
```
-i: mantiene abierta la entrada estándar (stdin) del contenedor. Esto significa que puedes enviar datos al proceso que se está ejecutando en el contenedor a través de la terminal local. *Sin embargo, esto no asigna un terminal al contenedor, por lo que no podrás ver la salida del proceso de forma interactiva.*

### Ejecutar una de las siguientes instrucciones
```
docker exec -i <nombre contenedor> /bin/bash 
```
ó
```
docker exec -i <nombre contenedor> bash 
```
**Considerar**
- /bin/bash: Al especificar la ruta completa del shell, Docker buscará el ejecutable /bin/bash en el sistema de archivos del contenedor y lo ejecutará. Esto es útil cuando quieres asegurarte de que se está utilizando un shell específico que está ubicado en una ubicación conocida en el sistema de archivos del contenedor. 
- bash: Al especificar solo el nombre del shell, Docker buscará el comando bash en las rutas del sistema (por lo general, en las rutas definidas en la variable de entorno PATH) del contenedor y lo ejecutará. Esto asume que bash está disponible en alguna de las rutas del sistema definidas en el contenedor.

Ejecutar
```
echo "Hola mundo"
```

Ejecutar
```
whoami
```
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/29cecdf9-1f98-4780-ad8a-a3017d2bb7a2)


**Si se visualiza el mensaje command not found, considerar**
El problema se debe a que no se ha asignado un terminal de salida al contenedor al ejecutar el comando. Cuando usas docker exec -i jenkins-server /bin/bash en Windows, el comando se ejecuta pero no hay un terminal asignado para mostrar la salida del comando ls.


### Para ejecutar un shell interactivo bidireccional en un contenedor de Docker especificado.
Ejecutar un shell interactivo bidireccional en un contenedor de Docker significa abrir una sesión de shell en el contenedor que permite la interacción bidireccional entre la terminal local y el contenedor. Es decir, puedes enviar comandos desde tu terminal local al contenedor y recibir la salida de esos comandos de vuelta en tu terminal local, al igual que si estuvieras trabajando directamente en la terminal del contenedor.

![Imagen](imagenes/jenkins-it.PNG)
```
docker exec -i-t <nombre contenedor> <programa o comando>
```
ó
```
docker exec -it <nombre contenedor> <programa o comando>
```

### Ahora puedes acceder al contenedor de jenkins y obtener la contraseña ubicada en /var/jenkins_home/secrets/initialAdminPassword
```
docker exec -it a9a380cf34d8b95a150bca3b35a1ff08f8837a6ba215cf9fb8ec5ac866bea2e9 cat /var/jenkins_home/secrets/initialAdminPassword
f0c5d6f6c1ac4442b000d3708a590853
```
###Ventana que aparece después de colocar la contraseña.
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/c4a15c4c-b4ad-468e-a9d8-c007577627f6)


**Para este punto no es necesario continuar con la instalación de Jenkins**


### Para ver los logs de un contenedor

```
docker logs n <cantidad de líneas> <nombre o id del contenedor> 
```
-t: para incluir la fecha y la hora





