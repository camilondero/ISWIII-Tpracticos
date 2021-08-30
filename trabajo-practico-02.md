4- Desarrollo:
1- Instalar Docker Community Edition

![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img1.png)

   - Ejecutar el siguiente comando para comprobar versiones de cliente y demonio.
   
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img2.png)

3- Obtener la imagen BusyBox

   - Ejecutar el siguiente comando, para bajar una imagen de DockerHub

![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img3.png)

   - Verificar qué versión y tamaño tiene la imagen bajada, obtener una lista de imágenes locales:

![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img4.png)

    
4- Ejecutando contenedores

   - Ejecutar un contenedor utilizando el comando run de docker:

         docker run busybox

   - Explicar porque no se obtuvo ningún resultado

No se obtuvo ningun resultado pq este comando lo unico que hace es buscar el contenedor y ejecutarlo, no le estamos diciendo que realice nada mas que eso.

   - Especificamos algún comando a correr dentro del contendor, ejecutar por ejemplo:

         docker run busybox echo "Hola Mundo"
         
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img5.png)

   - Ver los contendores ejecutados utilizando el comando ps:

         docker ps

   - Vemos que no existe nada en ejecución, correr entonces:

         docker ps -a
         
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img6.png)

   - Mostrar el resultado y explicar que se obtuvo como salida del comando anterior.
Se obtuvo como resultado el historial de comandos de los contenedores ordenados por tiempo. Tambien nos brinda informacion sobre los contenedores como el ID y nombre.

5- Ejecutando en modo interactivo

   - Ejecutar el siguiente comando

         docker run -it busybox sh
         
   - Para cada uno de los siguientes comandos dentro de contenedor, mostrar los resultados:

         ps
         uptime
         free
         ls -l /

   - Salimos del contendor con:

         exit
   
  ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img7.png)


6- Borrando contendores terminados

   - Obtener la lista de contendores

         docker ps -a

   - Para borrar podemos utilizar el id o el nombre (autogenerado si no se especifica) de contendor que se desee, por ejemplo:

         docker rm elated_lalande

   - Para borrar todos los contendores que no estén corriendo, ejecutar cualquiera de los siguientes comandos:

         docker rm $(docker ps -a -q -f status=exited)

         docker container prune

7- Montando volúmenes

Hasta este punto los contenedores ejecutados no tenían contacto con el exterior, ellos corrían en su propio entorno hasta que terminaran su ejecución. Ahora veremos cómo montar un volumen dentro del contenedor para visualizar por ejemplo archivos del sistema huésped:

   - Ejecutar el siguiente comando, cambiar myusuario por el usuario que corresponda. En linux/Mac puede utilizarse /home/miusuario):

         docker run -it -v C:\Users\misuario\Desktop:/var/escritorio busybox /bin/sh

   - Dentro del contenedor correr

         ls -l /var/escritorio
         touch /var/escritorio/hola.txt

   - Verificar que el Archivo se ha creado en el escritorio o en el directorio home según corresponda.

8- Publicando puertos

En el caso de aplicaciones web o base de datos donde se interactúa con estas aplicaciones a través de un puerto al cual hay que acceder, estos puertos están visibles solo dentro del contenedor. Si queremos acceder desde el exterior deberemos exponerlos.

   - Ejecutar la siguiente imagen, en este caso utilizamos la bandera -d (detach) para que nos devuelva el control de la consola:

         docker run -d daviey/nyan-cat-web
         
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img8.png)

    - Si ejecutamos un comando ps:

      PS D:\> docker ps
      CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS               NAMES
      87d1c5f44809        daviey/nyan-cat-web   "nginx -g 'daemon of…"   2 minutes ago       Up 2 minutes        80/tcp, 443/tcp     compassionate_raman

   - Vemos que el contendor expone 2 puertos el 80 y el 443, pero si intentamos en un navegador acceder a http://localhost no sucede nada.

   - Procedemos entonces a parar y remover este contenedor:
   
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img9.png)


   - Vamos a volver a correrlo otra vez, pero publicando uno de los puertos solamente, el este caso el 80

         docker run -d -p 80:80 daviey/nyan-cat-web
         
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img10.png)

   - Accedamos nuevamente a http://localhost y expliquemos que sucede.
   - 
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/img11.png)


9- Utilizando una base de datos

   - Levantar una base de datos PostgreSQL

      mkdir $HOME/.postgres

      docker run --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -v $HOME/.postgres:/var/lib/postgresql/data -p 5432:5432 -d postgres:9.4

   - Ejecutar sentencias utilizando esta instancia

         docker exec -it my-postgres /bin/bash

         psql -h localhost -U postgres

         #Estos comandos se corren una vez conectados a la base

         \l
         create database test;
         \connect test
         create table tabla_a (mensaje varchar(50));
         insert into tabla_a (mensaje) values('Hola mundo!');
         select * from tabla_a;

         \q

         exit
![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/im12.png)

   - Conectarse a la base utilizando alguna IDE (Dbeaver - https://dbeaver.io/, eclipse, IntelliJ, etc...). Interactuar con los objectos objectos creados.

   - Explicar que se logro con el comando docker run y docker exec ejecutados en este ejercicio.

    
