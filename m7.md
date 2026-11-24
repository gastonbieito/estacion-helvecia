# Misión 7: la radio de la estación

## Conectar la estación @showdialog

Cada micro:bit tiene una **radio** adentro. Las placas que están en el **mismo grupo** se escuchan entre ellas.

Vas a mandar mensajes a la placa de otra pareja. El juego te dice cuál es tu **grupo de radio** y con qué pareja te toca.

## El grupo

Del cajón ``||radio:Radio||`` arrastrá ``||radio:radio establecer grupo 1||`` adentro de ``||basic:al iniciar||``.

Cambiá el **1** por **tu grupo de radio** (está en el juego). La otra pareja tiene que poner el mismo número.

```blocks
radio.setGroup(1)
```

## Mandar una señal

Con el botón **A**: ``||radio:radio enviar número 0||`` con el número **1**.

Con el botón **B**: radio enviar número **2**.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})
radio.setGroup(1)
```

## Recibir la señal

Arrastrá ``||radio:al recibir radio recibirNúmero||``. Adentro, dos ``||logic:si||``:

- si **recibirNúmero = 1**, ``||basic:mostrar ícono||`` corazón.
- si **recibirNúmero = 2**, ``||basic:mostrar ícono||`` cara feliz.

En el simulador aparece una **segunda placa**: tocá A en una y mirá la otra.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        basic.showIcon(IconNames.Heart)
    }
    if (receivedNumber == 2) {
        basic.showIcon(IconNames.Happy)
    }
})
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})
radio.setGroup(1)
```

## El mensaje secreto

Con **A+B** se manda una palabra: ``||radio:radio enviar cadena||`` con **RED**.

Y para recibirla: ``||radio:al recibir radio recibirCadena||`` con ``||basic:mostrar cadena||`` y adentro **recibirCadena**.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        basic.showIcon(IconNames.Heart)
    }
    if (receivedNumber == 2) {
        basic.showIcon(IconNames.Happy)
    }
})
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
input.onButtonPressed(Button.AB, function () {
    radio.sendString("RED")
})
radio.onReceivedString(function (receivedString) {
    basic.showString(receivedString)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})
radio.setGroup(1)
```

## A la placa

Tocá **Descargar**. Cuando la otra pareja también lo tenga, apretá **A+B**: el código aparece **en la placa de ellos**. Ellos te lo dicen y vos lo escribís en el juego. ¡Y al revés!
