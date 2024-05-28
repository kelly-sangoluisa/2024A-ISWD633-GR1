# Variables de Entorno
### ¿Qué son las variables de entorno
Cadenas que contienen información acerca del entorno para el sistema y el usuario que ha iniciado sesión en ese momento

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.
```
docker run -d --name contenedorVariable nginx:alpine -e username -e role=admin 
```

###COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/eb69efd9-922f-4d86-8722-95a75559a5c4)


### Crear un contenedor con mysql:8 , mapear todos los puertos
```
docker run -P -d --name contenedorMysql mysql:8
```

### ¿El contenedor se está ejecutando?
Ejecutamos 
```
docker ps
```
y podemos ver que no se esta ejecutando

### Identificar el problema
El problema es que el contenedor no se ejecuta automaticamente aun cuando se coloco el comando run, por un problema con logs.

### Eliminar el contenedor creado con mysql:8 
```
docker rm contenedorMysql
```

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo

```
docker run -P -d --name Mysql --env-file="C:\Users\Usuario\Downloads\password.txt" mysql:8
```

### COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/e76ae7f1-fe84-42ae-9fe2-bc77c8f82d6c)




### ¿Qué bases de datos existen en el contenedor creado?
Existen las siguientes base de datos: 

![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/99faec50-34ce-4433-89e7-ae6c51d84086)
