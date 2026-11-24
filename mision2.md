# Misión 2: el panel de energía

## Cargar las baterías @showdialog

La estación necesita **10 cargas de energía**. Vas a hacer un panel: el botón **A** suma una carga y el botón **B** saca una.

Para guardar cuánta energía hay vas a usar una **variable**: una cajita con un nombre que guarda un número.

## Crear la variable

Abrí ``||variables:Variables||`` y tocá **Crear una variable**. Ponele de nombre **energia** (sin tilde).

Después arrastrá ``||variables:fijar energia a 0||`` adentro de ``||basic:al iniciar||``, y debajo ``||basic:mostrar número||`` con la variable **energia** adentro.

```blocks
let energia = 0
basic.showNumber(energia)
```

## El botón A suma

Del cajón ``||input:Entrada||`` arrastrá ``||input:al presionarse el botón A||``.

Adentro poné ``||variables:cambiar energia por 1||`` y ``||basic:mostrar número||`` con **energia**.

```blocks
let energia = 0
input.onButtonPressed(Button.A, function () {
    energia += 1
    basic.showNumber(energia)
})
basic.showNumber(energia)
```

## El botón B resta

Hacé lo mismo con el botón **B**, pero cambiando energia por **-1**.

Probalo en el simulador: tocá A y B.

```blocks
let energia = 0
input.onButtonPressed(Button.A, function () {
    energia += 1
    basic.showNumber(energia)
})
input.onButtonPressed(Button.B, function () {
    energia += -1
    basic.showNumber(energia)
})
basic.showNumber(energia)
```

## La batería llena

Cuando la energía llega a **10**, la estación da el código.

Del cajón ``||logic:Lógica||`` arrastrá ``||logic:si verdadero entonces||`` abajo de todo, adentro del botón A. En el hueco poné ``||logic:0 = 0||``: a la izquierda va **energia** y a la derecha **10**.

Adentro del **si** poné ``||basic:mostrar cadena||`` con **LUNA**.

```blocks
let energia = 0
input.onButtonPressed(Button.A, function () {
    energia += 1
    basic.showNumber(energia)
    if (energia == 10) {
        basic.showString("LUNA")
    }
})
input.onButtonPressed(Button.B, function () {
    energia += -1
    basic.showNumber(energia)
})
basic.showNumber(energia)
```

## A la placa

Tocá **Descargar** con la micro:bit enchufada.

En la placa de verdad, apretá **A** diez veces para cargar la batería. El código aparece solo cuando llegás a 10: escribilo en el juego.
