# Bad USB
![alt text](image-5.png)
## Ce este?
Un Bad USB este un device ce se comporta ca o tastatura pentru a realiza un keystroke injection attack, care poate fi folosit pentru a deschide un terminal, iar apoi sa ruleze comenzi pe un computer tinta.

Pe exterior, un Bad USB de obicei este foarte asemanator cu un USB normal. Insa, pe interior, are un chip programat sa se comporte precum o tastatura USB, pentru a deschide un terminal si a rula comenzi in cateva secunde.

## De ce functioneaza?
Functioneaza pentru ca abuzeaza de exceptiile noastre si increderea fata de cabluri USB si Flash Drive-uri. De altfel, se folosesc si de increderea computerului tinta in tastaturile USB.

Input-ul de tastatura este crezut fara dubii de computer, pentru ca acesta vine direct de la un om, om care are acces total asupra acestuia. Problema intervine cand keystroke-urile sunt introduse, pentru ca acesta nu stie daca vin chiar de la un om sau prin alta metoda.

## Keystroke Injection Attack
Bad USB-urile sunt programate sa execute atacuri de tip keystroke injection prin trimiterea unei secvente predefinite de taste catre computer. Sistemul de operare interpreteaza aceste semnale ca venind de la un utilizator uman si le proceseaza ca atare, desi ele sunt injectate cu viteze supraomenesti (peste 9000 de caractere pe secunda).

Depinzand de keystroke-urile trimise, un Bad USB poate sa instaleze pe un computer malware sau sa extraga date private. Poate sa faca aproape tot ce poti face si tu cu computerul tau chiar acum.

# Exemplu de Bad USB
![alt text](image-4.png)
In aceasta documentatie am ales sa folosesc un ATtiny85, pentru ca este un exemplu foarte bun si de altfel potrivit pentru toate bugetele.

1. Deschidem Arduino IDE, apasam pe butonul File > Preferences si introducem acest [URL](https://raw.githubusercontent.com/digistump/arduino-boards-index/master/package_digistump_index.json) in sectiunea de "Additional boards manager URLs"

![alt text](image-1.png)

2. Setam board-ul prin a apasa butonul Tools > Board > Digistump AVR Boards unde selectam Digispark (Default - 16.5mhz)

![alt text](image-1-1.png)

3. Acum trebuie sa introducem un cod pe care ATtiny85-ul nostru sa il execute la introducerea intr-un computer.

```
// Includem biblioteca necesara pentru simularea tastaturii USB
#include "DigiKeyboard.h"

// URL-ul pe care vrei sa-l deschizi
const char* targetUrl = "https://github.com/Paius-George";

void setup() {

  DigiKeyboard.delay(5000); // Asteapta 5 secunde

  // 1. Apasa tasta Windows (GUI) + R pentru a deschide fereastra "Run" (Executare)
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(500); 

  // 2. Tasteaza URL-ul dorit
  DigiKeyboard.print(targetUrl); 
  DigiKeyboard.delay(500);

  // 3. Apasa ENTER pentru a executa comanda (deschide link-ul in browserul implicit)
  DigiKeyboard.sendKeyStroke(KEY_ENTER); 
  DigiKeyboard.delay(500);

  // sau sa intre într-o bucla care nu face nimic.
}

void loop() {
  // Loop-ul este lasat gol, deoarece actiunea dorita se executa doar o singura data(in setup)
}
```

Am scris un cod care deschide in browser-ul computer-ului implicit pagina mea de Github. Am adaugat si comentarii pentru a intelege fiecare linie de cod si ce rol are.

4. Apasam pe buton-ul de upload si punem codul pe device-ul conectat (in cazul meu ATtiny85). 

![alt text](image-2.png)
5. Observam ca in terminal ni se spune sa introducem ATtiny-ul, asadar il introducem.


6. Putem observa acum ca totul este in regula si ATtiny-ul este pregatit sa execute codul caruia i-am dat la pasul 3 upload.

![alt text](image-3.png)

7. Dupa ce am dat upload, putem scoate ATtiny-ul din computer si la reintroduce va executa codul.


# Bad USB
![alt text](image-5.png)
## Ce este?
Un Bad USB este un device ce se comporta ca o tastatura pentru a realiza un keystroke injection attack, care poate fi folosit pentru a deschide un terminal, iar apoi sa ruleze comenzi pe un computer tinta.

Pe exterior, un Bad USB de obicei este foarte asemanator cu un USB normal. Insa, pe interior, are un chip programat sa se comporte precum o tastatura USB, pentru a deschide un terminal si a rula comenzi in cateva secunde.

## De ce functioneaza?
Functioneaza pentru ca abuzeaza de exceptiile noastre si increderea fata de cabluri USB si Flash Drive-uri. De altfel, se folosesc si de increderea computerului tinta in tastaturile USB.

Input-ul de tastatura este crezut fara dubii de computer, pentru ca acesta vine direct de la un om, om care are acces total asupra acestuia. Problema intervine cand keystroke-urile sunt introduse, pentru ca acesta nu stie daca vin chiar de la un om sau prin alta metoda.

## Keystroke Injection Attack
Bad USB-urile sunt programate sa execute atacuri de tip keystroke injection prin trimiterea unei secvente predefinite de taste catre computer. Sistemul de operare interpreteaza aceste semnale ca venind de la un utilizator uman si le proceseaza ca atare, desi ele sunt injectate cu viteze supraomenesti (peste 9000 de caractere pe secunda).

Depinzand de keystroke-urile trimise, un Bad USB poate sa instaleze pe un computer malware sau sa extraga date private. Poate sa faca aproape tot ce poti face si tu cu computerul tau chiar acum.

# Exemplu de Bad USB
![alt text](image-4.png)
In aceasta documentatie am ales sa folosesc un ATtiny85, pentru ca este un exemplu foarte bun si de altfel potrivit pentru toate bugetele.

1. Deschidem Arduino IDE, apasam pe butonul File > Preferences si introducem acest [URL](https://raw.githubusercontent.com/digistump/arduino-boards-index/master/package_digistump_index.json) in sectiunea de "Additional boards manager URLs"
![alt text](image.png)

2. Setam board-ul prin a apasa butonul Tools > Board > Digistump AVR Boards unde selectam Digispark (Default - 16.5mhz)
![alt text](image-1.png)

3. Acum trebuie sa introducem un cod pe care ATtiny85-ul nostru sa il execute la introducerea intr-un computer.

```
// Includem biblioteca necesara pentru simularea tastaturii USB
#include "DigiKeyboard.h"

// URL-ul pe care vrei sa-l deschizi
const char* targetUrl = "https://github.com/Paius-George";

void setup() {

  DigiKeyboard.delay(5000); // Asteapta 5 secunde

  // 1. Apasa tasta Windows (GUI) + R pentru a deschide fereastra "Run" (Executare)
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(500); 

  // 2. Tasteaza URL-ul dorit
  DigiKeyboard.print(targetUrl); 
  DigiKeyboard.delay(500);

  // 3. Apasa ENTER pentru a executa comanda (deschide link-ul in browserul implicit)
  DigiKeyboard.sendKeyStroke(KEY_ENTER); 
  DigiKeyboard.delay(500);

  // sau sa intre într-o bucla care nu face nimic.
}

void loop() {
  // Loop-ul este lasat gol, deoarece actiunea dorita se executa doar o singura data(in setup)
}
```

Am scris un cod care deschide in browser-ul computer-ului implicit pagina mea de Github. Am adaugat si comentarii pentru a intelege fiecare linie de cod si ce rol are.

4. Apasam pe buton-ul de upload si punem codul pe device-ul conectat (in cazul meu ATtiny85). 

![alt text](image-2.png)

5. Observam ca in terminal ni se spune sa introducem ATtiny-ul, asadar il introducem.


6. Putem observa acum ca totul este in regula si ATtiny-ul este pregatit sa execute codul caruia i-am dat la pasul 3 upload.

![alt text](image-3.png)

7. Dupa ce am dat upload, putem scoate ATtiny-ul din computer si la reintroduce va executa codul.
![alt text](<Gif ATtiny85.gif>)

