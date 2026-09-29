# PR1_AdminBBDD_Leandro_Kyliam

# 1. Creación de la base de datos

```postgresql
CREATE DATABASE biblioteca;
CREATE DATABASE
```

# 2. Creación de usuarios

## 2.a.i

```postgresql
biblioteca=# CREATE ROLE admin_biblio WITH LOGIN PASSWORD 'adminpass';
CREATE ROLE
biblioteca=# GRANT ALL PRIVILEGES ON DATABASE biblioteca TO admin_biblio;
GRANT
biblioteca=# ALTER DATABASE biblioteca OWNER TO admin_biblio;
ALTER DATABASE
```

## 2.a.ii

```postgresql
biblioteca=# CREATE ROLE usuario_biblio WITH LOGIN PASSWORD 'usuariopass';
CREATE ROLE
postgres=# GRANT CONNECT ON DATABASE biblioteca TO usuario_biblio;
GRANT
```

## 2.b (kyli, aclara que el SELECT ON ALL TABLES funca porque lo escribimos posterior a crear las tablas)

```postgresql
biblioteca=# CREATE ROLE lectores NOLOGIN;
CREATE ROLE
biblioteca=# GRANT USAGE ON SCHEMA public TO lectores;
GRANT
biblioteca=# GRANT SELECT ON ALL TABLES IN SCHEMA public TO lectores;
GRANT
```

## 2.c 

```postgresql
biblioteca=# GRANT lectores TO usuario_biblio;
GRANT ROLE
```

## 2.d. 

![Salida consulta](assets/2_d.png)

## 2.e. 

```postgresql
biblioteca=# ALTER ROLE usuario_biblio WITH PASSWORD '12345678';
ALTER ROLE
```

## 2.f. 

```postgresql
biblioteca=# REVOKE DELETE ON ALL TABLES IN SCHEMA public FROM usuario_biblio;
```

# 3. Creación de tablas

## Creacion de la tabla autores, libros y prestamos con sus respectivas claves primarias y foráneas

```postgresql
biblioteca=# CREATE TABLE autores(id_autor SERIAL PRIMARY KEY, nombre TEXT NOT NULL, nacionalidad TEXT);
CREATE TABLE

biblioteca=# CREATE TABLE libros(id_libro SERIAL PRIMARY KEY, titulo TEXT NOT NULL, año_publicacion REAL, id_autor INTEGER NOT NULL REFERENCES autores(id_autor));
CREATE TABLE

biblioteca=# CREATE TABLE prestamos(id_prestamo SERIAL PRIMARY KEY, id_libro INTEGER NOT NULL REFERENCES libros(id_libro), fecha_prestamo DATE NOT NULL, fecha_devolucion DATE, usuario_prestatario TEXT NOT NULL);
CREATE TABLE
```

### Práctica hecha por Leandro Delli Santi y Kyliam Chinea Salcedo, alu0101584003 y alu0101548050 respectivamente
