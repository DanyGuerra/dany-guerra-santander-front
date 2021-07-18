# 6. CSS Frameworks (Reutilizando componentes visuales)

**Framework CSS** es código que pueda ser reutilizable en más de un proyecto además de una colección de componentes interactivos que suelen estar presentes en una amplia variedad de páginas.

Frameworks mas utilizados

- Bootstrap
- Materialize
- Foundation
- Bulma
- Semantic UI
- Tailwind CSS

En este proyecto se estara utilizando Bootstrap por las siguientes razones.

- Es un framework muy usado al día de hoy.
- La base de componentes con las que cuenta hace que migrar a otro Framework sea un proceso más sencillo.
- Buena demanda en el mercado.

### Agregando Bootstrap al proyecto

#### Agregando estilos de Bootstrap
Para agregar Bootstrap al proyecto se agrega la siguiente etiqueta en `<head> </head>`

`Nota: los estilos de bootstrap se agregan antes de la hoja de estilos que ya tenemos en nuestro proyecto`

` <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">`

Atributos:

- `rel` :Este atributo indica la relación del documento enlazado con el actual. El atributo debe ser una lista de tipos de enlaces separados por espacio. El uso más común para este atributo es especificar el enlace a una hoja de estilos externa: el atributo rel se establece con valor `stylesheet`

- `href` : Este atributo especifica la URL del recurso enlazado. La URL debe ser absoluta o relativa.

- `integrity` : Contiene metadatos en línea, el valor criptográfico codificado a base 64 de un recurso (archivo) que se le está indicando al navegador que obtenga, el cual puede ser utilizado por el agente usuario para verificar si el recurso obtenido ha sido entregado libre de manipulaciones inesperadas.

- `crossorigin` :Este atributo enumerado indica si se debe usar CORS cuando se solicite una imagen relacionada. Las imágenes con CORS habilitado pueden ser reutilizadas en el elemento `<canvas>` sin que estén corruptas.Los valores permitidos son:

#### Interactividad con JavaScript
Para agregar los JavaScript de Bootstrap se agrega con la etiqueta `<script>` antes de que termine la etiqueta `<body>` lo siguiente:


```
    <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
      integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
      integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"
      integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
  </body>
</html>
```



[Documentacion de Bootstrap](https://getbootstrap.com/docs/5.0/getting-started/introduction/)

### [Anterior](../sesion5)
### [Siguiente](../sesion7)