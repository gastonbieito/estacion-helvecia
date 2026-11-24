# Misión 1: el faro de la estación

## La estación está a oscuras @showdialog

La Estación Helvecia se quedó sin luz. Su faro tiene que volver a latir para que las naves la encuentren.

Vas a programar la micro:bit para que muestre un **corazón que late**, para siempre.

## Paso 1: un corazón grande

Abrí el cajón ``||basic:Básico||`` y arrastrá ``||basic:mostrar ícono||`` adentro de ``||basic:para siempre||``.

Elegí el **corazón grande**.

```blocks
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
})
```

## Paso 2: un corazón chico

Poné otro ``||basic:mostrar ícono||`` debajo del primero y elegí el **corazón chico**.

Mirá el simulador de la izquierda: el corazón ya late.

```blocks
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
    basic.showIcon(IconNames.SmallHeart)
})
```

## Paso 3: el código de la misión

Cuando la placa se prende, primero tiene que decir el código de la misión.

Arrastrá ``||basic:mostrar cadena||`` adentro de ``||basic:al iniciar||`` y escribí **SOL**.

```blocks
basic.showString("SOL")
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
    basic.showIcon(IconNames.SmallHeart)
})
```

## Paso 4: a la placa

Ahora a la placa de verdad:

1. La micro:bit tiene que estar enchufada a la compu.
2. Tocá **Descargar** (abajo a la izquierda).
3. Si es la primera vez, MakeCode te pide **Conectar dispositivo**: elegí la micro:bit de la lista y tocá **Conectar**.

Cuando termine, la placa dice **SOL** y después late. Escribí ese código en el juego.

```blocks
basic.showString("SOL")
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
    basic.showIcon(IconNames.SmallHeart)
})
```
