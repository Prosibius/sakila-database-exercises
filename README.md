# sakila-database-exercises
Sakila database exercises for the course “SQL Queries and Exploratory Analysis from Python 2026-1”

1. Cargar la base de datos sakila.db en DBeaver. ¿Cómo se puede saber que está conectada? Agregar la captura de pantalla.

-R// Dentro del programa DBeaver desplegamos en la parte superior del programa la seccion de Base de datos, estableceremos una nueva conexion con la base de datos, para saber si nuestra base de datos esta conectada hay que asegurarnos de poder tener acceso a ella, revisar en la parte posterior que la fuente de datos este activa y ver un signo de aprobacion en el lateral izquierdo de nuestra pestaña de navegador de base de datos, tal como se aprecia en la imagen:

<img width="1920" height="1080" alt="2026-04-05-18:38:43-screenshot" src="https://github.com/user-attachments/assets/4f2de913-d356-457f-9309-aff7944db70f" />

2.Generar el diagrama entidad relación. Agregar la captura de pantalla.

R//

<img width="1920" height="1080" alt="2026-04-05-18:47:38-screenshot" src="https://github.com/user-attachments/assets/9c3e00ed-35e6-4f1a-afd1-1a7a2cf7f5ca" />

3. Crear una consulta para saber el contenido de la tabla actor. ¿Cuáles son las columnas y cuántas filas contiene?

R// Las columnas contienen informacion de id_actor, fisrt_name, last_name y last_update.
    tiene un numero total de 200 filas el contenido de la tabla de actor.

4. ¿Qué actores tienen el apellido Berry? Retornar su primer nombre.

R//SELECT first_name FROM actor WHERE last_name = 'BERRY' ;
KARL, HENRY, CRISTOPHER

5.¿Qué actores tienen un apellido que tiene el sufijo SON?

R//SELECT first_name FROM actor WHERE last_name LIKE '%SON' ;
BETTE NICHOLSON, MATTHEW JOHANSSON, CHRISTIAN NEESON, JAYNE NEESON, RAY JOHANSSON, ANGELA HUDSON, ALBERT JOHANSSON, MERYL GIBSON, WILL WILSON.

6- a) En la tabla payments, obtener el pago más bajo, el promedio y el más bajo.
   b) Cambiar los nombres de las columnas por MINIMO, PROMEDIO Y MAXIMO.

R//SELECT MIN(amount) AS MINIMO, AVG(amount) AS PROMEDIO, MAX(amount) AS MAXIMO FROM payment;
<img width="1920" height="1080" alt="2026-04-05-19:46:24-screenshot" src="https://github.com/user-attachments/assets/50e51dd5-cec3-4701-a3cf-b199d5a13634" />

7.a) En la tabla payments, retornar customer_id y la suma total de los pagos que ha hecho cada cliente. Ordenar en orden descendente.
  b) Cambiar los nombres de las columnas por ID_CLIENTE y TOTAL.
  c) ¿Cuál es el id del cliente con un total más alto y cuál es este total?

R//SELECT customer_id AS ID_CLIENTE, SUM(amount) AS TOTAL FROM payment GROUP BY customer_id ORDER BY TOTAL DESC;
<img width="1920" height="1080" alt="2026-04-05-20:29:23-screenshot" src="https://github.com/user-attachments/assets/46565a3e-0bd2-4b7a-98a0-42997694c139" />

8. a) ¿Cuántas películas hay por categoría? Revisar en la tabla film_list.
b) Cambiar los nombres de las columnas por CATEGORIA y CONTEO.
c) Después de esta agrupación, retornar solamente las categorías que empiezan por A.

R//SELECT category AS CATEGORIA, COUNT(*) AS CONTEO FROM film_list GROUP BY category HAVING category LIKE 'A%';
<img width="1920" height="1080" alt="2026-04-05-20:32:09-screenshot" src="https://github.com/user-attachments/assets/409d0b7d-bda9-4c44-b903-e6b4c7a5cb3e" />

9.a) En la tabla rental, separar en diferentes columnas el día, año y mes de la fecha de renta de la película que aparece en inventario como 367.
b) De esta selección, retornar solamente los registros a partir de julio de 2005, ordenados de manera ascendente.

R//SELECT 
    strftime('%d', rental_date) AS DIA,
    strftime('%m', rental_date) AS MES,
    strftime('%Y', rental_date) AS ANIO,
    inventory_id
FROM rental
WHERE inventory_id = 367 
  AND rental_date >= '2005-07-01'
ORDER BY rental_date ASC;

<img width="1920" height="1080" alt="2026-04-05-20:34:41-screenshot" src="https://github.com/user-attachments/assets/1c597eac-5f42-4015-b034-bacc5183165c" />

10. Obtener el nombre de la película que aparece en inventario con inventory_id 367. (Debe usarse un JOIN con las tablas inventory y film).

R//SELECT 
    f.title AS NOMBRE_PELICULA
FROM inventory i
JOIN film f ON i.film_id = f.film_id
WHERE i.inventory_id = 367;
<img width="1920" height="1080" alt="2026-04-05-20:36:51-screenshot" src="https://github.com/user-attachments/assets/0b00cdb1-e944-4e8b-8395-149208bba52c" />






