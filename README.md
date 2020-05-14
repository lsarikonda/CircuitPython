# CircuitPython

function blink(color2: number, times: number) {
    for (let i = 0; i < times; i++) {
        light.setAll(0x000000)
        pause(100)
        if (color2 == 0) {
            light.setAll(0xff0000)
        } else {
            light.setAll(0x00ff00)
        }
        pause(100)
    }
}
function countdown(seconds: number) {
    for (let index = 0; index <= seconds; index++) {
        counter = seconds - (index + 1)
        if (counter > 9) {
            pause(1000)
            light.setPixelColor(counter % 10, 0xff00ff)
        } else {
            pause(1000)
            light.setPixelColor(counter, 0x0000ff)
        }
    }
    light.setAll(0xff0000)
    pause(1000)
    blink(0, 3)
    light.setAll(0x000000)
    pause(2000)
}
input.onLoudSound(function () {
    prep_countdown(20)
    countdown(20)
})
function prep_countdown(seconds: number) {
    for (let index = 0; index <= seconds; index++) {
        if (index < 10) {
            light.setPixelColor(index, 0x00ffff)
            pause(100)
        } else {
            light.setPixelColor(index % 10, 0x00ff00)
            pause(100)
        }
    }
}
let counter = 0
light.setBrightness(10)
blink(1, 2)
light.setAll(0x000000)
pins.LED.digitalWrite(true)
