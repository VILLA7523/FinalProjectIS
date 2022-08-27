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

``` javascript
const express = require("express");
const router = express.Router();
const connectionDb = require("../../config/dbconnections");

class CityModel {
  async getAll() {
    const con = connectionDb.promise();
    const data = await con.query("SELECT * FROM city");
    return data[0];
  }
  async get(id) {
    const con = connectionDb.promise();
    const data = await con.query("SELECT * FROM city WHERE CityID = ?", [id]);
    return data[0];
  }
  async findByName(city) {
    const con = connectionDb.promise();
    const data = await con.query("SELECT * FROM city WHERE City_Name = ?", [
      city,
    ]);
    return data[0];
  }
}
module.exports = CityModel;
```

### Estilo 2 - Tantrum

#### Descripción
- Cada procedimiento y función verifica la cordura de sus argumentos y se niega a continuar cuando los argumentos no son razonables.
- Todos los bloques de código verifican todos los posibles errores, posiblemente imprimen mensajes específicos del contexto cuando ocurren errores y pasan los errores a la cadena de llamadas de función

#### Fragmento de código

``` javascript
const express = require("express");
const router = express.Router();
const VerifyModel = require("../../domain/models/verify.model");
const verifyDb = new VerifyModel();
const CityModel = require("../../domain/models/city.model");
const cityDb = new CityModel();
const CourseModel = require("../../domain/models/course.model");
const SectionModel = require("../../domain/models/section.model");
const sectionDb = new SectionModel();
const TypeModel = require("../../domain/models/type.model");
const typeDb = new TypeModel();
const PersonModel = require("../../domain/models/person.model");
const personDb = new PersonModel();
const courseDb = new CourseModel();

const CourseService = require("../../aplication/services/course.service");
const CourseRepository = require("../../domain/repository/course.repository");

const CityService = require("../../aplication/services/city.service");
const CityRepository = require("../../domain/repository/city.repository");

const TypeService = require("../../aplication/services/type.service");
const TypeRepository = require("../../domain/repository/type.repository");

const SectionService = require("../../aplication/services/type.service");
const SectionRepository = require("../../domain/repository/type.repository");


class DataController {
  constructor() { }
  async getAllPerson() {
    var personRepository = new TypeRepository(personDb);
    var personService = new TypeService(personRepository);
    const result = personService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllVerify() {
    var verifyRepository = new VerifyRepository(personDb);
    var verifyService = new VerifyService(verifyRepository);
    const result = verifyService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCities() {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const data = await cityService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }


  async getAllType() {
    var typeRepository = new TypeRepository(typeDb);
    var typeService = new TypeService(typeRepository);
    const data = await typeService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllSection() {
    var sectionRepository = new SectionRepository(sectionDb);
    var sectionService = new SectionService(sectionRepository);
    const result = sectionService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityByName(name) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.findByName(name);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityById(id) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.get(id);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCourses() {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseById(id) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.get(id)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseByName(name) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.findByName(name)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }
}
module.exports = DataController;
```

### Estilo 3 - Aspects

#### Descripción
- El problema se descompone utilizando alguna forma de abstracción (procedimientos, funciones, objetos, etc.)
- Los aspectos del problema se agregan al programa principal sin editar el código fuente de las abstracciones. Estas funciones secundarias se aferran a las abstracciones principales nombrándolas, como en "Soy un aspecto de foo (¡aunque puede que foo no lo sepa!)".

``` javascript
class DataController {
  constructor() { }

  async getAllPerson() {
    var personRepository = new TypeRepository(personDb);
    var personService = new TypeService(personRepository);
    const result = personService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllVerify() {
    var verifyRepository = new VerifyRepository(personDb);
    var verifyService = new VerifyService(verifyRepository);
    const result = verifyService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCities() {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const data = await cityService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }


  async getAllType() {
    var typeRepository = new TypeRepository(typeDb);
    var typeService = new TypeService(typeRepository);
    const data = await typeService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllSection() {
    var sectionRepository = new SectionRepository(sectionDb);
    var sectionService = new SectionService(sectionRepository);
    const result = sectionService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityByName(name) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.findByName(name);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityById(id) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.get(id);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCourses() {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseById(id) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.get(id)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseByName(name) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.findByName(name)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }
}

module.exports = DataController;
```

Uso de clases y funciones referente

``` javascript
const BaseRepository = require("./base.repository");

class CityRepository extends BaseRepository {
  constructor(CityDb) {
    super(CityDb);
  }

  async getAllWithoutPagination() {
    return this.model.find();
  }
}

module.exports = CityRepository;
```

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

Uso de comentarios respetando las reglas designadas 

``` javascript
const express = require("express");
const router = express.Router();
const PersonModel = require("../../domain/models/person.model");
const personDb = new PersonModel();
const LoginModel = require("../../domain/models/login.model");
const loginDb = new LoginModel();
const ProfessorModel = require("../../domain/models/professor.model");
const professorDb = new ProfessorModel();
const InscriptionModel = require("../../domain/models/inscription.model");
const inscriptionDb = new InscriptionModel();
const CourseModel = require("../../domain/models/course.model")
const courseDb = new CourseModel();
const CourseStudentsModel = require("../../domain/models/course_student.model");
const courseStudentsDb = new CourseStudentsModel();
const SheduleModel = require("../../domain/models/shedule.model");
const sheduleDb = new SheduleModel();

const ProfessorService = require("../../aplication/services/professor.service");
const ProfessorRepository = require("../../domain/repository/professor.repository");

const InscriptionService = require("../../aplication/services/inscription.service");
const InscriptionRepository = require("../../domain/repository/inscription.repository");

const SheduleService = require("../../aplication/services/shedule.service");
const SheduleRepository = require("../../domain/repository/shedule.repository");

const CourseService = require("../../aplication/services/course.service");
const CourseRepository = require("../../domain/repository/course.repository");

const PersonService = require("../../aplication/services/person.service");
const PersonRepository = require("../../domain/repository/person.repository");

const LoginService = require("../../aplication/services/login.service");
const LoginRepository = require("../../domain/repository/login.repository");

const CourseStudentsService = require("../../aplication/services/courseStudents.service");
const CourseStudentsRepository = require("../../domain/repository/courseStudents.repository");

class ProfessorController {
  async getAll() {
    var professorRepository = new ProfessorRepository(professorDb);
    var professorService = new ProfessorService(professorRepository);
    const result = profesorService.getAll()
    const data = await result.catch((err) => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findBydCode(code) {
    var professorRepository = new ProfessorRepository(professorDb);
    var professorService = new ProfessorService(professorRepository);
    const result = professorService.findBydCode(code)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async studentInscription(StudentID, CourseID) {
    var inscriptionRepository = new InscriptionRepository(inscriptionDb);
    var inscriptionService = new InscriptionService(inscriptionRepository);
    const result = inscriptionService.create({ StudentID, CourseID });
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async NuevoHorario(Day, Start, Finish, CourseID) {
    var sheduleRepository = new SheduleRepository(sheduleDb);
    var sheduleService = new SheduleService(sheduleRepository);
    const result = sheduleService.create({ Day, Start, Finish, CourseID });
    const data = await result.catch((err) => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async GetHorario(CourseID) {
    var sheduleRepository = new SheduleRepository(sheduleDb);
    var sheduleService = new SheduleService(sheduleRepository);
    const result = sheduleService.get(CourseID);
    const data = await result.catch((err) => {
      console.log("controller Error Get Horario ", err);
      return null;
    });
    return data;
  }

  async NuevoCourse(Course_Name, SectionID, TypeID, ProfessorID, NumEst, Semestre) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.create({ Course_Name, SectionID, TypeID, ProfessorID, NumEst, Semestre });
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });

    return data;
  }

  async register(
    First_Name,
    Last_Name,
    Email,
    DNI,
    Mobile_Phone,
    CityID,
    Department,
    Password,
    idDNI) {
    var personRepository = new PersonRepository(personDb);
    var personService = new PersonService(personRepository);
    var professorRepository = new ProfessorRepository(professorDb);
    var professorService = new ProfessorService(professorRepository);
    var loginRepository = new LoginRepository(loginDb);
    var loginService = new LoginService(loginRepository);

    const result = personService.create(

      First_Name,
      Last_Name,
      Email,
      DNI,
      null,
      Mobile_Phone,
      CityID

    );

    const data = await result.catch((err) => {
      console.log("controller Error", err);
      return null;
    });

    let dataId;
    const resultProfessor = professorService.create({ Department, dataId, idDNI });
    const dataProfessor = await resultProfessor.catch(err => {
      console.log("controller Error Professor", err);
      return null;
    })

    let val = null;
    let rol = 1;
    const resultLogin = loginService.create({ Email, Password, val, idDNI, rol });
    const dataLogin = await result.catch((err) => {
      console.log("controller Error", err);
      return null;
    });
    console.log("dataLogin", dataLogin);
    return dataLogin;
  }

  async login(email, password) {
    var loginRepository = new LoginRepository(loginDb);
    var loginService = new LoginService(loginRepository);
    const resulLogin = loginService.authenticate(email, password);
    const dataLogin = await resulLogin.catch((err) => {
      console.log("controller Error", err);
      return null;
    });
    return dataLogin;
  }

  async getAllCourses(id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const resultCourse = await courseService.findByIdProfessor(id)
      .catch((err) => {
        console.log("Controller Error", err);
        return null;
      });
    return resultCourse;
  }


  async getProfessorToCourse(token) {
    var professorRepository = new ProfessorRepository(professorDb);
    var professorService = new ProfessorService(professorRepository);

    const resultProfessor = professorService.findByDNI(token);
    const dataProfessor = await resultProfessor.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return dataProfessor;
  }

  async getStudentsOfCourses(token) {
    var courseStudentsRepository = new CourseStudentsRepository(courseStudentsDb);
    var courseStudentsService = new CourseStudentsService(courseStudentsRepository);

    const resultStudentsCourse = courseStudentsService.studentsForCourse(token);
    const dataStudentsCourse = await resultStudentsCourse.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return dataStudentsCourse;
  }

  async deleteCourse(id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const result = courseService.delete(id);
    const data = await result.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return data;
  }

  async getCourse(id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const result = courseService.get(id)
    const data = await result.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return data;
  }

  async updateCourse(name, section, type, semestre, id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const result = courseService.update({ name, section, type, semestre, id })
    const data = await result.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return data;
  }

}

module.exports = ProfessorController;
```

### Clean Code 2 - Reglas de nombres

- Elija nombres descriptivos e inequívocos.
- Hacer una distinción significativa.
- Usa nombres pronunciables.
- Utilice nombres buscables.
- Reemplace los números mágicos con constantes con nombre.
- Evite las codificaciones. No agregue prefijos ni escriba información.


#### Framgmento de código

Respetando las reglas de nombre , podemos observar en la sigueinte imagen que el nombre de las funciones como el de las variables no son ambiguas , y son muy descriotivas , encontradas en el dataController para más informacion.

``` javascript

class DataController {
  constructor() { }

  async getAllPerson() {
    var personRepository = new TypeRepository(personDb);
    var personService = new TypeService(personRepository);
    const result = personService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllVerify() {
    var verifyRepository = new VerifyRepository(personDb);
    var verifyService = new VerifyService(verifyRepository);
    const result = verifyService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCities() {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const data = await cityService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }


  async getAllType() {
    var typeRepository = new TypeRepository(typeDb);
    var typeService = new TypeService(typeRepository);
    const data = await typeService.getAll().catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllSection() {
    var sectionRepository = new SectionRepository(sectionDb);
    var sectionService = new SectionService(sectionRepository);
    const result = sectionService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityByName(name) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.findByName(name);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCityById(id) {
    var cityRepository = new CityRepository(cityDb);
    var cityService = new CityService(cityRepository);
    const result = cityService.get(id);
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async getAllCourses() {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.getAll();
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseById(id) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.get(id)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }

  async findCourseByName(name) {
    var courseRepository = new CourseRepository(CoursesDb);
    var courseService = new CourseService(courseRepository);
    const result = courseService.findByName(name)
    const data = await result.catch(err => {
      console.log("controller Error", err);
      return null;
    });
    return data;
  }
}

module.exports = DataController;
```

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
Uso de variables de entorno uso del código

``` javascript
require("dotenv").config();
const mysql = require("mysql2");
// create the pool
const pool = mysql.createPool({
  host: process.env.HOST,
  user: process.env.USER,
  database: process.env.DATABASE,
  password: process.env.PASSWORD,
});

module.exports = pool;
```

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

``` javascript
class BaseRepository {
  constructor(model) {
    this.model = model;
  }
  async get(id) {
    return await this.model.get(id);
  }
  async getAll() {
    return await this.model.getAll();
  }
  async getByName(name) {
    return await this.model.getByName(name);
  }
  async create(entity) {
    return await this.model.create(entity);
  }
  async update(entity) {
    return await this.model.update(entity);
  }
  async delete(id) {
    return await this.model.delete(id);
  }
}
module.exports = BaseRepository;
```

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

``` javascript
const BaseService = require("./base.service");

class CourseService extends BaseService {
  constructor(CourseRepository) {
    super(CourseRepository);
    this._CourseRepository = CourseRepository;
  }

  async findByIdProfessor(id) {
    if (!id) {
      const error = new Error();
      error.status = 400;
      error.message = "Email or password missing";
      throw error;
    }

    const entity = await this.repository.findByIdProfessor(id);

    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Failed authentication";
      throw error;
    }
    return entity;
  }
  //si es true aumenta , si es fals disminuye

  async updateCantEstIn(id) {
    if (!id) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro id debe ser enviado";
      throw error;
    }

    const entity = await this.repository.updateCantEstIn(id);

    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async updateCantEstDe(id) {
    if (!id) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro id debe ser enviado";
      throw error;
    }

    const entity = await this.repository.updateCantEstDe(id);

    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }
}

module.exports = CourseService;
```

``` javascript
const BaseRepository = require("./base.repository");

class CourseRepository extends BaseRepository {
  constructor(CourseDb) {
    super(CourseDb);
  }
  async findByIdProfessor(id) {
    return await this.model.findByIdProfessor(id);
  }
}

module.exports = CourseRepository
```

``` javascript
  async getCourse(id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const result = courseService.get(id)
    const data = await result.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return data;
  }

  async updateCourse(name, section, type, semestre, id) {
    var courseRepository = new CourseRepository(courseDb);
    var courseService = new CourseService(courseRepository);

    const result = courseService.update({ name, section, type, semestre, id })
    const data = await result.catch((err) => {
      console.log("Controller error", err);
      return null;
    });
    return data;
  }
```

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
En nuestra implementación se cumple este principio , un ejemplo de ello son en lo servicios , repository , etc . todas las funciones que se usaran en el proyecto son propias de cada modelo esto quiere decir , que en cada clase se impletan funciones que no comparte con las demás , y las que si son genéricas se establecen en una clase base , tomando en cuenta las principales funciones crud asi como los filtros.

Implementacion de baseService , se puede observar las principales funciones crud.

``` javascript
class BaseService {
  constructor(Repository) {
    this.repository = Repository;
  }
  async get(id) {
    if (!id) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro id debe ser enviado";
      throw error;
    }

    const entity = await this.repository.get(id);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async getByName(name) {
    if (!name) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro name debe ser enviado";
      throw error;
    }

    const entity = await this.repository.getByName(name);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async getAll() {
    const entity = await this.repository.getAll();
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async create(data) {
    const entity = await this.repository.create(data);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async update(data) {
    const entity = await this.repository.update(data);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async delete(id) {
    const entity = await this.repository.delete(id);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }
}
```

De esta clase base extienden otras como: 

CouserStudetsService , se observa que solo esta implementado funciones propias de esta.

```javascript
const BaseService = require("./base.service");

class CourseStudentsService extends BaseService {
  constructor(CourseStudentsRepository) {
    super(CourseStudentsRepository);
    this._CourseStudentsRepository = CourseStudentsRepository;
  }
  async studentsForCourse(token) {
    if (!token) {
      const error = new Error();
      error.status = 400;
      error.message = "token parameter is missing";
      throw error;
    }

    const entity = await this.repository.studentsForCourse(token);

    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Student not found";
      throw error;
    }
    return entity;
  }
}

module.exports = CourseStudentsService;
```

LoginService , se observa que solo esta implementado funciones propias de esta.

``` javascript
const BaseService = require("./base.service");

class LoginService extends BaseService {
  constructor(LoginRepository) {
    super(LoginRepository);
    this._LoginRepository = LoginRepository;
  }

  async authenticate(email, password) {
    if (!email || !password) {
      const error = new Error();
      error.status = 400;
      error.message = "Email or password missing";
      throw error;
    }

    const entity = await this.repository.authenticate(email, password);

    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Failed authentication";
      throw error;
    }
    return entity;
  }
}

module.exports = LoginService;
```

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

``` javascript
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


### 3 - Interface segregation principle(ISP)

#### Descripción
- No se debe obligar a los clientes a depender de métodos que no utilizan. Cuando se requiere que una Clase realice acciones que no son útiles, es un desperdicio y puede producir errores inesperados si la Clase no tiene la capacidad de realizar esas acciones.
- Una clase debe realizar solo las acciones necesarias para cumplir su función. Cualquier otra acción debe eliminarse por completo o moverse a otro lugar si otra Clase podría usarla en el futuro.

#### Fragmento de Código
Los metodos principales usados para el CRUD estan definidos tanto en base.repository.js como en base.service.js respectivamente , aqui cumplimos con lo mecionado anteriormente , de que no se debe colocar funcionalidades que no usemos , es por ello que estas clases definen solo acciones que otra clases podría cumplir en un futuro , y en general las que toda clase debe usar.  

Implementación de base repository , asi mismo esta clase funciona como interfaz entre los mmodels y los services

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

Implementación de Base Service , asi mismo esta clase funciona como interfaz entre los controllers y los repository

``` javascript
class BaseService {
  constructor(Repository) {
    this.repository = Repository;
  }
  async get(id) {
    if (!id) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro id debe ser enviado";
      throw error;
    }

    const entity = await this.repository.get(id);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async getByName(name) {
    if (!name) {
      const error = new Error();
      error.status = 400;
      error.message = "Parametro name debe ser enviado";
      throw error;
    }

    const entity = await this.repository.getByName(name);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async getAll() {
    const entity = await this.repository.getAll();
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async create(data) {
    const entity = await this.repository.create(data);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async update(data) {
    const entity = await this.repository.update(data);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }

  async delete(id) {
    const entity = await this.repository.delete(id);
    if (!entity) {
      const error = new Error();
      error.status = 400;
      error.message = "Entidad no encontrada";
      throw error;
    }
    return entity;
  }
}
```










