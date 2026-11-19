# Persecusions: dos actividades de Scratch

En estas actividades crearás un juego en el que un personaje persigue el puntero del ratón. Tu misión es guiarlo hasta un objeto sin que te alcance.

- **Actividad 5:** el juego muestra un mensaje cuando ganas o pierdes.
- **Actividad 6:** el juego utiliza puntos, vidas y velocidad. Ganas al llegar a **10 puntos** y pierdes cuando tus **3 vidas** llegan a 0.

Trabaja primero la actividad 5 y comprueba que funciona antes de continuar con la 6.

## Actividad 5: primera versión de Persecusions

### 1. Prepara los objetos

1. Crea un proyecto nuevo en Scratch.
2. Elige un personaje que será el **perseguidor**. Lo puedes llamar `Perseguidor`: selecciónalo y escribe ese nombre en el campo **Objeto**, debajo del escenario.
3. Pulsa **Elegir un objeto** y añade el objeto que será la meta; por ejemplo, una estrella. Llámalo `Meta`.
4. Coloca la meta hacia la derecha del escenario y el perseguidor hacia la izquierda, separados uno del otro.
5. Si quieres, añade un fondo. La meta no necesita ningún programa en esta versión.

**Cómo se juega:** mueve el puntero del ratón para que el perseguidor vaya detrás. Intenta conducirlo hasta la meta. Si llega a la meta, ganas; si toca el puntero, pierdes.

> El puntero del ratón es la flecha que mueves en la pantalla; no tienes que crear un objeto con forma de ratón.

### 2. Haz que el personaje persiga al puntero

1. Selecciona **Perseguidor** en la lista de objetos y abre **Código**.
2. En **Eventos**, arrastra **al presionar bandera verde**.
3. En **Movimiento**, añade **ir a x: -120 y: 0**. Así empezará en el mismo sitio cada vez.
4. En **Control**, añade un bloque **por siempre**.
5. Dentro de **por siempre**, añade **apuntar hacia [puntero del ratón]**, de **Movimiento**.
6. Después añade **si... entonces... si no**, de **Control**.
7. En **Operadores**, coloca **[ ] < [ ]** en el rombo del **si**. En el primer hueco coloca **distancia a [puntero del ratón]**, de **Sensores**; en el segundo escribe `4`.
8. En el hueco **si**, coloca **ir a [puntero del ratón]**, de **Movimiento**. En el hueco **si no**, coloca **mover 4 pasos**.
9. Al final del hueco de **por siempre**, añade **esperar 0.03 segundos**, de **Control**. Ese pequeño descanso ayuda a que el movimiento sea visible.

Si está a menos de 4 pasos del puntero, el personaje irá directamente hasta él. Así no se pasará de largo por dar un paso demasiado grande.

```text
al presionar bandera verde
ir a x: -120 y: 0
por siempre
    apuntar hacia [puntero del ratón]
    si <(distancia a [puntero del ratón]) < 4> entonces
        ir a [puntero del ratón]
    si no
        mover 4 pasos
    esperar 0.03 segundos
```

**Prueba:** coloca el puntero en una zona alejada del perseguidor y pulsa la bandera verde. El personaje debe mirar hacia el puntero y seguirlo. Todavía no hay mensajes: los añadiremos ahora.

### 3. Comprueba si llega a la meta

Las siguientes instrucciones van **dentro de `por siempre`**, después del bloque completo **si... entonces... si no** que mueve al personaje y antes de **esperar**.

1. En **Control**, busca **si... entonces** y colócalo en el hueco de **por siempre**.
2. En **Sensores**, busca **¿tocando [puntero del ratón]?**. Cambia el desplegable a **Meta** y coloca el bloque en el hueco con forma de rombo del **si**.
3. Dentro del **si**, añade **decir [¡Has ganado!] durante 2 segundos**, de **Apariencia**.
4. Debajo de ese bloque, dentro del mismo **si**, añade **detener [todos]**, de **Control**.

### 4. Comprueba si alcanza al puntero

1. Debajo del primer **si**, pero todavía dentro de **por siempre**, añade otro **si... entonces**.
2. Coloca en su condición **¿tocando [puntero del ratón]?**, de **Sensores**.
3. Dentro del segundo **si**, añade **decir [¡Has perdido!] durante 2 segundos**.
4. Debajo añade **detener [todos]**.

> El juego comprueba primero la meta y después el puntero. Si el personaje toca ambos al mismo tiempo, se considerará que has ganado.

### 5. Programa completo del perseguidor

Los dos bloques **si** y el bloque **esperar** están dentro de **por siempre**. En cada **si**, el mensaje y **detener todos** están dentro de su hueco.

```text
al presionar bandera verde
ir a x: -120 y: 0
por siempre
    apuntar hacia [puntero del ratón]
    si <(distancia a [puntero del ratón]) < 4> entonces
        ir a [puntero del ratón]
    si no
        mover 4 pasos
    si <¿tocando [Meta]?> entonces
        decir [¡Has ganado!] durante 2 segundos
        detener [todos]
    si <¿tocando [puntero del ratón]?> entonces
        decir [¡Has perdido!] durante 2 segundos
        detener [todos]
    esperar 0.03 segundos
```

### 6. Prueba las dos posibilidades

1. Pulsa la bandera verde y guía al perseguidor hasta la **Meta**. Debe decir «¡Has ganado!» y detenerse.
2. Pulsa de nuevo la bandera verde y deja que alcance el **puntero**. Debe decir «¡Has perdido!» y detenerse.
3. Guarda el proyecto con el nombre `Persecusions - mensajes`.

**Consejo:** si el perseguidor se mueve demasiado rápido, puedes reducir tanto el `4` de la comparación como el `4` de **mover** al mismo número.

---

## Actividad 6: puntos, vidas y velocidad

Ahora cambiaremos el juego anterior para que no termine en el primer contacto.

- Al tocar la **Meta**, ganas **1 punto**.
- Al tocar el **puntero**, pierdes **1 vida**.
- Cada punto aumenta la **velocidad en 2**.
- Ganas al conseguir **10 puntos**.
- Pierdes al quedarte con **0 vidas**. Empiezas con 3.

Para conseguir otro punto debes sacar al perseguidor de la meta y volver a entrar en ella. Para perder otra vida, el perseguidor y el puntero deben separarse y volver a tocarse. Así un contacto continuo no suma muchos puntos ni quita todas las vidas de golpe.

### 1. Prepara una segunda versión

1. Abre tu proyecto de la actividad 5.
2. Guarda una copia con otro nombre, por ejemplo, `Persecusions - puntos y vidas`, para conservar la primera versión.
   - Si tienes sesión iniciada, puedes usar **Archivo → Guardar como una copia**.
   - Sin iniciar sesión, usa **Archivo → Guardar en tu ordenador** y guarda la segunda versión con otro nombre. Para abrir después un archivo guardado, usa **Archivo → Cargar desde tu ordenador**.
3. Selecciona **Perseguidor**.
4. Retira los bloques de su programa de la actividad 5: construiremos el nuevo programa paso a paso. La meta sigue siendo el otro objeto y no necesita programa.

> En Scratch, para separar un bloque, arrástralo fuera del grupo. Para eliminarlo, arrástralo hasta la zona de bloques de la izquierda. Comprueba que estás trabajando en la copia antes de borrar.

### 2. Crea las variables

1. En **Variables**, pulsa **Crear una variable**.
2. Crea **Puntos** y elige **Para todos los objetos**.
3. Repite el proceso con **Vidas** y **Velocidad**.
4. Crea también **ContactoMeta** y **ContactoRatón**, eligiendo **Solo para este objeto** en cada una. Nos servirán para recordar si el perseguidor ya estaba tocando la meta o el puntero.
5. Deja visibles en el escenario **Puntos**, **Vidas** y **Velocidad**. Puedes ocultar los marcadores de **ContactoMeta** y **ContactoRatón** desmarcando sus casillas en la categoría **Variables**.

**¿Qué significa 0 o 1 en las variables de contacto?**

- `0`: el contacto todavía no se ha contado.
- `1`: ya hemos contado ese contacto. Hay que separarse antes de volver a contarlo.

### 3. Prepara el inicio de la partida

En el **Perseguidor**, añade estos bloques:

1. **al presionar bandera verde**, de **Eventos**.
2. **ir a x: -120 y: 0**, de **Movimiento**.
3. Desde **Variables**, coloca los cinco bloques **dar a ... el valor ...**:
   - `Puntos` a `0`
   - `Vidas` a `3`
   - `Velocidad` a `2`
   - `ContactoMeta` a `0`
   - `ContactoRatón` a `0`
4. Debajo añade **por siempre**, de **Control**. Las instrucciones de los siguientes pasos irán **dentro** de este bloque.

```text
al presionar bandera verde
ir a x: -120 y: 0
dar a [Puntos] el valor 0
dar a [Vidas] el valor 3
dar a [Velocidad] el valor 2
dar a [ContactoMeta] el valor 0
dar a [ContactoRatón] el valor 0
por siempre
    ... instrucciones de los siguientes pasos ...
```

### 4. Haz que persiga al puntero usando la velocidad

Al principio del hueco de **por siempre**:

1. Añade **apuntar hacia [puntero del ratón]**, de **Movimiento**.
2. Añade **si... entonces... si no**, de **Control**.
3. En el rombo coloca una comparación **[ ] < [ ]**, de **Operadores**. En sus huecos coloca **distancia a [puntero del ratón]**, de **Sensores**, y **Velocidad**, de **Variables**.
4. En el hueco **si**, añade **ir a [puntero del ratón]**, de **Movimiento**.
5. En el hueco **si no**, añade **mover 10 pasos**, también de **Movimiento**. Sustituye `10` por el bloque ovalado **Velocidad**, de **Variables**.

Cuando `Velocidad` valga 2, el personaje se moverá 2 pasos cada vez; cuando valga 4, se moverá 4. Si el puntero está más cerca que esa distancia, irá directamente hasta él en vez de pasarse.

### 5. Cuenta un punto al tocar la meta

Debajo del bloque completo **si... entonces... si no** que mueve al personaje, todavía dentro de **por siempre**:

1. Añade **si... entonces... si no**, de **Control**.
2. En la condición, coloca **¿tocando [Meta]?**, de **Sensores**.
3. En el hueco de **si**, añade otro **si... entonces**. Este comprobará si el contacto aún no se ha contado.
4. En **Operadores**, busca **[ ] = [ ]** y colócalo en la condición del **si** interior. Introduce el bloque ovalado **ContactoMeta** en un lado y `0` en el otro.
5. Dentro del **si** interior añade, desde **Variables**:
   - **cambiar Puntos por 1**
   - **cambiar Velocidad por 2**
   - **dar a ContactoMeta el valor 1**
6. En el hueco de **si no** del bloque exterior, añade **dar a ContactoMeta el valor 0**. Así quedará preparado para contar otro punto cuando se separe de la meta.

```text
si <¿tocando [Meta]?> entonces
    si <(ContactoMeta) = 0> entonces
        cambiar [Puntos] por 1
        cambiar [Velocidad] por 2
        dar a [ContactoMeta] el valor 1
si no
    dar a [ContactoMeta] el valor 0
```

### 6. Termina la partida al conseguir 10 puntos

Debajo del bloque anterior, dentro de **por siempre**:

1. Añade **si... entonces**.
2. En su condición coloca **[ ] = [ ]**, de **Operadores**, con **Puntos** y `10`.
3. Dentro del **si**, añade **decir [¡Has ganado!] durante 2 segundos** y después **detener [todos]**.

```text
si <(Puntos) = 10> entonces
    decir [¡Has ganado!] durante 2 segundos
    detener [todos]
```

### 7. Resta una vida al tocar el puntero

Debajo de la comprobación de los 10 puntos, dentro de **por siempre**:

1. Añade otro **si... entonces... si no**.
2. Coloca **¿tocando [puntero del ratón]?** en la condición.
3. En el hueco **si**, añade otro **si... entonces** con la condición **ContactoRatón = 0**.
4. Dentro del **si** interior añade **cambiar Vidas por -1** y **dar a ContactoRatón el valor 1**.
5. En el hueco **si no** del bloque exterior, añade **dar a ContactoRatón el valor 0**.

```text
si <¿tocando [puntero del ratón]?> entonces
    si <(ContactoRatón) = 0> entonces
        cambiar [Vidas] por -1
        dar a [ContactoRatón] el valor 1
si no
    dar a [ContactoRatón] el valor 0
```

### 8. Termina la partida al quedarte sin vidas

Debajo del bloque anterior, dentro de **por siempre**:

1. Añade **si... entonces** con la condición **Vidas = 0**.
2. Dentro, añade **decir [¡Has perdido!] durante 2 segundos** y luego **detener [todos]**.
3. Al final de **por siempre**, después de todas las comprobaciones, añade **esperar 0.03 segundos**.

Los mensajes de ganar y perder ahora aparecen **solo al terminar la partida**, no en cada contacto.

### 9. Programa completo de la segunda versión

```text
al presionar bandera verde
ir a x: -120 y: 0
dar a [Puntos] el valor 0
dar a [Vidas] el valor 3
dar a [Velocidad] el valor 2
dar a [ContactoMeta] el valor 0
dar a [ContactoRatón] el valor 0
por siempre
    apuntar hacia [puntero del ratón]
    si <(distancia a [puntero del ratón]) < (Velocidad)> entonces
        ir a [puntero del ratón]
    si no
        mover (Velocidad) pasos
    si <¿tocando [Meta]?> entonces
        si <(ContactoMeta) = 0> entonces
            cambiar [Puntos] por 1
            cambiar [Velocidad] por 2
            dar a [ContactoMeta] el valor 1
    si no
        dar a [ContactoMeta] el valor 0
    si <(Puntos) = 10> entonces
        decir [¡Has ganado!] durante 2 segundos
        detener [todos]
    si <¿tocando [puntero del ratón]?> entonces
        si <(ContactoRatón) = 0> entonces
            cambiar [Vidas] por -1
            dar a [ContactoRatón] el valor 1
    si no
        dar a [ContactoRatón] el valor 0
    si <(Vidas) = 0> entonces
        decir [¡Has perdido!] durante 2 segundos
        detener [todos]
    esperar 0.03 segundos
```

> Cada **si no** pertenece al **si** exterior que comprueba si se está tocando algo. El **si** que comprueba la variable de contacto va dentro de la parte superior de ese bloque.

El programa comprueba primero los puntos y después las vidas. Si el perseguidor consigue el décimo punto y toca el puntero al mismo tiempo, gana.

### 10. Prueba la segunda versión

1. Pulsa la bandera verde. Comprueba que aparecen **Puntos = 0**, **Vidas = 3** y **Velocidad = 2**.
2. Guía al perseguidor hasta la meta: deben aparecer **Puntos = 1** y **Velocidad = 4**.
3. Déjalo tocar la meta sin separarse: no debería sumar más puntos por ese mismo contacto.
4. Guíalo fuera de la meta y vuelve a entrar: debe sumar otro punto y la velocidad debe aumentar otros 2.
5. Deja que alcance el puntero: debe perder una vida, no las tres de golpe. Sepáralos y permite que se vuelvan a tocar para perder otra.
6. Prueba que al llegar a **0 vidas** aparece «¡Has perdido!» y que al llegar a **10 puntos** aparece «¡Has ganado!». Puedes jugar dos partidas para comprobar ambos finales.
7. Pulsa de nuevo la bandera verde: puntos, vidas, velocidad y contactos deben volver a sus valores iniciales.

## Si algo no funciona

- **El perseguidor no sigue al puntero:** comprueba que has seleccionado el perseguidor y que **apuntar hacia [puntero del ratón]** y **mover** están dentro de **por siempre**.
- **No detecta la meta:** en el sensor, selecciona el nombre real del objeto de la meta, no el puntero.
- **No suma otro punto:** el perseguidor debe separarse de la meta antes de volver a tocarla.
- **Pierde varias vidas o suma varios puntos sin separarse:** revisa los bloques de **ContactoMeta** y **ContactoRatón** y dónde están colocados los dos **si no**.
- **No ves la velocidad:** marca la casilla de **Velocidad** en la categoría **Variables** y comprueba que su bloque está dentro de **mover**.
- **El personaje pasa de largo junto al puntero:** revisa la comparación **distancia a [puntero del ratón] < Velocidad** y que **ir a [puntero del ratón]** esté dentro de su parte **si**.
- **No reinicia la partida:** comprueba los cinco bloques de valores iniciales debajo de la bandera verde.

## Lista de comprobación

- [ ] En la actividad 5, el perseguidor sigue al puntero y aparecen los mensajes correctos al ganar o perder.
- [ ] En la actividad 6, empiezo con 0 puntos, 3 vidas y velocidad 2.
- [ ] Cada contacto nuevo con la meta suma 1 punto y 2 de velocidad.
- [ ] Cada contacto nuevo con el puntero resta 1 vida.
- [ ] Gano con 10 puntos y pierdo con 0 vidas.
- [ ] He guardado ambas versiones.
