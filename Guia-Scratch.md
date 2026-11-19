# Mi primera guía de Scratch

## Hola, programadora

Esta guía te ayudará a crear tu primer videojuego paso a paso. No hace falta que sepas programar: iremos construyendo el proyecto poco a poco y podrás probarlo cada vez que termines una parte.

**Objetivo:** crear un juego en el que mueves un personaje con las flechas del teclado para atrapar una estrella y conseguir puntos.

**Tiempo aproximado:** 45-60 minutos. Puedes parar al final de cualquier paso y continuar otro día.

---

## 1. Entrar en Scratch

1. Abre un navegador de Internet.
2. Escribe esta dirección: [scratch.mit.edu/create](https://scratch.mit.edu/create).
3. Espera a que aparezca el editor de Scratch.
4. Si te pregunta el idioma, puedes elegir **Español** desde el icono del mundo.

No necesitas crear una cuenta para empezar. Si no has iniciado sesión, al final podrás guardar el proyecto en tu ordenador.

## 2. Conocer la pantalla

En el editor encontrarás estas zonas:

- **Escenario:** es la pantalla donde ocurre el juego. La bandera verde inicia los programas y el botón rojo los detiene.
- **Personajes u objetos:** son las figuras que aparecen en el juego. En Scratch también se llaman *objetos* o *sprites*.
- **Bloques:** están agrupados por colores y sirven para dar instrucciones.
- **Zona de programación:** aquí arrastras los bloques y los unes como piezas de un puzle.

### Prueba rápida

1. Haz clic en el personaje que aparece en el escenario.
2. Busca la categoría **Movimiento**.
3. Arrastra el bloque **mover 10 pasos** a la zona de programación.
4. Haz clic sobre el bloque.

**¿Qué ha pasado?** El personaje se ha movido. ¡Acabas de ejecutar una instrucción!

> Si el personaje se ha salido del escenario, no pasa nada. Puedes arrastrarlo de vuelta con el ratón.

## 3. Crear el juego

### Paso 1: elegir el escenario

1. En la zona de escenarios, haz clic en **Elegir un fondo**.
2. Escoge el fondo que más te guste.
3. Pulsa sobre el personaje para volver a programarlo.

**Comprueba:** ¿ves el fondo nuevo detrás del personaje?

### Paso 2: preparar al personaje

Al comenzar una partida queremos que el personaje aparezca siempre en el mismo sitio.

1. Selecciona el personaje.
2. Busca la categoría **Eventos** y arrastra el bloque **al presionar bandera verde** a la zona de programación.
3. En **Movimiento**, busca **ir a x: 0 y: 0** y únelo debajo del bloque anterior.
4. Si quieres, cambia los números para colocar al personaje donde prefieras.
5. Pulsa la bandera verde.

**Comprueba:** cada vez que pulsas la bandera verde, el personaje vuelve a ese lugar.

### Paso 3: mover al personaje con las flechas

Vamos a crear cuatro programas, uno para cada flecha. Los bloques de cada programa deben quedar unidos.

1. En **Eventos**, arrastra **al presionar tecla espacio** a una zona vacía de programación.
2. Haz clic en la palabra **espacio** y elige **flecha derecha**.
3. En **Movimiento**, añade debajo **cambiar x por 10**.
4. Repite los pasos para crear estos otros tres programas:

| Tecla | Bloque de movimiento |
|---|---|
| Flecha derecha | cambiar x por 10 |
| Flecha izquierda | cambiar x por -10 |
| Flecha arriba | cambiar y por 10 |
| Flecha abajo | cambiar y por -10 |

**Pista:** cambiar **x** mueve al personaje a derecha o izquierda. Cambiar **y** lo mueve arriba o abajo.

**Comprueba:** pulsa la bandera verde y prueba las cuatro flechas. Si una dirección está al revés, revisa si el número es positivo o negativo.

### Paso 4: añadir una estrella

1. Haz clic en **Elegir un objeto**.
2. Busca y selecciona una estrella. También puedes escoger otro objeto pequeño.
3. Comprueba que ahora aparecen el personaje y la estrella en la lista de objetos.
4. Selecciona la estrella.
5. En **Movimiento**, arrastra el bloque **ir a posición aleatoria** a su zona de programación.
6. Haz clic sobre ese bloque para probarlo. La estrella debería aparecer en otro lugar.

### Paso 5: crear el marcador de puntos

1. Con la estrella seleccionada, abre **Variables**.
2. Pulsa **Crear una variable**.
3. Escribe **Puntos** y deja seleccionada la opción para todos los objetos.
4. Pulsa **Aceptar**. Verás el marcador en el escenario.

Ahora prepara el marcador para que empiece de cero:

1. En **Eventos**, añade **al presionar bandera verde**.
2. En **Variables**, añade debajo **dar a Puntos el valor 0**.
3. En **Movimiento**, añade debajo **ir a posición aleatoria**.
4. Pulsa la bandera verde para comprobar que la estrella cambia de sitio y el marcador empieza en 0.

### Paso 6: sumar un punto al atrapar la estrella

La estrella comprobará una y otra vez si toca al personaje.

1. Selecciona la estrella.
2. En **Eventos**, arrastra **al presionar bandera verde**.
3. En **Control**, añade debajo el bloque **por siempre**.
4. Dentro del hueco del bloque **por siempre**, coloca un bloque **si... entonces** de la categoría **Control**.
5. En **Sensores**, busca **¿tocando [puntero del ratón]?**. Cambia el menú desplegable para que diga el nombre de tu personaje.
6. Coloca ese bloque con forma de rombo en el hueco del **si... entonces**.
7. Dentro del **si... entonces**, coloca estos dos bloques, en este orden:
   - En **Variables**: **cambiar Puntos por 1**.
   - En **Movimiento**: **ir a posición aleatoria**.

Tu programa de la estrella debería parecerse a esto:

```text
al presionar bandera verde
por siempre
    si <¿tocando [tu personaje]?> entonces
        cambiar [Puntos] por 1
        ir a posición aleatoria
```

**Comprueba:** pulsa la bandera verde y mueve el personaje hasta la estrella. Cada vez que la atrapes, el marcador debe subir un punto y la estrella debe aparecer en otro sitio.

¡Ya tienes un videojuego!

## 4. Guardar el proyecto

Guarda tu trabajo con frecuencia.

- **Si has iniciado sesión:** busca **Guardar ahora** en el menú **Archivo**.
- **Si no has iniciado sesión:** abre **Archivo** y elige **Guardar en tu ordenador**. Recuerda en qué carpeta guardas el archivo para poder abrirlo otro día.

Ponle un nombre fácil de reconocer, por ejemplo: **Atrapa la estrella - tu nombre**.

## 5. ¿Algo no funciona?

Prueba estas soluciones, una por una:

- **El personaje no se mueve:** comprueba que cada bloque de tecla está unido a su bloque de movimiento y que pruebas con la bandera verde en marcha.
- **Se mueve en la dirección equivocada:** revisa los números de **cambiar x** y **cambiar y**. Para ir a la izquierda o abajo, el número suele ser negativo.
- **No suma puntos:** selecciona la estrella y revisa que el bloque de **si... entonces** está dentro de **por siempre** y que pregunta si toca a tu personaje.
- **La estrella no cambia de lugar:** comprueba que **ir a posición aleatoria** está dentro del **si... entonces**, después de sumar el punto.
- **Los puntos no vuelven a cero:** asegúrate de que **dar a Puntos el valor 0** está conectado a **al presionar bandera verde**.
- **Un bloque ha desaparecido:** mira si está escondido detrás de otro bloque o fuera de la zona visible. Puedes alejar el zoom de la zona de programación.

Si sigue sin funcionar, detén el juego con el botón rojo, revisa el paso correspondiente y vuelve a probar.

## 6. Personaliza tu juego

Cuando el juego básico funcione, elige uno o dos retos:

- Cambia el fondo y los personajes.
- Haz que el personaje se mueva más rápido cambiando 10 por 15.
- Añade un sonido cuando atrapes la estrella. Busca un bloque de sonido y colócalo junto a los bloques que suman el punto.
- Añade otro objeto para atrapar y crea una variable diferente para contar sus puntos.
- Cambia el nombre de la variable **Puntos** por **Estrellas atrapadas**.

Haz un cambio cada vez y prueba el juego. Así sabrás qué cambio ha funcionado.

## 7. Mi lista de comprobación

Antes de dar el trabajo por terminado, comprueba:

- [ ] El proyecto tiene un nombre.
- [ ] He elegido un fondo y al menos dos objetos.
- [ ] Puedo mover al personaje con las cuatro flechas.
- [ ] La estrella aparece en una posición aleatoria al empezar.
- [ ] El marcador empieza en 0.
- [ ] Al tocar la estrella, consigo un punto.
- [ ] He guardado el proyecto.

## 8. Palabras importantes

- **Programa:** instrucciones que le damos al ordenador.
- **Bloque:** una instrucción de Scratch.
- **Evento:** algo que inicia un programa, como pulsar una tecla o la bandera verde.
- **Bucle:** instrucciones que se repiten; por ejemplo, **por siempre**.
- **Condición:** una pregunta que Scratch comprueba; por ejemplo, **¿está tocando al personaje?**
- **Variable:** un espacio donde guardamos un dato que puede cambiar, como la puntuación.
- **Coordenadas x e y:** números que indican dónde está un objeto en el escenario.

### Al terminar

¿Qué parte te ha salido mejor? ¿En qué paso has necesitado parar y revisar? Anota tus respuestas para comentarlas con tu profesora.

## Actividades de clase: Persecusions

Para las actividades en las que un personaje persigue el ratón, consulta la [guía paso a paso de Persecusions](./Guia-Persecusions-Scratch.md). Incluye la versión con mensajes y la versión con puntos, vidas y velocidad.
