
4- Desarrollo:

1- Instanciación del sistema

- Clonar el repositorio https://github.com/microservices-demo/microservices-demo
    
      mkdir -p socks-demo
      cd socks-demo
      git clone https://github.com/microservices-demo/microservices-demo.git
      
 ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/tp4-1.png)  
 
- Ejecutar lo siguiente

      cd microservices-demo
      docker-compose -f deploy/docker-compose/docker-compose.yml up -d
      
- Una vez terminado el comando docker-compose acceder a http://localhost

 ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/tp4-2.png) 
 
- Generar un usuario

 ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/tp4-3.png)     

- Realizar búsquedas por tipo de media, color, etc.

 ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/tp4-4.png)

- Hacer una compra - poner datos falsos de tarjeta de crédito ;)

 ![imagen](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/tp4-5.png)     

2- Investigación de los componentes

1. Describa los contenedores creados, indicando cuales son los puntos de ingreso del sistema

Realizamos un cat al archivo docker-compose.yml y buscamos los contenedores creados:

 - Catalogue: Catalogo de medias
 - Catalogue_db: Base de datos mysql donde se almacenan los produtos del catalogo.
 - Queue-master: Es el encargado de administrar los pedidos de la pagina web.
 - Edge-router: punto de acceso al sistema.
 - Front-end: Diseño de la pagina
 - Payment: Maneja los pagos de los productos
 - Carts: Es el encargado de administrar los datos de los carritos de compra
 - Carts_db:Base de datos con la informacion almacenada en los carritos de compra.
 - Orders: Administra las ordenes de compra.
 - Orders_db: Base de datos que almacena la informacion sobre las ordenes de compra.
 - User: Administra los usuarios de la web. Punto de entrada al sistema.
 - User_db: Base de datos que almacena la informacion de los usuarios.


3. Clonar algunos de los repositorios con el código de las aplicaciones
       
        cd socks-demo
        git clone https://github.com/microservices-demo/front-end.git
        git clone https://github.com/microservices-demo/user.git
        git clone https://github.com/microservices-demo/edge-router.git

3. ¿Por qué cree usted que se está utilizando repositorios separados para el código y/o la configuración del sistema? Explique puntos a favor y en contra.

4. ¿Cuál contenedor hace las veces de API Gateway?

5.Cuando ejecuto este comando:

        curl http://localhost/customers
    
6. ¿Cuál de todos los servicios está procesando la operación?
    El servicio User es el que procesa esta operacion.
    
8. ¿Y para los siguientes casos?
    
       curl http://localhost/catalogue
       curl http://localhost/tags
       
    Estas operaciones son procesadas por el servicio Catalogue.
    
8. ¿Como perisisten los datos los servicios?
    Los datos de estos servicios son almacenados en sus respectivas base de datos, cuentan con base de datos MongoDB y MYSQL
10. ¿Cuál es el componente encargado del procesamiento de la cola de mensajes? 
    RabbitMQ
12. ¿Qué tipo de interfaz utilizan estos microservicios para comunicarse?
    Utilizan la interfaz de RabbitMQ.
