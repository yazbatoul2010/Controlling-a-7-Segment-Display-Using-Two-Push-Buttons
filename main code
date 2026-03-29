const int pbSelect = 2;
const int pbStart = 3;
const int ledPin = 4;
// 7-segment pins (a to g)
int segPins[7] = {7, 8, 9, 10, 11, 12, 13};
// Numbers 0–9 for Common Cathode
byte numbers[10][7] = {
{1,1,1,1,1,1,0}, // 0
{0,1,1,0,0,0,0}, // 1
{1,1,0,1,1,0,1}, // 2
{1,1,1,1,0,0,1}, // 3
{0,1,1,0,0,1,1}, // 4
{1,0,1,1,0,1,1}, // 5
{1,0,1,1,1,1,1}, // 6
{1,1,1,0,0,0,0}, // 7
{1,1,1,1,1,1,1}, // 8
{1,1,1,1,0,1,1} // 9
};
int currentNumber = 0;
void setup() { 
  pinMode(pbSelect, INPUT_PULLUP);
  pinMode(pbStart, INPUT_PULLUP);
  pinMode(ledPin, OUTPUT); 
  for (int i = 0; i < 7; i++) 
{ 
 pinMode(segPins[i], OUTPUT); 
} 
displayNumber(currentNumber); 
}
void loop()
{
// Button 1: Select number
if (digitalRead(pbSelect) == LOW)
{
delay(200); // debounce
currentNumber++;
if (currentNumber > 9) currentNumber = 0;
digitalWrite(ledPin, LOW); // Turn off LED when selecting a new number
displayNumber(currentNumber);
}
// Button 2: Start countdown
if (digitalRead(pbStart) == LOW && currentNumber >0)
{
delay(200);
countdown();
}
}
void countdown()
{
for (int i = currentNumber; i >= 0; i--)
{
displayNumber(i);
delay(1000);
}
digitalWrite(ledPin, HIGH); // Turn ON LED when countdown ends
}
// Display a number on the 7-segment
void displayNumber(int num)
{
for (int i = 0; i < 7; i++)
{
digitalWrite(segPins[i], numbers[num][i]);
}
}
