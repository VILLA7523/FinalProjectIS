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


