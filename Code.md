# beeeproject
beee FIle and code
created on 01/11/2018
Code:-


const int buttonPin = 11;
const int ledPin = 4;   
int ledState = HIGH;    
int buttonState;        
int lastButtonState = LOW;  
unsigned long lastDebounceTime = 0;
unsigned long debounceDelay = 50;  
void setup() {
  pinMode(buttonPin, INPUT);
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, ledState);
}
void loop() {
  int reading = digitalRead(buttonPin);
  if (reading != lastButtonState) {
  lastDebounceTime = millis();
  }
if ((millis() - lastDebounceTime) > debounceDelay) {
    if (reading != buttonState) {
      buttonState = reading;
      if (buttonState == HIGH) {
        ledState = !ledState;
      }
    }
  }
  digitalWrite(ledPin, ledState);
  lastButtonState = reading;
