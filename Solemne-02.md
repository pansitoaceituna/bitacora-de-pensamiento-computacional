## Integrantes del grupo

- (Martina Acevedo) [cuentaGithub](https://github.com/maaartiii)
- (Benjamin Marchant) [cuentaGithub](https://github.com/pansitoaceituna)

## Descripción del disco

![Portada de álbum xxxx yyyy](./img/lostres.jpg)


- Nmbre del album:
- "los tres"
- Año:
-  1991
- Artista:
-  los tres
- Tracklist:
- Somos tontos no pesados
- El haz sensor 
- Sudapara 
- Flores secas 
- Pajaros de fuego
- La primera vez 
- En jamaica 
- Un amor violento 
- Amores incompletos 
- He barrido el sol

```txt
1. Cancion 1
-  Amor violento
2. Cancion 2
-  He barrido el sol
3. Cancion 3
-  Sudapara
```

- Aspecto del álbum a desarrollar (premisa)

> Quisimos trabajar con los colores del álbum y ponerlos en el fondo con las herramientas que se nos han enseñado. 
Dependiendo de la posición del mouse, se muestran los distintos colores de la paleta original (azul, ocre y oscuro).
También nos gustó la idea de dejar una estela o rastro difuso cada vez que la imagen se mueva, inspirados en la atmósfera 
de sus videos musicales. Queríamos aventurarnos con ello, además de lograr que la imagen principal cambie dinámicamente de
tamaño conforme interactuamos con el lienzo.

## Conclusión del proceso

- Distancia entre premisa y resultado

> La verdad es que lo logramos bastante bien. Conseguimos una interacción fluida y cumplimos la gran mayoría
de las cosas que nos propusimos. Estamos muy contentos con el resultado del trabajo y con todo el conocimiento que adquirimos en el proceso.

- Cosas no conseguidas

> Incorporar múltiples imágenes independientes moviéndose en distintas direcciones simultáneamente.
Creemos que esto no se debió a una falta de capacidad, sino a que concentramos nuestros esfuerzos y nos preocupamos más
por perfeccionar la estela, la rotación y la transición de colores del fondo, los cuales encontramos más interesantes
de descubrir y desarrollar.

- Descubrimientos al trabajar

> Lograr el efecto de estela o rastro transparente al desplazar la imagen, incorporar partículas flotantes que simulan
la estética de sus videos musicales y programar una aceleración de giro suave que se activa únicamente al mantener presionado el mouse.

## Explicación del código (3 aspectos)

### Bloque de código 1
Este bloque cambia el color del fondo dependiendo de la posición vertical del mouse.

Arriba → azul
Medio → ocre
Abajo → oscuro

mouseY / height
convierte la posición del mouse en un valor entre 0 y 1.

Después lerpColor() mezcla colores suavemente.
```js
// Tu pedazo de código acá
```
let porcentajeY = mouseY / height;

if (porcentajeY < 0.5) {
 colorFondo = lerpColor(azulAlbum, ocreAlbum, porcentajeY * 2);
} else {
 colorFondo = lerpColor(ocreAlbum, oscuroAlbum, (porcentajeY - 0.5) * 2);
}

background(colorFondo);
### Bloque de código 2
Este bloque crea el efecto de “rastro” o “fantasma”.

Cada frame:

guarda la posición actual del mouse
dibuja una copia de la imagen
reduce su transparencia
estela.push()
guarda nuevas posiciones en un arreglo.

Y:

copia.alfa -= 5;
hace que desaparezcan lentamente.

```js
// Tu pedazo de código acá
```
let nuevaPosicion = {
  x: mouseX,
  y: mouseY,
  alfa: 255,
  w: tamano
};

estela.push(nuevaPosicion);

for (let i = 0; i < estela.length; i++) {
  let copia = estela[i];

  tint(255, copia.alfa);
  image(img, copia.x, copia.y, copia.w, copia.w);

  copia.alfa -= 5;
}

### Bloque de código 3
¿Qué hace?

Hace que la imagen gire suavemente cuando haces click


lerp() suaviza el cambio de velocidad.

En vez de pasar instantáneamente de:

0 → 0.1
la velocidad aumenta poco a poco.

```js
// Tu pedazo de código acá
if (mouseIsPressed) {
  velocidadRotacion = lerp(velocidadRotacion, velocidadMaxima, 0.1);
} else {
  velocidadRotacion = lerp(velocidadRotacion, 0, 0.1);
}

angulo += velocidadRotacion;


```

### Declaración sobre el uso de IA

- IA utilizada(s) y tipo de licencia (pago, gratuita)

> > Gemini (Gratuita).

- Problema a resolver a través de la IA

> Utilizamos la IA , específicamente para pedirle algunas ideas sobre cómo podíamos desarrollar
técnicamente dos funciones más complejas: la creación del efecto de estelacon la imagen en movimiento y la 
lógica para hacer que la imagen principal rotara al interactuar con el mouse. Cada vez que acudimos a ella,
nos preocupamos de pedirle explicaciones detalladas para entender perfectamente cómo funcionaba esa lógica de programación.

- Prompts utilizados

> "Queremos agregar un efecto de rastro o estela con la imagen del álbum que se vaya desvaneciendo a
medida que movemos el mouse por el lienzo. ¿Qué ideas o herramientas nos recomiendas usar en p5.js para lograrlo y
cómo funciona la lógica detrás de ese efecto?"

> "Tenemos la idea de que la imagen principal empiece a rotar en su propio eje cuando mantengamos presionado el mouse.
¿Cómo podemos programar esa rotación de manera suave y qué hacen exactamente las funciones push() y pop() 
para que el giro no afecte al resto de la pantalla? Explícanos paso a paso."



- Secciones de código entregadas por la IA

```js
//código entregado por IA acá
```

// Lógica sugerida para el desvanecimiento de los elementos de la estela
for (let i = estela.length - 1; i >= 0; i--) {
  if (estela[i].alfa <= 0) {
    estela.splice(i, 1);

// Estructura recomendada para suavizar la velocidad de rotación con el mouse
if (mouseIsPressed) {
  velocidadRotacion = lerp(velocidadRotacion, velocidadMaxima, 0.1); 
} else {
  velocidadRotacion = lerp(velocidadRotacion, 0, 0.1); 
}
angulo += velocidadRotacion;
```
