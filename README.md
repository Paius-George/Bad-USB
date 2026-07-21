# Bad USB

*[Versiunea în limba română →](README.ro.md)*

<img alt="image" src="https://github.com/user-attachments/assets/9d181f49-eeff-4c67-9be1-8f7fbe8d94f4" />

## What is it?
A Bad USB is a device that behaves like a keyboard in order to carry out a keystroke injection attack, which can be used to open a terminal and then run commands on a target computer.

On the outside, a Bad USB usually looks very similar to a normal USB. On the inside, however, it has a chip programmed to behave like a USB keyboard, so it can open a terminal and run commands within a few seconds.

## Why does it work?
It works because it abuses our assumptions and trust toward USB cables and Flash Drives. On top of that, it also exploits the target computer's trust in USB keyboards.

Keyboard input is believed without a doubt by the computer, because it comes directly from a human — a human who has full access to it. The problem arises when the keystrokes are injected, because the computer does not know whether they actually come from a human or through some other method.

## Keystroke Injection Attack
Bad USBs are programmed to execute keystroke injection attacks by sending a predefined sequence of keys to the computer. The operating system interprets these signals as coming from a human user and processes them as such, even though they are injected at superhuman speeds (over 9000 characters per second).

Depending on the keystrokes sent, a Bad USB can install malware on a computer or extract private data. It can do almost anything you yourself could do with your computer right now.

## How can we prevent such an attack?

A Bad USB attack, as mentioned above, only works when such a device is plugged into our computer. Therefore, as precautionary rules, we should:

- Never connect an unknown USB device: stick or cable (because there is, for example, the [O.MG Cable](https://shop.hak5.org/products/omg-cable?srsltid=AfmBOopnsigoQO3fz623PuO05h8JmmDPtADbqIenAGjWnPTwGRKfzp-X), which looks exactly like any ordinary charging cable).
- We should never leave our computer unattended while it is unlocked.

# Example of a Bad USB

<img alt="image" src="https://github.com/user-attachments/assets/6b9ad99d-6b89-4aa1-ad80-ddd5007d6549" />

In this documentation I chose to use an ATtiny85, because it is a very good example and, moreover, suitable for all budgets.

1. We open the Arduino IDE, click on File > Preferences, and enter this [URL](https://raw.githubusercontent.com/digistump/arduino-boards-index/master/package_digistump_index.json) in the "Additional boards manager URLs" section.

<img alt="image" src="https://github.com/user-attachments/assets/1c8f2964-f0cf-4c30-8c62-e3db5a44c710" />


2. We set the board by clicking Tools > Board > Digistump AVR Boards, where we select Digispark (Default - 16.5mhz).

<img alt="image" src="https://github.com/user-attachments/assets/e673f8a7-7b48-4056-a2c7-70987d1e9e1b" />


3. Now we need to load a piece of code for our ATtiny85 to execute when plugged into a computer.

```
// Include the library needed to simulate the USB keyboard
#include "DigiKeyboard.h"

// The URL you want to open
const char* targetUrl = "https://github.com/Paius-George";

void setup() {

  DigiKeyboard.delay(5000); // Wait 5 seconds

  // 1. Press the Windows key (GUI) + R to open the "Run" window
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(500); 

  // 2. Type the desired URL
  DigiKeyboard.print(targetUrl); 
  DigiKeyboard.delay(500);

  // 3. Press ENTER to execute the command (opens the link in the default browser)
  DigiKeyboard.sendKeyStroke(KEY_ENTER); 
  DigiKeyboard.delay(500);

  // or enter a loop that does nothing.
}

void loop() {
  // The loop is left empty, because the desired action runs only once (in setup)
}
```

I wrote a piece of code that opens my GitHub page in the computer's default browser. I also added comments so you can understand each line of code and its role.

4. We click the upload button and put the code on the connected device (in my case, the ATtiny85).


5. We notice that the terminal tells us to plug in the ATtiny, so we plug it in.

<img alt="image" src="https://github.com/user-attachments/assets/10c7aac5-6503-4c63-9436-9dbe5482dcf9" />


6. We can now see that everything is fine and the ATtiny is ready to execute the code we uploaded in step 3.
   
<img alt="image" src="https://github.com/user-attachments/assets/30ad645d-acc6-4da9-b436-ef6b4b6b2a01" />


7. After uploading, we can remove the ATtiny from the computer, and re-inserting it will execute the code.


![Image](https://github.com/user-attachments/assets/6aface64-925a-4319-a62b-428f554b8128)

----

###### *Thank you for going through my documentation!*
