# Proyecto Final de Ingeniería de Software: Scooby Attendance

## Trello

 [Enlace](https://trello.com/invite/b/q2yXLGNM/04a48536b6d5f02e8ac25edefeeedf0f/scooby-attendance)

<p align="center">
  <img src="https://github.com/VILLA7523/theoriginscooby/blob/main/WEB/src/public/images/logodog.png?raw=true" alt="Sublime's custom image"/>
</p>


## PRÁCTICA 9: ESTILOS DE LA PROGRAMACIÓN

### Estilo 1 - Letterbox

#### Descripción
- El problema más grande se descompone en 'cosas' que tienen sentido para el dominio del problema.
- Cada 'cosa' es una cápsula de datos que expone un solo procedimiento, a saber, la capacidad de recibir y enviar mensajes que se le envían.
- El envío de mensajes puede resultar en el envío del mensaje a otra cápsula.

#### Fragmento de código
![image](https://user-images.githubusercontent.com/79772873/185766980-a6ee77f6-3e46-4e2d-be25-21d34f6fce47.png)


### Estilo 2 - Tantrum

#### Descripción
- Cada procedimiento y función verifica la cordura de sus argumentos y se niega a continuar cuando los argumentos no son razonables.
- Todos los bloques de código verifican todos los posibles errores, posiblemente imprimen mensajes específicos del contexto cuando ocurren errores y pasan los errores a la cadena de llamadas de función

#### Fragmento de código
![image](https://user-images.githubusercontent.com/79772873/185767788-aeeb7a7d-4084-45cd-93f0-4b721a7de161.png)


### Estilo 3 - Aspects

#### Descripción
- El problema se descompone utilizando alguna forma de abstracción (procedimientos, funciones, objetos, etc.)
- Los aspectos del problema se agregan al programa principal sin editar el código fuente de las abstracciones. Estas funciones secundarias se aferran a las abstracciones principales nombrándolas, como en "Soy un aspecto de foo (¡aunque puede que foo no lo sepa!)".

_1. Manejo de objetos: Codigo refrente en [Click aqui](https://github.com/MrsblR/FinalProjectIS/blob/main/Application/src/interfaces/controllers/professor.controller.js_)_

![image](https://user-images.githubusercontent.com/79772873/186238736-3ae793ac-da44-437c-91a3-f2181df3e6eb.png)

_2. Uso de clases y funciones referente en [Click aqui](https://github.com/VILLA7523/FinalProjectIS/blob/main/Application/src/domain/repository/city.repository.js)_

![image](https://user-images.githubusercontent.com/79772873/186239671-c6f36b9f-d83c-4f1b-852f-9da425663c90.png)

## PRÁCTICA 9: CODIFICACIÓN LEGIBLE (CLEAN CODE)

### Clean Code 1 - Comentarios

#### Descripción

- Intenta siempre explicarte en código.
- No seas redundante.
- No agregue ruido obvio.
- No use comentarios de llaves de cierre.
- No comente el código. Solo elimina.
- Utilizar como explicación de la intención. 
- Utilizar como aclaración de código.
- Utilizar como advertencia de las consecuencias.

#### Framgmento de código

_1. Uso de comentarios respetando las reglas designadas [enlace](https://github.com/VILLA7523/FinalProjectIS/blob/main/Application/src/interfaces/controllers/professor.controller.js)_

![image](https://user-images.githubusercontent.com/79772873/186257096-47c895cf-62b6-4af3-869f-34050d4b440d.png)


### Clean Code 2 - Reglas de nombres

- Elija nombres descriptivos e inequívocos.
- Hacer una distinción significativa.
- Usa nombres pronunciables.
- Utilice nombres buscables.
- Reemplace los números mágicos con constantes con nombre.
- Evite las codificaciones. No agregue prefijos ni escriba información.


#### Framgmento de código

_1. Respetando las reglas de nombre , podemos observar en la sigueinte imagen que el nombre de las funciones como el de las variables no son ambiguas , y son muy descriotivas , encontradas en el dataController para más informacion [Click aqui](https://github.com/VILLA7523/FinalProjectIS/blob/main/Application/src/interfaces/controllers/data.controller.js)_

![image](https://user-images.githubusercontent.com/79772873/186258403-627cd7ac-8883-4cb9-a622-74642230f201.png)


### Clean Code 3 - Consejos de comprensibilidad

#### Despcripción 
- Se consistente. Si haces algo de cierta manera, haz todas las cosas similares de la misma manera.
- Usa variables explicativas.
- Encapsular las condiciones de contorno. Las condiciones de contorno son difíciles de seguir. Ponga el procesamiento para ellos en un solo lugar.
- Prefiere los objetos de valor dedicados al tipo primitivo.
- Evita la dependencia lógica.
- No escriba métodos que funcionen correctamente dependiendo de otra cosa en la misma clase.
- Evita los condicionales negativos.

#### Fragmento de Código
_1 - Uso de variables de entorno uso del código [Click aqui](https://github.com/VILLA7523/FinalProjectIS/blob/main/Application/src/config/dbconnections.js)

![image](https://user-images.githubusercontent.com/79772873/186261145-152e92dd-0ea5-49cf-8ca1-ea2822687627.png)

### Clean Code 4 - Reglas de funciones
#### Descripción
- Pequeña.
- Haz una cosa.
- Utilice nombres descriptivos.
- Prefiere menos argumentos.
- No tiene efectos secundarios.
- No use argumentos de bandera. Divida el método en varios métodos independientes que se pueden llamar desde el cliente sin la bandera.

#### Fragmento de Código
_1 El nombre de las funciones son descriptivas , además en todas las funciones realizadas los parametros no exceden de 7 parámetros referente en el código en [Click aqui](https://github.com/VILLA7523/FinalProjectIS/blob/main/Application/src/domain/repository/base.repository.js)_

![image](https://user-images.githubusercontent.com/79772873/186263098-2abaf811-5074-41f6-99dd-44c702e15ac0.png)


### Clean Code 5 - Objetos y estructuras de datos
#### Descripción
- Ocultar estructura interna.
- Preferir estructuras de datos.
- Evita estructuras híbridas (mitad objeto y mitad datos).
- Debería ser pequeño.
- Haz una cosa.
- Pequeño número de variables de instancia.
- La clase base no debe saber nada acerca de sus derivados.
- Es mejor tener muchas funciones que pasar algo de código a una función para seleccionar un comportamiento.
- Prefiere métodos no estáticos a métodos estáticos.

### Fragmento de código

![image](https://user-images.githubusercontent.com/79772873/186264910-72737056-ae92-422f-9a7c-00c9bf9653d3.png)

![image](https://user-images.githubusercontent.com/79772873/186265001-77c45102-206c-4007-a4cd-7377655dd876.png)

![image](https://user-images.githubusercontent.com/79772873/186265155-43317f51-da47-4f91-8768-f7ba28495e95.png)
