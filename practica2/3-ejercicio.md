### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name contenedorPostgre postgres:11.21-alpine3.17
```
### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name pgadmin -p 8080:80 -e PGADMIN_DEFAULT_EMAIL=admin@example.com -e PGADMIN_DEFAULT_PASSWORD=admin dpage/pgadmin4
```
# COMPLETAR

La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 80

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
![image](https://github.com/kelly-sangoluisa/2024A-ISWD633-GR1/assets/94008979/023b287c-d7dc-45f0-9e4e-6e9ea0c238e4)


# COMPLETAR CON UNA CAPTURA DEL LOGIN


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
