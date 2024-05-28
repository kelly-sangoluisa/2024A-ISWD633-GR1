## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio5.PNG)

### Crear la red
```
docker network create net-wp
```

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -P -d --name mysql --env-file="C:\Users\Usuario\Downloads\password.txt" --network net-wp mysql:8
```

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name wordpress -p 8080:80 --network net-wp wordpress
```

De acuerdo con el trabajo realizado, en el esquema de ejercicio el puerto a es **8080**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/7b28bcab-38ea-4008-a221-45d5c73aa497)


Desde el panel de admin: 
cambiar el tema 
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/3b6aa5ca-94b6-466f-8ecc-a37e4946cc92)


crear una nueva publicación.
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/a3bedd38-3c7f-4a56-9a2d-d47b081235e7)


Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/7bda2dc2-2484-41ed-9a9c-70bd23e7d5f6)



### Eliminar el contenedor wordpress
```
docker rm wordpress
```


### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
```
docker run -d --name wordpress -p 9300:80 wordpress
```

### ¿Qué ha sucedido, qué puede observar?
Se puede observar que el contenedor nos regresa a la configuracion inicial, donde se escoge el idioma preferido, es decir que el contenedor se reinició. 
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/32778a59-c488-4dcb-9afc-4fd898ac2c94)





