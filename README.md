# Modified-Debug
#include "mbed.h"

InterruptIn button(USER_BUTTON);
volatile bool buttonPressed = false;

void onButtonPress() {
    buttonPressed = true;
}

int main() {
    while (true) {
        if (buttonPressed) {
            printf("Button pressed\n");
            buttonPressed = false;
        } else {
            // Debug: Check the state of the flag when the button is not pressed
            printf("Button not pressed or flag not set\n");
        }
        ThisThread::sleep_for(1000ms); // Using a longer delay to make the output readable
    }
}
