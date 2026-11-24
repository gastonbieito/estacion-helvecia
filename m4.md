# Misión 4: el sensor de gravedad

## La estación se inclina @showdialog

En el espacio no se sabe dónde está el piso. La micro:bit tiene un **acelerómetro**, un sensor que siente para dónde la inclinás.

Vas a hacer que la placa muestre una **flecha** hacia el lado que la inclinás.

## Inclinar a la izquierda

Del cajón ``||input:Entrada||`` arrastrá ``||input:si agitar||`` y cambiá **agitar** por **inclinar a la izquierda**.

Adentro poné ``||basic:mostrar flecha||`` apuntando al **Oeste**.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
```

## Inclinar a la derecha

Hacé otro igual para **inclinar a la derecha**, con la flecha al **Este**.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    basic.showArrow(ArrowNames.West)
})
input.onGesture(Gesture.TiltRight, function () {
    basic.showArrow(ArrowNames.East)
})
```

## Derecha y quieta

Cuando la placa está acostada sobre la mesa (**pantalla arriba**), muestra un ícono de cara feliz.

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

## El código escondido

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

## A la placa

Tocá **Descargar**. Con la placa enchufada, inclinala despacio para los costados y después hacia vos. Escribí el código en el juego.
