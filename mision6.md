# Misión 6: esquivar asteroides

## ¡Asteroides! @showdialog

Ahora vas a programar un **videojuego** para la micro:bit. Tu nave está abajo y se mueve con **A** y **B**. Desde arriba cae un asteroide: si te toca, se termina el juego. Cada asteroide que esquivás suma un punto.

## Paso 1: la nave y el asteroide

Creá dos variables: **nave** y **asteroide**.

Del cajón ``||game:Juego||`` usá ``||game:crear sprite en x: 2 y: 2||``. La nave va en **x: 2, y: 4** (abajo al medio). El asteroide en **x: 2, y: 0** (arriba).

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
```

## Paso 2: mover la nave

Con el botón **A** la nave va a la izquierda: ``||game:cambiar x por -1||``. Con el **B**, a la derecha: x por **1**. Elegí la variable **nave** en el bloque.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
```

## Paso 3: el asteroide cae

En ``||basic:para siempre||`` poné una ``||basic:pausa (ms) 400||`` y después ``||game:cambiar y por 1||`` con la variable **asteroide**.

Probalo: el asteroide baja y se queda abajo.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
basic.forever(function () {
    basic.pause(400)
    asteroide.change(LedSpriteProperty.Y, 1)
})
```

## Paso 4: un asteroide nuevo

Cuando el asteroide llega abajo (**y = 4**), vuelve arriba en un lugar al azar y sumás un punto.

Usá ``||logic:si … entonces / si no||``. Si ``||game:asteroide y||`` = 4: ``||game:fijar y a 0||``, ``||game:fijar x a||`` **elegir al azar de 0 a 4** y ``||game:cambiar puntuación por 1||``. Si no: que baje.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
basic.forever(function () {
    basic.pause(400)
    if (asteroide.get(LedSpriteProperty.Y) == 4) {
        asteroide.set(LedSpriteProperty.Y, 0)
        asteroide.set(LedSpriteProperty.X, randint(0, 4))
        game.addScore(1)
    } else {
        asteroide.change(LedSpriteProperty.Y, 1)
    }
})
```

## Paso 5: ¡choque!

Al final de **para siempre**, agregá otro ``||logic:si||``: si ``||game:asteroide ¿tocando nave?||``, entonces ``||game:fin del juego||``. La placa muestra cuántos puntos hiciste.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
basic.forever(function () {
    basic.pause(400)
    if (asteroide.get(LedSpriteProperty.Y) == 4) {
        asteroide.set(LedSpriteProperty.Y, 0)
        asteroide.set(LedSpriteProperty.X, randint(0, 4))
        game.addScore(1)
    } else {
        asteroide.change(LedSpriteProperty.Y, 1)
    }
    if (asteroide.isTouching(nave)) {
        game.gameOver()
    }
})
```

## Paso 6: el código y a la placa

Arriba de todo, en ``||basic:al iniciar||``, antes de crear los sprites, poné ``||basic:mostrar cadena||`` con **ASTRO**.

Tocá **Descargar** y jugá en la placa de verdad. Para jugar otra vez, apretá el botón de atrás de la placa (**reset**).

```blocks
basic.showString("ASTRO")
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(2, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
basic.forever(function () {
    basic.pause(400)
    if (asteroide.get(LedSpriteProperty.Y) == 4) {
        asteroide.set(LedSpriteProperty.Y, 0)
        asteroide.set(LedSpriteProperty.X, randint(0, 4))
        game.addScore(1)
    } else {
        asteroide.change(LedSpriteProperty.Y, 1)
    }
    if (asteroide.isTouching(nave)) {
        game.gameOver()
    }
})
```
