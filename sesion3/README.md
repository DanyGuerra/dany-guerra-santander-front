# 3. HTML- flexbox (Dividiendo secciones en columnas)

[Documentacion de MDN](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
## Que es flexbox?

El Módulo de Caja Flexible, comúnmente llamado flexbox, fue diseñado como un modelo unidimensional de layout, y como un método que pueda ayudar a distribuir el espacio entre los ítems de una interfaz y mejorar las capacidades de alineación.

## Los dos ejes de flexbox

Cuando trabajamos con flexbox necesitamos pensar en términos de dos ejes — el eje principal y el eje cruzado. El eje principal está definido por la propiedad flex-direction, y el eje cruzado es perpendicular a este. Todo lo que hacemos con flexbox está referido a estos dos ejes, por lo que vale la pena entender cómo trabajan desde el principio.

### El eje principal

El eje principal está definido por flex-direction, que posee cuatro posibles valores:

- `row`
- `row-reverse`
- `column`
- `column-reverse`

Si elegimos `row` o `row-reverse` el eje principla estara de la siguiente manera:

![Eje principal de flexbox](./../images/Basics1.png)

Al elegir `column` o `column-reverse` el eje principal correrá desde el borde superior de la página hasta el final — según la dirección del bloque.


![Eje principal de flexbox](./../images/Basics2.png)


### El eje cruzado

El eje cruzado va perpendicular al eje principal. Por lo tanto el eje secundario depende de como este definido el principal.

Si el eje principal esta definido con `row` o `row-reverse` el eje cruzado irá por las columnas.

![Eje principal de flexbox](./../images/Basics3.png)

Si el eje principal es column o column-reverse entonces el eje cruzado corre a lo largo de las filas.

![Eje principal de flexbox](./../images/Basics4.png)

## Juegos para aprender Flexbox
Se dejan los enlaces de algunos juegos para aprender Flexbox muy divertidos y ademas entenderas y aplicaras Flexbox de una manera didactica.

[Juego Flexbox froggy](https://flexboxfroggy.com/)
[Juego Flexbox Defense](http://www.flexboxdefense.com/)
[Juego Flexbox Zombies](https://mastery.games/flexboxzombies/)

### [Anterior](../sesion2)
### [Siguiente](../sesion4)