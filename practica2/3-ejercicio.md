### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name contenedorPostgre postgres:11.21-alpine3.17
```
### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name pgadmin -p 8080:80 -e PGADMIN_DEFAULT_EMAIL=kelly@epn.com -e PGADMIN_DEFAULT_PASSWORD=password dpage/pgadmin4
```

La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5032

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
Acceder al http://localhost:8080/ 
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/a1e5e502-7816-4706-89e4-2e54af00d221)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/0653a9ee-464b-418d-be12-3a7e153f7d58)


## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
```
docker exec -it contenedorPostgres /bin/bash
40f6386ddf2a:/# psql -h 26.11.219.176 -p 5432 -u postgres -d info
```
### Realizar un select *from personas
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/cfbcea50-c2cb-46ed-8e05-d144f37859bb)
