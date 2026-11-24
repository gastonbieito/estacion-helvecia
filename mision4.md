# Misión 4: el sensor de gravedad

## La estación se inclina @showdialog

En el espacio no se sabe dónde está el piso. La micro:bit tiene un **acelerómetro**, un sensor que siente para dónde la inclinás.

Vas a hacer que la placa muestre una **flecha** hacia el lado que la inclinás.

## Paso 1: inclinar a la izquierda

Del cajón ``||input:Entrada||`` arrastrá ``||input:al agitado||`` y cambiá **agitado** por **inclinar a la izquierda**.

Adentro poné ``||basic:mostrar flecha||`` (está en ``||basic:Básico||`` → **más**) apuntando al **Oeste**.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
```

## Paso 2: inclinar a la derecha

Hacé otro igual para **inclinar a la derecha**, con la flecha al **Este**.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
input.onGesture(Gesture.TiltRight, function () {
    basic.showArrow(ArrowNames.East)
})
```

## Paso 3: derecha y quieta

Cuando la placa está acostada sobre la mesa (**pantalla hacia arriba**), muestra un ícono de cara feliz.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
input.onGesture(Gesture.TiltRight, function () {
    basic.showArrow(ArrowNames.East)
})
input.onGesture(Gesture.ScreenUp, function () {
    basic.showIcon(IconNames.Happy)
})
```

## Paso 4: el código escondido

Si levantás la placa de la parte de arriba y la inclinás **hacia vos** (**logo abajo**), muestra el código **ORBITA**.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
input.onGesture(Gesture.TiltRight, function () {
    basic.showArrow(ArrowNames.East)
})
input.onGesture(Gesture.ScreenUp, function () {
    basic.showIcon(IconNames.Happy)
})
input.onGesture(Gesture.LogoDown, function () {
    basic.showString("ORBITA")
})
```

## Paso 5: a la placa

Tocá **Descargar**. Con la placa enchufada, inclinala despacio para los costados y después hacia vos. Escribí el código en el juego.
