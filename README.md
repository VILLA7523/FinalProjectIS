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

### Clean Code - 7 Capitalize SQL Special Words
#### Descripción
- La interacción con la base de datos es una parte importante de la mayoría de las aplicaciones web. Si está escribiendo consultas SQL sin procesar, es una buena idea mantenerlas legibles también.
- Aunque las palabras especiales de SQL y los nombres de funciones no distinguen entre mayúsculas y minúsculas, es una práctica común usar mayúsculas para distinguirlos de los nombres de tablas y columnas.

Fragmento de Código



## PRACTICA 11 - PRINCIPIOS SOLID
### Principio de inversión de dependencia (DIP)

#### Descripción
Este principio establece dos cosas esenciales:

- Los módulos de alto nivel no deben depender de los módulos de bajo nivel. Ambos deberían depender de abstracciones.
- Las abstracciones no deben depender de los detalles. Los detalles deben depender de las abstracciones.
Esto puede ser difícil de entender al principio,
pero si has trabajado con marcos PHP (como Symfony), has visto una implementación de este principio en forma de inyección de dependencia (DI). Si bien no son conceptos idénticos, DIP evita que los módulos de alto nivel conozcan los detalles de sus módulos de bajo nivel y los configuren. Puede lograr esto a través de DI.
Un gran beneficio de esto es que reduce el acoplamiento entre módulos. El acoplamiento es un patrón de desarrollo muy malo porque hace que su código sea difícil de refactorizar.

#### Fragmento de código

Clase base de implementación de crud en la siguiente imagen: 

![image](https://user-images.githubusercontent.com/79772873/187010563-0dad0d99-4d68-4105-b7e1-d092795005ec.png)

Clases que usan al implementacion de base Service.

![image](https://user-images.githubusercontent.com/79772873/187010583-371bc6d1-82af-40d2-91ee-2e05ef3902d2.png)

### 2 - Principio abierto/cerrado (OCP)
#### Descripción
El Principio Abierto/Cerrado, también conocido como Open/Closed Principle o por sus siglas OCP, es el segundo de los 5 principios SOLID de la programación orientada a objetos.

Los módulos que cumplen con el principio abierto-cerrado tienen dos características principales. Estos son

 - Abiertos para la extensión: Esto significa que el comportamiento del módulo puede ser extendido. Cuando los requerimientos de la aplicación cambian, debemos ser capaces de extender el módulo con estos nuevos comportamientos que satisfagan esos cambios. En otras palabras, debemos ser capaces de cambiar lo que el módulo hace.
 - Cerrado para la modificación: Esto significa que extender el comportamiento de un módulo no debería tener como resultado cambiar el código fuente, es decir, el código original debe permanecer sin cambios.

#### Fragmento de Código
La siguiente fragmento de código muestra la implementación de la clase BaseRepository , en la cual se encuentran las funciones crud , cumple con las caracteristica de este principio ya que se puede observar que en la clase baseRepository estan implementadas las funciones crud , que todos nuestros modelos usaran , de esta clase ectendimos más clases en las cuales hay funciones propias de cada repositorio:

En el siguiente fragmento de código podemos observar que los parámetros de las funciones , reciben un objeto , esto con el objetivo de hacer que las funciones sean génericas y cualquier repository que estiendan a ella sean independientes a sus parámetros 

``` Javascript
class BaseRepository {
  constructor(model) {
    this.model = model;
  }
  async get(id) {
    return this.model.get(id);
  }
  async getAll() {
    return this.model.getAll();
  }
  async getByName(name) {
    return this.model.getByName(name);
  }
  async create(entity) {
    return this.model.create(entity);
  }
  async update(entity) {
    return this.model.update(entity);
  }
  async delete(id) {
    return this.model.delete(id);
  }
}
```

En las siguientes imagenes son nuestras implementaciones .repository que extienden del baseRepository:

implementación de loginRepository , como se observa authenticate es propio de login , pues ninguna de las otras clases lo comparte , es por eso que est funcionalidad se desarrolla dentro de la clase porpia de esta 

``` javascript
const BaseRepository = require("./base.repository");

class LoginRepository extends BaseRepository {
  constructor(LoginDb) {
    super(LoginDb);
  }

  async authenticate(email , password) {
    return await this.model.authenticate(email , password);
  }
}

module.exports = LoginRepository
```

Implementación de courseStudentsRepository que extiende de BaseRepository 

```javascript
const BaseRepository = require("./base.repository");

class CourseStudentsRepository extends BaseRepository {
  constructor(CourseStudentsDb) {
    super(CourseStudentsDb);
  }
  async studentsForCourse(token) {
    return await this.model.studentsForCourse(token);
  }
}

module.exports = CourseStudentsRepository
```

Implementación de Course que extiende de baseRepository

const BaseRepository = require("./base.repository");

``` javascript
class CourseRepository extends BaseRepository {
  constructor(CourseDb) {
    super(CourseDb);
  }

  async getAllWithoutPagination() {
    return await this.model.find();
  }

  async findByIdProfessor(id) {
    return await this.model.findByIdProfessor(id);
  }
}

module.exports = CourseRepository
```


### Interface segregation principle(ISP)
#### Descripción
No se debe obligar a los clientes a depender de métodos que no utilizan. Cuando se requiere que una Clase realice acciones que no son útiles, es un desperdicio y puede producir errores inesperados si la Clase no tiene la capacidad de realizar esas acciones.
Una clase debe realizar solo las acciones necesarias para cumplir su función. Cualquier otra acción debe eliminarse por completo o moverse a otro lugar si otra Clase podría usarla en el futuro.

#### Fragmento de Código
Los metodos principales usados para el CRUD estan definidos tanto en base.repository.js como en base.service.js respectivamente.

![image](https://user-images.githubusercontent.com/79772873/186266190-ee8f3091-9f82-443a-a969-9f538cdccf8f.png)

Se usa en las siguientes clases: 

![image](https://user-images.githubusercontent.com/79772873/187010495-54a84de6-9407-4c47-8ceb-a3e833a70dbc.png)


![image](https://user-images.githubusercontent.com/79772873/187010519-2529dada-354a-4d32-81e2-41f1112099c0.png)








