# Misión 3: el dado de meteoritos

## Lluvia de meteoritos @showdialog

Por la ventana pasan meteoritos y nadie sabe cuántos van a caer. Vas a hacer un **dado**: cuando sacudís la placa, sale un número **al azar** del 1 al 6.

## Paso 1: al sacudir

Del cajón ``||input:Entrada||`` arrastrá el bloque ``||input:al agitado||`` (el que dice **agitado**).

```blocks
input.onGesture(Gesture.Shake, function () {
})
```

## Paso 2: una variable para el dado

Creá una variable llamada **dado**. Adentro de **al agitado** poné ``||variables:fijar dado a||`` y en el hueco el bloque ``||math:elegir al azar de 0 a 10||`` (del cajón ``||math:Matemática||``). Cambiá los números por **1** y **6**.

```blocks
let dado = 0
input.onGesture(Gesture.Shake, function () {
    dado = randint(1, 6)
})
```

## Paso 3: mostrar el número

Debajo poné ``||basic:mostrar número||`` con la variable **dado** adentro.

En el simulador, tocá el botón **SHAKE** para sacudir.

```blocks
let dado = 0
input.onGesture(Gesture.Shake, function () {
    dado = randint(1, 6)
    basic.showNumber(dado)
})
```

## Paso 4: el seis de la suerte

Si sale **6**, cae el meteorito dorado y aparece el código.

Agregá un ``||logic:si||`` con ``||logic:dado = 6||``, y adentro ``||basic:mostrar cadena||`` con **COMETA**.

```blocks
let dado = 0
input.onGesture(Gesture.Shake, function () {
    dado = randint(1, 6)
    basic.showNumber(dado)
    if (dado == 6) {
        basic.showString("COMETA")
    }
})
```

## Paso 5: a la placa

Tocá **Descargar**. Sacudí la placa de verdad (con cuidado, sin desenchufarla) hasta que salga un 6. Escribí el código en el juego.
