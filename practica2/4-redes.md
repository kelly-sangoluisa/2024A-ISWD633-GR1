# Redes
Las redes son un componente fundamental que permite la comunicación entre contenedores, así como la comunicación de los contenedores con el mundo exterior. 
![Imagen](imagenes/redes.PNG)
- Bridge: Esta es la red por defecto en Docker. Permite la comunicación entre contenedores en el mismo host. Cada contenedor conectado a la red bridge tiene una IP propia en la subred de la red bridge.
    -  Brige por default: Cuando se ejecuta un contenedor, Docker crea automáticamente una red de tipo bridge por default. Esta red se utiliza para permitir la comunicación entre contenedores en el mismo host. Cada contenedor conectado a esta red obtiene su propia dirección IP en la subred de la red bridge.
    - Bridge creada por nosotros: Un usuario también puede crear sus propias redes de tipo bridge en Docker. Esto puede ser útil para organizar y segmentar los contenedores de una aplicación de manera más controlada. Al crear una red bridge personalizada, se puede especificar un rango de direcciones IP y otras configuraciones de red específicas. Los contenedores conectados a esta red utilizarán las direcciones IP de la subred definida por el usuario.
- Host: Con esta red, los contenedores comparten la red del host en lugar de tener su propia interfaz de red. Esto puede mejorar el rendimiento de red, pero los contenedores pueden entrar en conflicto con los puertos del host si intentan utilizar los mismos puertos.
- None: Con esta red, se deshabilita la configuración de red. Los contenedores que usan esta red tienen su propia red de bucle invertido y no pueden comunicarse con otros contenedores a menos que se conecten explícitamente a una red.

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```

### Para saber a qué red está conectado un contenedor

```
docker inspect <nombre contenedor>
```
ó
```
docker network inspect <nombre red> 
```

### Vincular contenedor a una red
```
docker network connect <nombre red> <nombre contenedor>
```

### Para desvincular un contenedor de una red
```
docker network disconnect <nombre red> <nombre contenedor>
```

### Para listar las redes existentes
```
docker network ls
```

### Crear los contenedores y las redes que se presentan en el esquema. Usar para todos los contenedores la imagen de nginx:alpine

![Imagen](imagenes/esquema-ejercicio-redes.PNG)
## REDES EXISTENTES CREADAS
creamos las redes a utilizar:
```
docker network create net-curso01
docker network create net-curso02
```
Con el mismo comando se crean los contenedores y los unimos a los contenedores:
```
docker run -d --name contenedor1 --network net-curso01 nginx:alpine
```
### LISTA DE REDES EXISTENTES CREADAS
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/45640a4d-ca02-40bb-ae4c-d188c5f05ab2)

## CONTENEDORES Y A QUE RED ESTÁN VINCULADAS

### CONTENEDORES EN NET-CURSO01
```
docker inspect net-curso01
```
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/e9ad061a-ca80-4d9f-8640-591e309097b4)

###  CONTENEDORES EN NET-CURSO02
```
docker inspect net-curso02
```
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/52c26353-4962-4e86-8eb9-55ed18f1555d)

# Eliminar las redes creadas
```
docker network rm net-curso01
docker network rm net-curso02
```

