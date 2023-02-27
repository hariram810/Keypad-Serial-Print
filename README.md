# Keypad-Serial-Print

![Screenshot (1224)](https://user-images.githubusercontent.com/118633170/221625847-4b953c50-fd90-4927-b8cd-d983faa88bc1.png)


If you have hard-time 3d printing stuff and other materials which i have provided in this project please refer the professionals for the help, [JLCPCB](https://jlcpcb.com/RNA) is one of the best company from shenzhen china they provide, PCB manufacturing, PCBA and 3D printing services to people in need, they provide good quality products in all sectors

[JLCPCB](https://jlcpcb.com/RNA)


Please use the following link to register an account in [JLCPCB](https://jlcpcb.com/RNA)

https://jlcpcb.com/RNA


Pcb Manufacturing

----------

2 layers

4 layers

6 layers

jlcpcb.com/RNA


PCBA Services

[JLCPCB](https://jlcpcb.com/RNA) have 350k+ Components In-stock. You don’t have to worry about parts sourcing, this helps you to save time and hassle, also keeps your costs down.

Moreover, you can pre-order parts and hold the inventory at [JLCPCB](https://jlcpcb.com/RNA), giving you peace-of-mind that you won't run into any last minute part shortages. jlcpcb.com/RNA


3d printing

-------------------

SLA -- MJF --SLM -- FDM -- & SLS. easy order and fast shipping makes [JLCPCB](https://jlcpcb.com/RNA) better companion among other manufactures try out [JLCPCB](https://jlcpcb.com/RNA) 3D Printing servies

[JLCPCB](https://jlcpcb.com/RNA) 3D Printing starts at $1 &Get $54 Coupons for new users

![Screenshot (1226)](https://user-images.githubusercontent.com/118633170/221625896-50259108-cfc5-4a74-9469-1010bb9704bf.png)
![Screenshot (1227)](https://user-images.githubusercontent.com/118633170/221625920-68c48482-ec68-4ffb-8cbf-2324b2a11174.png)


One of the simplest interfaces for an Arduino project is a push button switch. It can easily be 
added by connecting one side of the switch to ground and the other side to one of the Arduino’s 
digital input pins. Hold the input pin HIGH, either by using a resistor or the microcontroller’s 
internal pullup, and that’s all you need. Pressing the button will send the input pin LOW, 
and you can detect this change within your sketch to provide functionality for the push button.

Add a Resistive Keypad
This is a really elegant solution, and it only takes one analog input.

With this arrangement, a group of push buttons are connected to different points within a resistor array, that itself is connected between the reference voltage and ground.

When a push button is activated it causes a voltage to be sent to the analog input. As each push button is on a different leg of the array it will have a unique corresponding voltage. Your sketch can read the value of the A/D converter and use it to determine which button was activated.

This is a good solution for applications that only require a few push buttons, add too many buttons and you run the risk of inaccuracies due to reference voltage fluctuations or resistor tolerances.

But it certainly is a viable choice, and we have used it before in the article about using LCD displays. The LCD display shield has a group of push buttons wired up in this exact fashion.

Add a Matrix Keypad
This is the solution we will look at today. 

A matrix keypad is a group of switches connected in an X-Y, or row-column, matrix arrangement. Pressing a button will connect a row with a column, and we can then scan the array to determine which button was pressed.

By arranging the push buttons in a matrix as opposed to connecting them directly to input pins we can usually reduce the amount of wiring. Commercial matrix keypads are inexpensive and readily available, which simplifies the wiring even more.

This is a great solution, with the following caveats:

You need at least six pushbuttons. Fewer than six defeats the wiring advantages, as six pushbuttons will require a 2 x 3 matrix for a total of five wires. A larger number of keys will increase the advantage of using a matrix.
You don’t require users to press two buttons simultaneously. The keypad solution will only accept one input at a time.
You’ll need to use a software routine to determine which button was pressed, this is in addition to the code you’ll need to write to actually do something once the keypress is received.
You’ll still need a lot of inputs, not as many as discrete switches (providing you stay over five) but more than the resistive keypad or ASCII keyboard solutions. Once you exceed 25 push buttons you’re better off choosing the ASCII Keyboard solution.
In many cases, the matrix keypad still has a lot of advantages. And that’s what we will be using in our experiments today.

![Screenshot (1231)](https://user-images.githubusercontent.com/118633170/221625983-bac1b488-39e8-41c6-8352-61e19a138eb0.png)


Matrix Membrane Keypads
The type of keypad we will be using today is a “Matrix Membrane Keypad”. This is an X-Y matrix of switches created using layers of plastic and conductive surfaces. These devices are inexpensive and can be styled to match your project, reducing the mechanical work of mounting all of those push buttons.

Two extremely common membrane matrix keypads are the 4 x 3 keypad (12 switches) and the 4 x 4 keypad (16 switches). They are laid out in the same fashion as a telephone keypad, which is a common user interface that most people are familiar with.

Although I’ll be using the 4 X 4 matrix keypad in today’s experiments you can easily substitute the 4 x 3 unit with minor wiring and code changes.

Now we need to determine which row the switch is connected to. To do this we will pull all of the column inputs LOW (technically we really only need to keep our detected column LOW, but it is simpler to control them all).

After doing this we begin scanning the rows by raising them HIGH, one-by-one. In the above illustration, we test the top row, which produces no results.

![Screenshot (1229)](https://user-images.githubusercontent.com/118633170/221626009-b81b84b5-4444-48fa-ba72-e4f176014f67.png)
![Screenshot (1230)](https://user-images.githubusercontent.com/118633170/221626016-f7f13fdf-ec8a-4e6e-bb32-e8f64ab84f58.png)


The third row, however, is the correct row. Bringing it HIGH will cause the column output to go HIGH, revealing the location of the switch. 

While the above steps may at first appear complex they actually are not. We will be using a common library to do all of the work for us.

Inexpensive Membrane Matrix Keypads
The keypad we will be using in our experiments is very inexpensive and easily available. It consists of four rows and four columns, each connected to a film ribbon cable.

The film ribbon cables both terminate with an 8-pin female Dupont connector. The pinouts are as follows:

Row 1
Row 2
Row 3
Row 4
Column 1
Column 2
Column 3
Column 4
If you obtain a 4 x 3 keypad you can use it in the experiments, the only difference is that it will have a 7-pin connector and will be missing the Column 4 connection.

Now that you understand how the keypad works let’s see how to use it with an Arduino.

Basic Keypad Test
The first experiment we’ll perform with the keypad is to simply connect it up to the Arduino and use the serial monitor to verify that we can read all of the keys. This is a good way to get to know how to work with the keypad, and can also be used to verify that all of the keys are indeed working.

The easiest way to get everything connected is to use a multi-conductor male-to-male Dupont ribbon cable with 8 conductors. The hookup is quite simple, as the Arduino connections are all made in the same order as they are on the keypad connector.

Once everything is hooked up you can proceed to the sketch that we’ll use to test our keypad.

Keypad Test Sketch
The sketch we’ll be using is simplified by the use of a special library, the Keypad Library by Mark Stanley and Alexander Brevig. With this library using matrix keypads is very easy.

You can install this library directly from your Library Manager. 

Open your Arduino IDE.
Select the Sketch item from the top menu bar.
Navigate to Include Library. A sub-menu will open.
Select Manage Libraries. This will open the Library Manager dialog box.
In the Filter Your Search box type “keypad”.
From the results scroll down until you find the Keypad by Mark Stanley and Alexander Brevig library.
Select Install to install the library
Close the Library Manager dialog box.
Load the sketch and open your serial monitor, making sure to observe the baud rate (it should be 9600 baud). Now press some keys on the keypad. You should observe the key values displayed on the serial monitor.

Keypad with LCD
Our next experiment is just an extension of the first one. This time we will use an LCD display instead of the serial monitor to read keypress values.

Using a display such as an LCD or OLED display with the keypad is a very common application, as it can give you feedback when you are entering data.

Combination Lock
A great use for a matrix keypad is to build a combination lock. You can use this to lock a door or a drawer or to regulate access to an electronic device.

Our lock project will drive a relay, which in turn could be used to activate a standard locking solenoid. These devices stay in the locked position and will only release the lock when voltage is applied to them. Typically these devices use 12-volts to operate.

In most cases you’ll only want to apply voltage for a few seconds, just enough time to unlock the solenoid to open the guarded area. Applying voltage to the solenoid for too long a period can burn it out, you should read the specifications on your locking mechanism for more details.

Our lock will operate as follows:

![Screenshot (1232)](https://user-images.githubusercontent.com/118633170/221626120-4a5983cb-5841-49a9-8569-9385cdc5c52e.png)


The LCD display will prompt the user to enter a password
As the password is entered it will be printed on the display
When the correct number of characters have been entered the code will check the data against the stored combination.
If the code is correct it will activate the relay for five seconds.
If the code is incorrect it will display an error message.
It will then clear the display.


Relay modules typically have three input connections:

Ground
Power (typically 5-volts)
Trigger or Input
The output of the relay is labeled as follows:

NC (normally closed)
Common
NO (normally open)
Typically you would connect one side of your solenoid (or other activated device) to one side of the power supply (i.e. 12-volts). The other side would be routed between the Common and NO connections of the relay. This way the relay will switch the solenoid on when it is activated.

In my experiment I just used a lamp, as it was easier to see in the video!

After wiring it up it’s time to turn our attention to the sketch that will run our combination lock.

![Screenshot (1234)](https://user-images.githubusercontent.com/118633170/221626362-b754b5c5-d5a0-441c-90c8-e9d1e02b60dc.png)


You’ll note that it uses the same libraries as the LCD sketch, which of course makes perfect sense.

We define the length of the password on line 23. Note that this also includes a null character, so the value here is actually one more than the actual password length. You can change this to make an easier or harder password.

Two character variable arrays are defined. The Data array holds the key entries, and the Master arry has the actual password. You should edit the password to be something harder to guess than just the first seven digits on the keypad!

We also define the lock output pin. I used pin 13, as the Arduino has a built-in LED on that pin, so it can be used for troubleshooting if the relay fails to activate. 

The byte_count variable counts the number of keypresses entered.

In the Setup we define pin 13 as an OUTPUT.

We start the Loop by placing the LCD cursor in the top left corner and printing “Enter Password:”. Then we look for a keypress, as we did in the previous sketches.

If we get a keypress we record the value in an element of the Data array. We then increment the counter for the next keypress.

Beneath each key is a membrane switch. Each switch in a row is connected to the other switches in the row by a conductive trace underneath the pad. Each switch in a column is connected the same way – one side of the switch is connected to all of the other switches in that column by a conductive trace. Each row and column is brought out to a single pin, for a total of 8 pins on a 4X4 keypad

![Screenshot (1238)](https://user-images.githubusercontent.com/118633170/221626407-c62f2ca7-42a2-438b-aabb-c70a5d2859d4.png)


Pressing a button closes the switch between a column and a row trace, allowing current to flow between a column pin and a row pin.

The schematic for a 4X4 keypad shows how the rows and columns are connected:



The Arduino detects which button is pressed by detecting the row and column pin that’s connected to the button.

This happens in four steps:

1. First, when no buttons are pressed, all of the column pins are held HIGH, and all of the row pins are held LOW:

![Screenshot (1239)](https://user-images.githubusercontent.com/118633170/221626424-988d1c90-3827-4165-89bb-015155e4285a.png)


2. When a button is pressed, the column pin is pulled LOW since the current from the HIGH column flows to the LOW row pin:

![Screenshot (1240)](https://user-images.githubusercontent.com/118633170/221626460-c47c9cfa-e3e8-4df1-b7a5-6c41e9144d3f.png)

3. The Arduino now knows which column the button is in, so now it just needs to find the row the button is in. It does this by switching each one of the row pins HIGH, and at the same time reading all of the column pins to detect which column pin returns to HIGH:

First, find out which keypad pins are connected to the button rows. Insert the ground (black) wire into the first pin on the left. Press any button in row 1 

and hold it down. Now insert the positive (red) wire into each one of the other pins. If the LED lights up at one of the pins, press and hold another button in row 1, then insert the positive wire 
into each one of the other pins again. If the LED lights up on a different pin, it means the ground wire is inserted into the row 1 pin. If none of the buttons in row 1 make the LED light up, the ground wire is not connected to row 
1. Now move the ground wire over to the next pin, press a button in a different row, and repeat the process above until you’ve found the pin for each row.
