# Misión 5: el sensor de luz

## ¿Es de día o de noche? @showdialog

La estación da vueltas alrededor de la Tierra y pasa del sol a la sombra. Las luces de la micro:bit también sirven para **medir la luz**.

Vas a hacer un medidor: cuanta más luz, más barritas encendidas.

## Paso 1: medir para siempre

Del cajón ``||led:LED||`` arrastrá ``||led:graficar barras de 0 hasta 255||`` adentro de ``||basic:para siempre||``.

En el primer hueco poné ``||input:nivel de luz||`` (del cajón ``||input:Entrada||``).

En el simulador, mové el círculo amarillo de arriba a la izquierda de la placa para cambiar la luz.

```blocks
basic.forever(function () {
    led.plotBarGraph(input.lightLevel(), 255)
})
```

## Paso 2: la temperatura

La placa también sabe la **temperatura**. Con el botón **A** que muestre ``||basic:mostrar número||`` con ``||input:temperatura (°C)||`` adentro.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(input.temperature())
})
basic.forever(function () {
    led.plotBarGraph(input.lightLevel(), 255)
})
```

## Paso 3: la noche espacial

Cuando hay muy poca luz, la estación está en la sombra y muestra el código.

Agregá un ``||logic:si||`` en **para siempre**, con ``||logic:0 < 0||``: a la izquierda **nivel de luz** y a la derecha **10**. Adentro, ``||basic:mostrar cadena||`` con **NOVA**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(input.temperature())
})
basic.forever(function () {
    led.plotBarGraph(input.lightLevel(), 255)
    if (input.lightLevel() < 10) {
        basic.showString("NOVA")
    }
})
```

## Paso 4: a la placa

Tocá **Descargar**. En la placa de verdad, **tapá las luces con la mano** para que sea de noche. Si no aparece, probá tapándola con un cuaderno. Escribí el código en el juego.
