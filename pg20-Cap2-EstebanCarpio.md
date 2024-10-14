# ¿Cómo Leer una Respuesta HTTP?

En respuesta a mi solicitud GET, el servidor envía una gran cantidad de datos que se ven así:

```
http
HTTP/1.1 200 OK
ETag: "f60e0978bc9c458989815b18ddad6d75"
Last-Modified: Thu, 10 Jan 2013 01:45:22 GMT
Content-Type: application/vnd.collection+json
{
  "collection": {
    "version": "1.0",
    "href": "http://www.youtypeitwepostit.com/api/",
    "items": [
      {
        "href": "http://www.youtypeitwepostit.com/api/messages/21818525390699506",
        "data": [
          { "name": "text", "value": "Test." },
          { "name": "date_posted", "value": "2013-04-22T05:33:58.930Z" }
        ],
        "links": []
      },
      {
        "href": "http://www.youtypeitwepostit.com/api/messages/3689331521745771",
        "data": [
          { "name": "text", "value": "Hello." },
          { "name": "date_posted", "value": "2013-04-20T12:55:59.685Z" }
        ],
        "links": []
      },
      {
        "href": "http://www.youtypeitwepostit.com/api/messages/7534227794967592",
        "data": [
          { "name": "text", "value": "Pizza?" },
          { "name": "date_posted", "value": "2013-04-18T03:22:27.485Z" }
        ],
        "links": []
      }
    ]
  },
  "template": {
    "data": [
      {"prompt": "Text of message", "name": "text", "value":""}
    ]
  }
}
```
### ¿Qué podemos aprender de esto? Bueno, cada respuesta HTTP se puede dividir en tres partes:

*Código de estado, también llamado código de respuesta.*

Es un número de tres dígitos que resume el resultado de la solicitud. El código de respuesta es lo primero que ve un cliente API y establece el contexto para el resto de la respuesta. En este caso, el código de estado es 200 (OK), lo que indica que la solicitud fue exitosa.

*El cuerpo de la entidad, también llamado simplemente el cuerpo*

Este es un documento escrito en algún formato de datos que el cliente debe comprender. En el caso de una solicitud GET, el cuerpo de la entidad es la representación de los datos solicitados. Aquí, el cuerpo de la entidad es el documento extenso al final de la respuesta, lleno de corchetes.

*Encabezados de respuesta*

Son una serie de pares clave-valor que describen el cuerpo de la entidad y la respuesta HTTP en general. Los encabezados se envían entre el código de estado y el cuerpo de la entidad. El encabezado más importante es Content-Type, que le indica al cliente HTTP cómo interpretar el cuerpo de la entidad. En este caso, el valor del encabezado Content-Type es application/vnd.collection+json, lo que indica que el cuerpo de la entidad está en formato JSON.

## **JSON**

Si tú eres un desarrollador web, probablemente reconoces este cuerpo-entidad como un documento JSON.
El cuerpo de la entidad en este caso es un documento JSON, que es un estándar para representar estructuras de datos simples en texto plano, definido en RFC 4627. JSON utiliza comillas dobles para cadenas, corchetes para listas y llaves para objetos (colecciones de pares clave-valor), con una sintaxis muy parecida a JavaScript o Python.

JSON, descrito en el RFC 4627, es un estándar para representar estructuras de datos simples en texto plano. Utiliza comillas dobles para describir cadenas:

```
"this is a string"
```

Utiliza corchetes para describir una lista:
```
[1, 2, 3]
```
Utiliza llaves para describir objetos (colecciones de pares clave-valor):
```
{"key": "value"}
```
Los datos JSON se parecen mucho al código JavaScript o Python. El estándar JSON impone restricciones al texto plano. Dice que una cadena simple como **It was the best of times.** no es aceptable, aunque un ser humano pueda entenderla. Para ser un JSON válido, una cadena debe ir entre comillas dobles: **"It was the best of times."**
