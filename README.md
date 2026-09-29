# PR1_AdminBBDD_Leandro_Kyliam

# 2. Creación de usuarios

## 2.a. 

## 2.b. 

## 2.c. 

```postgresql
biblioteca=# GRANT lectores TO usuario_biblio;
GRANT ROLE
```

## 2.d. 

## 2.e. 

```postgresql
biblioteca=# ALTER ROLE usuario_biblio WITH PASSWORD '12345678';
ALTER ROLE
```

## 2.f. 

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
