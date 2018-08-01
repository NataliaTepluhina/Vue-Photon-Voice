# Vue-Photon-Voice

Vue application built with VueJS and Web Speech API to recognize speech to text and send commands to Particle Photon device.

[Live Demo](https://www.youtube.com/watch?v=6DLkr9--ans)

Particle Photon code in C++:

```
int style = 0;
LEDStatus status(RGB_COLOR_WHITE, LED_PATTERN_BLINK);

void setup() {
    status.setActive(true);
    status.setSpeed(LED_SPEED_SLOW);
    status.setPattern(LED_PATTERN_SOLID);
    Particle.function("colorMode",colorMode);
}

void loop() {
    switch(style) {
        case 0: status.setColor(RGB_COLOR_WHITE);
        break;
        case 1: status.setColor(RGB_COLOR_RED);
        break;
        case 2: status.setColor(RGB_COLOR_GREEN);
        break;
        case 3: status.setColor(RGB_COLOR_BLUE);
        break;
        case 4: status.setColor(RGB_COLOR_ORANGE);
        break;
        case 5: status.setColor(RGB_COLOR_YELLOW);
        break;
        case 6: status.setColor(RGB_COLOR_MAGENTA);
        break;
        case 7: {
            status.setPattern(LED_PATTERN_SOLID);
            status.setColor(RGB_COLOR_RED);
            delay(300);
            status.setColor(RGB_COLOR_ORANGE);
            delay(300);
            status.setColor(RGB_COLOR_YELLOW);
            delay(300);
            status.setColor(RGB_COLOR_GREEN);
            delay(300);
            status.setColor(RGB_COLOR_CYAN);
            delay(300);
            status.setColor(RGB_COLOR_BLUE);
            delay(300);
            status.setColor(RGB_COLOR_MAGENTA);
            delay(300);
        };
        break;
        case 8: status.setPattern(LED_PATTERN_SOLID);
        break;
        case 9: status.setPattern(LED_PATTERN_BLINK);
        break;
    }
}

int colorMode(String color) {
    if (color == "red") {
        style = 1;
    }
    else if (color == "green") {
        style = 2;
    }
        else if (color == "blue") {
        style = 3;
    }
    else if (color == "orange") {
        style = 4;
    }
    else if (color == "yellow") {
        style = 5;
    }
    else if (color == "magenta") {
        style = 6;
    }
    else if (color == "rainbow") {
        style = 7;
    }
    else if (color == "stop") {
        style = 8;
    }
    else if (color == "blink") {
        style = 9;
    }
    else if (color == "white") {
        style = 0;
    }
}
```

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn run serve
```

### Compiles and minifies for production

```
yarn run build
```
