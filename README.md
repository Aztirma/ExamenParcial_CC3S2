# Examen Parcial CC3S2

## Pregunta 2

Se procedio a ejecutar el comando 

```
rails new todo_app
```

De este modo se creo en nuestro directorio la "aplicacion" todo_app con sus distintos files, lo que significa que se creo correctamente.

![Alt text](Imagenes/image.png)
 
Si ejecutamos el comando ls, se podra ver el contenido

![Alt text](Imagenes/image-1.png)

 Escribimos e ingresamos lo siguiente en el símbolo del sistema:

```
rails generate scaffold todo description:string
```
Lo cual nos da como salida lo siguiente:

 ![Alt text](Imagenes/image-2.png)

 **¿Qué está pasando aquí ?**

Como el comando se ejecutó correctamente, deberíamos ver una vez más una lista de resultados tanto para create <nombre de archivo> como para invoke <generator>

### Base de datos

Ya que tenemos nuestro modelo, procederemos a crear nuestra base de datos, con el siguiente comando:

```
bundle exec rake db:migrate
```
Como observamos, nos da el siguiente mensaje el cual significa que se creo exitosamente lo que deseabamos.

![Alt text](Imagenes/image-3.png)


 **¿Qué está pasando aquí ?**
 
 Al ejecutar este comando, lo que la advertencia nos indica es que se creo exitosamente el Modelo Todos, es decir ya tenemos nuestra base de datos, en este momento vacia, con la cual podemos trabajar posteriormente.

Como mencionamos, ya que tenemos nuestra base de datos, insertaremos algunos registros:

 Para ello, abriremos db/seeds.rb en nuestro directorio
  
 ![Alt text](Imagenes/image-4.png)
 
 luego pegamos las dos líneas siguientes en la parte inferior del archivo, debajo de los comentarios:

 ```
    Todo.create(description: "Hello CC3S2- Kids")
    Todo.create(description: " Do the assignments kid ")
```

 ![Alt text](Imagenes/image-5.png)

Para verificar que el modelo Todo esa definido correctamente ejecutamos la consola de rails, una vez en la consola, simplemente escribimos Todo.new. Esto debería crear una nueva instancia de la clase Movie con atributos nulos.

 ![Alt text](Imagenes/image-6.png)


Después de agregar los datos iniciales a db/seeds.rb, ejecutamos el siguiente comando para llenar la base de datos con estos datos

 ```
 rake db:seeds
 ```

 ![Alt text](Imagenes/image-7.png)

Ahora, podemos volver a la consola Rails ejecutando rails console y ejecutar Todo.all para verificar que las los datos anteriores se han agregado correctamente a la base de datos.


![Alt text](Imagenes/image-8.png)

Ahora mostraremos todas las rutas generadas por Scaffold:



FALTA!!!!!!!!
Muestra todas las rutas generadas por el comando scaffold. Recomendamos realizar solicitudes a estas
rutas para que puedas ver cómo responde tu aplicación, tanto en términos de comportamiento visual
como de qué código se llama o se modifica.

### Mas migraciones

La primera migración nos permitió crear la base de datos. Digamos que el cliente quiere que cada "tareas pendientes" tenga una fecha de vencimiento asociada. **¿Cómo hacemos que eso suceda?** 

Generamos una nueva migracion, podria realizarse de la siguiente manera:

rails generate migration AddFechaVencimientoToTareasPendientes fecha_vencimiento:date

Esto generara un nuevo archivo de migracion, similar a lo realizado en lo anterior, leugo de haber generado la migracion con el nombre asociado a el, modificamos este mismo archivo con la informacion requerida, luego lo guardamos y ejecutamos la consola rails para poder ver si nuestros cambios tuvieron efecto.

### Nuevas rutas

Para agregar un nuevo servicio a nuestra aplicacion, pero si queremos acceder a el tenemos que crear una nueva ruta.

1. Agregamos una ruta en config/routes.rb y asígnamos a una acción del controlador.  

    ```
    get ’/hello’, to: ’todos#hello’
    ```

    ![Alt text](Imagenes/aimage.png)

2. Añadimos una nueva vista correspondiente a la ruta. Para ello seguimos una serie de pasos, para poder modificar dicha vista.  
    • Creamos un archivo en el directorio app/views/todos llamado hello.html.erb.

    ![Alt text](Imagenes/aimage-1.png)

    • Por el momento el HTML permitido para esta actividad es:    
         
         <h1>¡Hola!</h1>.

    ![Alt text](Imagenes/aimage-2.png)

    • Agregamos el siguiente método `def hello` a app/controllers/todos_controller.rb.

    ![Alt text](Imagenes/aimage-3.png)

    Para comprobar si seguimos adecuantamente los pasos, ejecutamos rails server para corroborar que el mensaje aparezca al momento de acceder a nuestra ruta /hello

    ![Alt text](Imagenes/aimage-4.png)

    ### Mas ejercicios:

    1. Agregamos un nuevo atributo al modelo Todo, agregando un nuevo campo booleano llamado "done" con un valor predeterminado de falso.

     ![Alt text](Imagenes/aimage-5.png)

    2. Luego generamos la migración 

    ![Alt text](Imagenes/aimage-6.png)

    3. Esto generará un nuevo archivo

    ![Alt text](Imagenes/aimage-7.png)

    4. Actualizamos la migración

    ![Alt text](Imagenes/aimage-8.png)

    5. Modificamos las vistas 

    
 