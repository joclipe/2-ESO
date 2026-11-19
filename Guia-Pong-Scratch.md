# Actividad 7: crea tu juego de Pong en Scratch

## ¿Qué vamos a construir?

En este juego, una pelota se mueve y rebota por el escenario. Controlarás una pala moviendo el ratón de izquierda a derecha. Cada vez que la pelota toque la pala, ganarás un punto. Si la pelota llega a la línea del fondo, perderás. Si consigues 10 puntos, ganarás.

Esta guía amplía con explicaciones propias el [tutorial Pong de Scratch Foundation](https://www.scratchfoundation.org/learn/learning-library/pong-game). También puedes consultar sus [tarjetas oficiales en español](https://cms.scratchfoundation.org/assets/ec4df5cb-efd1-4d0a-8987-db94bbd18fd7). Nuestra versión usa un objeto como línea de pérdida y añade algunas comprobaciones para hacer los rebotes más fiables.

Trabaja por partes y prueba el juego después de cada paso. No necesitas la extensión Lápiz.

## 1. Crear el proyecto y sus tres objetos

1. Abre [el editor de Scratch](https://scratch.mit.edu/create).
2. Ponle un nombre al proyecto, por ejemplo, `Mi juego de Pong`.
3. Si no vas a usar el gato, selecciónalo y elimínalo con el icono de la papelera de su miniatura.
4. Pulsa **Elegir un objeto** y busca una pelota. Selecciona la que te guste. En el campo **Objeto**, debajo del escenario, cambia su nombre a `Pelota`.
5. Añade un segundo objeto para usarlo como pala. Puedes buscar `Paddle` en la biblioteca de objetos. Cámbiale el nombre a `Pala`.
6. Añade un tercer objeto: coloca el ratón sobre **Elegir un objeto** y selecciona **Pintar**. Se abrirá el editor de disfraces.
7. Elige la herramienta **Rectángulo**, un relleno de color visible, por ejemplo rojo, y dibuja una barra horizontal, ancha y fina. Este será el suelo que no debe tocar la pelota. Cambia el nombre del objeto a `Linea`.
8. Vuelve a **Código**. Comprueba que en la lista de objetos aparecen **Pelota**, **Pala** y **Linea**.

> Si no encuentras una pala en la biblioteca, también puedes pintarla: dibuja un rectángulo horizontal. Conviene que la **Pala** y la **Linea** tengan colores diferentes.

### Coloca y ajusta los objetos

1. Selecciona **Linea**. En sus datos, debajo del escenario, escribe `0` en **x** y `-160` en **y**.
2. Si la línea no ocupa casi todo el ancho del escenario, abre su pestaña **Disfraces** y ensancha el rectángulo con la herramienta de selección. Procura que no sobresalga del escenario.
3. Selecciona **Pala** y escribe `0` en **x** y `-110` en **y**. Debe quedar por encima de la línea, sin tocarla.
4. Selecciona **Pelota** y colócala cerca del centro. Si es muy grande, reduce el valor de **Tamaño**, por ejemplo a `50`.
5. Comprueba que la pelota cabe entre la pala y la línea. Si ambas están demasiado juntas, mueve la línea un poco más abajo o la pala un poco más arriba.

**Recuerda:** en Scratch, **x** indica la posición horizontal e **y** la vertical. El centro del escenario es aproximadamente x: 0, y: 0.

## 2. Haz que la pelota se mueva y rebote en los bordes

1. Selecciona **Pelota** y abre **Código**.
2. En **Eventos**, arrastra **al presionar bandera verde**.
3. En **Movimiento**, añade **ir a x: 0 y: 0**. Así la pelota empezará en el centro.
4. Añade **apuntar en dirección 135**. Esta dirección hace que comience moviéndose en diagonal hacia abajo y hacia la derecha.
5. En **Control**, añade **por siempre**.
6. Dentro de **por siempre**, coloca:
   - **mover 5 pasos**, de **Movimiento**.
   - **si toca un borde, rebotar**, también de **Movimiento**.
   - **esperar 0.02 segundos**, de **Control**.

```text
al presionar bandera verde
ir a x: 0 y: 0
apuntar en dirección 135
por siempre
    mover 5 pasos
    si toca un borde, rebotar
    esperar 0.02 segundos
```

**Prueba:** pulsa la bandera verde. La pelota debe moverse y rebotar en los bordes. De momento puede llegar hasta abajo y rebotar allí: aún no hemos programado la línea de pérdida.

> Los bloques que aparecen indentados bajo **por siempre** van dentro del hueco del bloque naranja.

## 3. Mueve la pala con el ratón

1. Haz clic en **Pala** en la lista de objetos. Su zona de código está separada de la de la pelota.
2. En **Eventos**, arrastra **al presionar bandera verde**.
3. En **Movimiento**, añade **dar a y el valor -110**. Esto coloca la pala a una altura fija al comenzar.
4. En **Control**, añade **por siempre**.
5. Dentro de **por siempre**, coloca **dar a x el valor 0**, de **Movimiento**.
6. En **Sensores**, localiza el bloque ovalado **posición x del ratón** y arrástralo al hueco `0` de **dar a x el valor 0**.

```text
al presionar bandera verde
dar a y el valor -110
por siempre
    dar a x el valor (posición x del ratón)
```

**Prueba:** pulsa la bandera verde y mueve el ratón de izquierda a derecha sobre el escenario. La pala debe seguirlo horizontalmente sin subir ni bajar. La pelota sigue moviéndose con su propio programa.

**Si la pala queda demasiado cerca de la línea:** cambia `-110` por una posición más alta, por ejemplo `-100`. Utiliza esa misma altura cada vez que reinicies el proyecto.

## 4. Haz que la pelota rebote en la pala

Ahora programaremos la pelota para que cambie su dirección al tocar la pala. Solo contaremos el choque cuando la pelota vaya hacia abajo; así no volverá a rebotar inmediatamente mientras se separa.

1. Selecciona **Pelota**.
2. En su programa, localiza **si toca un borde, rebotar**.
3. Debajo de ese bloque y antes de **esperar**, coloca un bloque **si... entonces**, de **Control**.
4. En el rombo del **si**, coloca **¿tocando [Pala]?**, de **Sensores**. Usa el desplegable para elegir `Pala`.
5. Dentro de ese **si**, coloca otro **si... entonces**.
6. En la condición del **si** interior, vamos a comprobar si la pelota baja:
   - En **Operadores**, busca **[ ] o [ ]** y colócalo en el rombo.
   - Dentro del primer hueco coloca una comparación **[ ] > [ ]**; dentro del segundo, una comparación **[ ] < [ ]**.
   - En **Movimiento**, busca el bloque ovalado **dirección** y colócalo en cada comparación.
   - Escribe `90` a la derecha del primer signo y `-90` a la derecha del segundo.
7. Dentro del **si** interior añade **apuntar en dirección 90**, de **Movimiento**.
8. Sustituye el número `90` por una resta de **Operadores**: escribe `180` en el primer hueco y coloca **dirección** en el segundo.

Los bloques nuevos quedan así:

```text
si <¿tocando [Pala]?> entonces
    si <<(dirección) > 90> o <(dirección) < -90>> entonces
        apuntar en dirección ((180) - (dirección))
```

En Scratch, una dirección mayor que 90 o menor que -90 apunta hacia abajo. La operación `180 - dirección` cambia la parte vertical de la dirección: si la pelota bajaba hacia la derecha, empezará a subir hacia la derecha; si bajaba hacia la izquierda, subirá hacia la izquierda.

**Prueba:** mueve la pala debajo de la pelota. Cuando la pelota baje y toque la pala, debería volver hacia arriba. Todavía no sumará puntos.

## 5. Añade la línea que hace perder

La **Linea** es el objeto rojo que colocaste debajo de la pala. No necesita un programa propio: la pelota comprobará si la toca.

1. Selecciona **Pelota**.
2. En su programa, dentro de **por siempre**, coloca otro **si... entonces** debajo del bloque que comprueba la pala y antes de **esperar**.
3. En su condición coloca **¿tocando [Linea]?**, de **Sensores**.
4. Dentro del **si**, añade **decir [¡Has perdido!] durante 2 segundos**, de **Apariencia**.
5. Debajo añade **detener [todos]**, de **Control**.

```text
si <¿tocando [Linea]?> entonces
    decir [¡Has perdido!] durante 2 segundos
    detener [todos]
```

**Prueba:** deja pasar la pelota sin recogerla con la pala. Al tocar la línea, debe aparecer el mensaje y detenerse el juego. Después pulsa la bandera verde para comenzar otra partida.

Si la pelota rebota en el borde inferior sin tocar la línea, ensancha la línea o colócala un poco más arriba. Asegúrate de que sigue por debajo de la pala.

## 6. Crea y suma la puntuación

1. Selecciona **Pelota**.
2. En **Variables**, pulsa **Crear una variable**.
3. Escribe `Puntos`, elige **Para todos los objetos** y pulsa **Aceptar**. Deja marcada su casilla para ver el marcador en el escenario.
4. Busca **dar a [Puntos] el valor 0** y colócalo al principio del programa, debajo de **al presionar bandera verde** y antes de **por siempre**. Así cada partida empieza de cero.
5. Busca **cambiar [Puntos] por 1**.
6. Colócalo dentro del **si** que comprueba la dirección, justo después de **apuntar en dirección ((180) - (dirección))**.

La parte de la pala debe quedar así:

```text
si <¿tocando [Pala]?> entonces
    si <<(dirección) > 90> o <(dirección) < -90>> entonces
        apuntar en dirección ((180) - (dirección))
        cambiar [Puntos] por 1
```

**Prueba:** pulsa la bandera verde. El marcador debe empezar en 0. Cada vez que la pelota baje, toque la pala y rebote, debería sumar un punto.

## 7. Gana al conseguir 10 puntos

1. En el programa de **Pelota**, dentro de **por siempre**, añade otro **si... entonces** debajo de la comprobación de la pala.
2. En **Operadores**, busca **[ ] = [ ]** y colócalo en la condición.
3. En el primer hueco introduce el bloque ovalado **Puntos**, de **Variables**; en el otro escribe `10`.
4. Dentro del **si**, añade **decir [¡Has ganado!] durante 2 segundos** y después **detener [todos]**.

```text
si <(Puntos) = 10> entonces
    decir [¡Has ganado!] durante 2 segundos
    detener [todos]
```

Para comprobar esta parte sin jugar toda una partida, puedes cambiar **temporalmente** el 10 por 1. Al terminar la prueba, vuelve a escribir 10.

## 8. Revisa los programas completos

### Código de Pelota

Todas las comprobaciones están **dentro de `por siempre`**. La comprobación de la dirección está **dentro** de la que pregunta si toca la pala.

```text
al presionar bandera verde
dar a [Puntos] el valor 0
ir a x: 0 y: 0
apuntar en dirección 135
por siempre
    mover 5 pasos
    si toca un borde, rebotar
    si <¿tocando [Pala]?> entonces
        si <<(dirección) > 90> o <(dirección) < -90>> entonces
            apuntar en dirección ((180) - (dirección))
            cambiar [Puntos] por 1
    si <(Puntos) = 10> entonces
        decir [¡Has ganado!] durante 2 segundos
        detener [todos]
    si <¿tocando [Linea]?> entonces
        decir [¡Has perdido!] durante 2 segundos
        detener [todos]
    esperar 0.02 segundos
```

### Código de Pala

```text
al presionar bandera verde
dar a y el valor -110
por siempre
    dar a x el valor (posición x del ratón)
```

### Código de Linea

No necesita bloques en esta versión. La pelota detecta si la toca.

Si la pelota toca la pala y alcanza los 10 puntos en la misma vuelta en que toca la línea, el programa comprueba primero la victoria y muestra «¡Has ganado!».

## 9. Prueba y guarda tu juego

1. Pulsa la bandera verde. Comprueba que **Puntos** vuelve a 0 y que la pelota parte del centro.
2. Mueve el ratón para controlar la pala. Comprueba que la pelota rebota en ella y suma puntos.
3. Deja pasar la pelota: al tocar la línea debe aparecer «¡Has perdido!» y el juego debe detenerse.
4. Inicia otra partida y comprueba el mensaje de victoria al llegar a 10 puntos. Si haces la prueba con un límite más bajo, recuerda restaurarlo.
5. Guarda el proyecto. Si no tienes cuenta, usa **Archivo → Guardar en tu ordenador**. Para abrirlo otro día, usa **Archivo → Cargar desde tu ordenador**.

## 10. Si algo no sale

- **La pala no sigue el ratón:** selecciona **Pala** y revisa que **dar a x el valor (posición x del ratón)** esté dentro de **por siempre**.
- **La pala se mueve también arriba y abajo:** comprueba que usas **dar a x el valor** y no **ir a puntero del ratón**.
- **La pelota atraviesa la pala:** revisa que el sensor diga **Pala** y que la comprobación esté en el programa de **Pelota**. Si va demasiado rápido, reduce **mover 5 pasos** a **mover 3 pasos**.
- **La pelota rebota pero no suma:** coloca **cambiar Puntos por 1** junto al cambio de dirección, dentro del **si** que comprueba si baja.
- **La puntuación no vuelve a 0:** revisa **dar a Puntos el valor 0** al principio del programa, fuera de **por siempre**.
- **La pelota toca abajo y no pierdo:** comprueba que la línea sea un objeto llamado **Linea**, que cubra casi todo el ancho y que el sensor de la pelota seleccione ese objeto.
- **La partida se termina nada más empezar:** comprueba que la pelota empieza en x: 0, y: 0, lejos de la línea, y que **detener todos** está dentro del **si** correspondiente.
- **La pelota parece no moverse:** revisa que **mover 5 pasos** y **si toca un borde, rebotar** estén dentro de **por siempre**.

## 11. Retos opcionales

Cuando el juego básico funcione, prueba uno de estos cambios:

- Añade un sonido al rebotar: selecciona **Pelota**, añade un sonido en su pestaña **Sonidos** y coloca **iniciar sonido** junto a **cambiar Puntos por 1**.
- Cambia el fondo y los colores.
- Prueba con una pala más ancha o más estrecha. ¿Cómo cambia la dificultad?
- Experimenta cambiando los puntos necesarios para ganar. Prueba tu juego después de cada cambio.

## Lista de comprobación

- [ ] Tengo una pelota, una pala y una línea de pérdida.
- [ ] La pelota se mueve y rebota en los bordes y en la pala.
- [ ] Controlo la pala con el ratón.
- [ ] Cada rebote en la pala suma un punto.
- [ ] Pierdo si la pelota toca la línea y gano al llegar a 10 puntos.
- [ ] La puntuación vuelve a 0 al empezar una nueva partida.
- [ ] He guardado mi proyecto.
