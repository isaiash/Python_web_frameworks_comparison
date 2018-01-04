# Frameworks Web basados en Python

En este documento se comparan dos de los Frameworks Web basados en Python más importantes:
  - ##### Tornado
  - ##### Django

## 1. Asincronía

La mayor ventaja de Tornado por sobre Django es que maneja sus redes de forma asíncrona (ver [explicación](https://msdn.microsoft.com/en-us/library/windows/desktop/aa365683(v=vs.85).aspx)), logrando un rendimiento muy superior y permitiéndole escalar a decenas de miles de conexiones activas. Hay que notar que no es lo mismo manejar la cantidad de peticiones por segundo que la cantidad de conexiones activas. Tornado soluciona el [C10K Problem](https://en.wikipedia.org/wiki/C10k_problem).

**Pro**: Tornado es muy útil si se necesita eficiencia cuando muchos usuarios mantegan una conexión de larga duración.
**Contra**: Hay una posibilidad de que alguna librería en específico no corra asincrónicamente, por lo que se necesitaría buscar alguna librería alternativa o programarla uno mismo.
##### 1.1. Benchmark
http://klen.github.io/py-frameworks-bench/#results
En el análisis experimental se realizaron tres mediciones:
- Serializar un objeto JSON y retornarlo como respuesta (application/json):
    **Django: 42.5 ms  ✓** | Tornado: 77.5 ms
- Cargar un respuesta de un servidor remoto y retornarlo como respuesta:
    Django: 3477 ms | **Tornado: 1037 ms  ✓**
- Cargar datos de una base de datos con ORM y renderizar a la plantilla:
    Django: 2904 ms | **Tornado: 1345 ms  ✓**
## 2. Comunidad
La comunidad de Django es [**~50 veces más grande**](https://stackshare.io/stackups/django-vs-tornado) que la de Tornado -juzgando por el contenido en StackOverflow- lo que implica que para Django hay más soluciones *ready-to-use* y una gran base de conocimiento.

## 3. WSGI
WSGI es una interface estándar para aplicaciones web en Python utilizada en Django. Define cómo manejar las consultas y generar respuestas, abstrayéndose del protocolo HTTP, sin embargo, ésto conlleva a una serie de defectos descritos [aquí](http://rz.scale-it.pl/2013/01/25/tornado___the_best_web_framework.html).
## Tamaño del proyecto
Django es un framework MVC, mientras que Tornado es un conjunto de necesidades básicas que construyen un servicio (incluye controller, templates processing engine y no incluye Object Relational Mapper[ORM] por defecto). Django tiene una estructura de proyecto bien definida, mientras que trabajando con Tornado, los desarrolladores tienen que construir la suya.
Para proyectos grandes Django es mejor opción porque facilita el mantenimiento del código.

## Testing
Django posee un *test runner* que facilita el testeo de los códigos, mientras que en Tornado es un poco más complicado porque se testea código asincrónico. Además, Django incluye por defecto ORM:
##### Object Relational Mapper
https://www.fullstackpython.com/object-relational-mappers-orms.html
ORMs proveen una abstracción mayor de la base de datos porque permite al desarrollador escribir código Python en vez de realizar declaraciones sobre la base de datos directamente (create, read, update, etc).
## Crecimiento del proyecto
Cuando un nuevo desarrrollador se involucra con el proyecto, le toma más tiempo aprender a familiarizarse con Tornado que con Dyango, por la naturaleza Asincrónica.


## Respuesta Quora
Would you begin with Tornado or Django?
>Its totally different branches of technology, full cycle web publication framework as Django, actually you can use it for many types of web projects but it can fit very tough, and it have a heavy infrastructure from-the-box with high inertness. If you want to make something like magazine site or photo-blog site its perfect. But the more you have from the box with framework the more foreign code and solutions details you have to handle or fight with.

>And tornado as fast simple asynchronous and flexible framework. Its better for web apps, especially very responsive web-apps with rich interfaces, but it requires significantly better coding skills.