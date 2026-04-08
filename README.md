# Question-1---Blinking-LED-with-different-time-interval
This project demonstrates how to control multiple LEDs using Arduino microcontroller by making them blink at different time intervals simultaneously. It's helpful in understanding the basic concepts like digital output, controlling time using delay() function, and independent LED behaviour.

-> Objective :
1. To control the LEDs independently
2. To implement the different blinking speeds
3. To understand the timing using delay() function.

-> Tinkercad simulation link : https://www.tinkercad.com/things/lpBnoFouUTp-blinking-led-with-different-time-interval/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=zu69S4tF2mmjnVALH9FqWkXYbU-mQD-0QeWoOu9r1Rk

-> Components used :
1. Arduino Uno
2. 3 LEDs of different colours(to vissibly show the difference in blinking time intervals)
3. 3 Resistors(each 220 Ohm)
4. Breadboard
5. Jumper wires

-> Circuit connection :
LED 1 connected to Pin 12
LED 2 connected to Pin 10
LED 3 connected to Pin 4
All LEDs are connected to ground(GND) through resistors

-> Working :
Each LED is assigned a different delay :
LED 1 - fast blinking
LED 2 - medium blinking
LED 3 - slow blinking
The Arduino switches LEDs ON amd OFF using digitalWrite() and controls the speed using delay()

-> Output :
All three LEDs blink simultaneously at different speeds, creating unique pattern.

-> Code : [Blinking_LED_with_different_time_interval.c](https://github.com/user-attachments/files/26573504/Blinking_LED_with_different_time_interval.c)

//Blinking LEDs with different time interval
//C code
// declaring the LEDs
int led_1 = 12;
int led_2 = 10;
int led_3 = 4;

unsigned long time_led_1 = 0;
//this represents the last time LED 1 blinked

unsigned long time_led_2 = 0;
//this represents the last time LED 2 blinked

unsigned long time_led_3 = 0;
//this represents the last time LED 3 blinked

void setup(){
  pinMode(led_1, OUTPUT);
  pinMode(led_2, OUTPUT);
  pinMode(led_3, OUTPUT);
}

void loop(){
  unsigned long now = millis();
  //millis() function gives the current time.
  //here "now" variable stores the current time.
  
  if(now - time_led_1 >= 500){
    time_led_1 = now;
    digitalWrite(led_1, !digitalRead(led_1));

    /*since LED 1 has to blink after 500 milli seconds,
    if the time difference between current time and 
    the last time it blinked is 500 milli seconds, the if loop
    runs. After each execution we update the time at which LED 1
    blinked for the last. digitalRead function reads the state of 
    LED and Not operator reverses the state so that it says 
    whether to give the voltage or stop the voltage. digitalWrite 
    function gives output to the pin.*/
  }
    
    if(now - time_led_2 >= 1000){
      time_led_2 = now;

      digitalWrite(led_2, !digitalRead(led_2));
      /*since LED 2 has to blink after 1000 milli seconds,
    if the time difference between current time and 
    the last time it blinked is 1000 milli seconds, the if loop
    runs. After each execution we update the time at which LED 2
    blinked for the last.*/
    }
      
      if(now - time_led_3 >= 1500){
        time_led_3 = now;
        digitalWrite(led_3, !digitalRead(led_3));

        /*since LED 3 has to blink after 1500 milli seconds,
    if the time difference between current time and 
    the last time it blinked is 1500 milli seconds, the if loop
    runs. After each execution we update the time at which LED 3
    blinked for the last.*/
      }
}

-> Brief explanation of code : 
  The program controls the LEDs connected to different individual digital pins of Arduino. Each LED is made as an output using pinMode() function.
  In the loop function, eacg LED is turned ON and OFF using digtalWrite() function. Different delay values causes each LED to blink at different speed.
  The delay() function decides how long the LED stays ON or OFF, controling the blinking interval.
  All 3 LEDs blink independently with different time intervals.
