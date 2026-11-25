# Misión 6: esquivar asteroides

## ¡Asteroides! @showdialog

Ahora vas a programar un **videojuego** para la micro:bit. Tu nave está abajo y se mueve con **A** y **B**. Desde arriba cae un asteroide: si te toca, se termina el juego. Cada asteroide que esquivás suma un punto.

## La nave y el asteroide

Creá dos variables: **nave** y **asteroide**.

Del cajón ``||game:Juego||`` usá ``||game:crear sprite en x: 2 y: 2||``. La nave va en **x: 2, y: 4** (abajo al medio). El asteroide en **x: 0, y: 0** (arriba a la izquierda), así la primera caída no le pega a la nave.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
```

## Mover la nave

Con el botón **A** la nave va a la izquierda: ``||game:cambiar x por -1||``. Con el **B**, a la derecha: x por **1**. Elegí la variable **nave** en el bloque.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
input.onButtonPressed(Button.A, function () {
    nave.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    nave.change(LedSpriteProperty.X, 1)
})
```

## El asteroide cae

En ``||basic:para siempre||`` poné una ``||basic:pausa (ms) 400||`` y después ``||game:cambiar y por 1||`` con la variable **asteroide**.

Probalo: el asteroide baja y se queda abajo.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
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

## Un asteroide nuevo

Cuando el asteroide llega abajo (**y = 4**), vuelve arriba en un lugar al azar y sumás un punto.

Usá ``||logic:si … entonces / si no||``. Si ``||game:asteroide y||`` = 4: ``||game:establecer y en 0||``, ``||game:establecer x en||`` **escoger al azar de 0 a 4** y ``||game:agregar puntos a la puntuación actual||``. Si no: que baje.

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
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

## ¡Choque!

Al final de **para siempre**, agregá otro ``||logic:si||``: si ``||game:asteroide esta tocando nave||``, entonces ``||game:fin del juego||``. Si te toca, el juego termina y la placa muestra tus puntos (SCORE). Para jugar otra vez: el botón de reinicio del simulador o el botón de atrás de la placa (reset).

```blocks
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
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

## El código y a la placa

Arriba de todo, en ``||basic:al iniciar||``, antes de crear los sprites, poné ``||basic:mostrar cadena||`` con **ASTRO**.

Tocá **Descargar** y jugá en la placa de verdad. Para jugar otra vez, apretá el botón de atrás de la placa (**reset**).

```blocks
basic.showString("ASTRO")
let nave = game.createSprite(2, 4)
let asteroide = game.createSprite(0, 0)
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
