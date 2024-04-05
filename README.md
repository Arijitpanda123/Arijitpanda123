#include <Keypad.h>


char * password = “3690”; // To increase the passcode length change the numerical to the size after position


int position = 0;


const byte ROWS = 4; // 4 rows

const byte COLS = 4; // 4 columns


char keys[ROWS][COLS] =

{

{‘1′,’2′,’3′,’A’},

{‘4′,’5′,’6′,’B’},

{‘7′,’8′,’9′,’C’},

{‘*’,’0′,’#’,’D’}

}; //mapping of the keys done w.r.t to the grid keypad


byte rowPins[ROWS] = { 13, 12, 11, 10 }; //connection of rows pins to the Arduino

byte colPins[COLS] = { 9, 8, 7, 6 }; // connection of the columns pins to the Arduino


Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS, COLS );


int Lock = 5; // Connecting the relay to the 5th pin


void setup()

{


pinMode(Lock, OUTPUT);

LockedPosition(true);

}


void loop()

{

char key = keypad.getKey();

if (key == ‘*’ || key == ‘A’) //OR operator used to lock the device back again

{

position = 0;

LockedPosition(true);

}

if (key == password[position])

{

position ++;

}

if (position == 4) // change this if you want to increase the password length

{

LockedPosition(false);

}

delay(100);

}

void LockedPosition(int locked)

{

if (locked)

{

digitalWrite(Lock, LOW);

}

else

{

digitalWrite(Lock, HIGH);

}

}
- 👋 Hi, I’m @Arijitpanda123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Arijitpanda123/Arijitpanda123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
