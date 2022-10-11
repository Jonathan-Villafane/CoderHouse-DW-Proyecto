# CoderHouse - Diseño Web 2022 - Proyecto Final - Jonathan Villafañe

## Cosas que aprendí

- HTML (estructura, semántica, SEO)

- CSS (FLEX y GRID)

- SASS (clase base, extend, variables, mapas, mixins)

---

## Características y detalles

### Cosas que merecen ser mencionadas, ya sea por la funcionalidad o la dificultad que me representó lograrlas.

---

## #Index

Lo principal que aprendí en el index, fue desde un principio la dificultad que tenía para ordenar y manejar el tamaño de las "**secciones**", las cuales eventualmente aprendí a manejar como "**contenedores**", y ni hablemos de haber pasado por el proceso de aprender FLEX, luego GRID, y por último BOOTSTRAP.

Me hubiera gustado poner un **carousel** en vez de la imagen estática, pero no me terminó convenciendo cómo quedaban las distintas variantes, y peor aún, no tenía unas imágenes que queden realmente bien.

## #Nosotros

Las fuentes en esta sección me complicaron las cosas, y no estoy del todo conforme, pero tenía que conjugar la cantidad de texto, la fuente, el tamaño, y también, que el total no ocupe mucho más que la tarjeta al costado, ya que quedaría desbalanceado.

## #Servicios

Me costó el hecho de que en general, los estudios contables no suelen explayarse dentro de sus secciones de servicios, por lo cual tuve que improvisar un pocos los textos o extenderlos, para que haya cierta correspondencia visual entre todos estos.

También se me ocurrió poner una navBar secundaria, para que el usuario no tenga que subir hasta la primer nav, que sea mas directo con un solo click, y que indique también en dónde se encuentra uno. Aunque por desgracia no logré encontrar la forma de modificar el **color** del **active** de la nav de tabs de Bootstrap. 

## #Sitios de Interés

Al principio la había realizado usando una tabla muy rústica, pero luego salté a GRID y me quedó un poco mejor, pero todavia tenía algunos problemas con el comportamiento de cada elemento.

Luego ya al usar Bootstrap, me resultó mucho más sencillo el realizar modificaciones e incluso, resolver lo que me molestaba de los elementos, que no respondían como deseaba, al moverse entre resoluciones para cambiar y testear la vista mobile.

## #Contacto

Ufff, en esta tuve varias complicaciones...
En un principio, como todavía no usaba el concepto de "**compartimentar**" todo, me costó lograr separar los elementos.

Pero después ya pude arreglar cosas, como el tamaño de la **caja** de **texto** del **formulario** (que aparecia con cualquier tamaño) y también, buscando una solución en google, pude hacer que el mapa de GoogleMaps (elemento iFrame) pudiera ser responsive.

## *body

Al body le había puesto un fondo con simil efecto "paralax", pero al final simplemente le dejé una pequeña animación hecha con un gradiente cambiando de dirección.

```sass
body{
    background-size: auto;
    animation: bg-animate 3s ease-in-out infinite;
}

@keyframes bg-animate{
    0%{background: linear-gradient(45deg, rgb(107, 106, 106), rgb(181, 173, 186),rgb(177, 138, 138));}
    50%{background: linear-gradient(90deg, rgb(107, 106, 106), rgb(181, 173, 186),rgb(177, 138, 138));}
    100%{background: linear-gradient(135deg, rgb(107, 106, 106), rgb(181, 173, 186),rgb(177, 138, 138));}
}
```

## *navBar

La navBar pasó por varias etapas.
Primero tuve que hacerla como pude, con **position** y cosas fijas o estáticas, que se rompían con facilidad al querer implementar un **submenú**.
Después pasé por la etapa de FLEX, aunque no me resultó del todo útil.

Para terminar, la forma final fue lograda con Bootstrap, ya que si bien usa FLEX, me resultó más facil acomodar las cosas como quería, usando la navBar de Bootstrap y dándole los **colores** y **animaciones** con CSS.

**Hablando de animaciones, hay una segunda versión de la animación de los botones (está comentada)**

Si bien la vista mobile de la navBar me pareciá bien, le cambié el **alpha** del fondo de la navBar por sugerencia de la profesora, que para lograr hacerlo de manera específica y clara, tuve que hacer algo que nos enseñó la profesora, y esto es... usar un **media querie** dentro del código que había hecho en SASS.

Me parece relevante resaltarlo porque fue lo más útil que me resultó, de haber aprendido el concepto de **media queries**, porque al fin y al cabo, con Bootstrap ya casi tenemos resuelto ese tema del **responsive**.

```sass
#navBar {
    background-color: $color-main;
    @media screen and (max-width:991px) {
        background-color: rgba(173, 216, 230, 0.8);
    }
}
```

## *footer

Con este elemento mi dificultad pasaba mas por el diseño y los colores que por la funcionalidad.
Pero al llegar a usar Bootstrap, se me facilitó encontrar distintas "plantillas" y opté por una que me gustó, para luego retocar y configurar a mi gusto.

**Los links del footer llevan a la página 404**

Mi "joyita" del footer, fue haber logrado hacer una **animación** (básica, pero efectiva) de **rotación** con un poquito de **blur**.

```sass
footer div section a img:hover{
    filter: blur(1px);
    animation: icon-animate 0.2s ease-out forwards;
}


@keyframes icon-animate{
    0%{transform: rotate(90deg);}
    25%{transform: rotate(180deg);}
    50%{transform: rotate(270deg);}
    100%{transform: rotate(360deg);}
}
```

## -SASS

Sin duda fue lo que más me gustó haber aprendido a usar. En especial los mixins mezclados con maps.
Es una forma de elegir parámetros para los mixins, pero con mis propias formas de llamar las variables contenidas en los mapas.

Me imagino que en un proyecto grande debe ser glorioso poder modificar cosas, simplemente cambiando algo dentro de los mapas.

```sass
// mapa de size de font
$textSize:(
    '2.5': 2.5rem,
    '3': 3rem,
    '4': 4rem,
    '5': 5rem,
    '6': 6rem,
);

// mapa de align de texto
$textPos:(
    'l': left,
    'c': center,
    'r': right,
);
```

```sass
// mixin de pos y size (l, c, r ; 3-6)
@mixin textBoxFont ($align, $size){
    text-align: map-get($map: $textPos, $key: $align);
    font-size: map-get($map: $textSize, $key: $size);
}

// mixin de tamaño (3-6) pero con margin establecido
@mixin textBoxMar ($size){
    font-size: map-get($map: $textSize, $key: $size);
    margin: $margin-10;
}
```

---

## Conclusiones

Me llevo un buen aprendizaje, aunque parezca recién haber mojado la punta de los dedos de los pies.
Pero supongo que me prepara para poder continuar con el aprendizaje, y empezar a meterme de verdad en el extenso mundo de la programación.

Saludos a todo aquel que se haya tomado el tiempo de leer esto.
