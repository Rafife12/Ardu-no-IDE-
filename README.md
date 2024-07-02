 Importação de Biblioteca e Inicialização de LCD
 cpp #include <LiquidCrystal.h> 
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
 cpp const int tSens = A5; 
const int tSet = A0; 
const int Cald = 8; 
unsigned int tSensVal = 0; 
unsigned int tSetVal = 0; 
boolean statoCald = 0; 
Função setup()
 cpp void setup() { lcd.begin(16, 2); 
pinMode(Cald, OUTPUT); 
 Serial.begin(9600); 
lcd.print("T. Impos.:"); 
lcd.setCursor(0, 1); 
 lcd.print("T. Amb.:"); 
}
 Função loop()
 cpp void loop() { delay(200); 
tSetVal = analogRead(tSet); 
 tSetVal = map(tSetVal, 0, 1023, 0, 50);
 tSensVal = analogRead(tSens); 
 tSensVal = map(tSensVal, 0, 1023, 0, 110); 
if (tSensVal > tSetVal + 1) 
statoCald = LOW; 
else if (tSensVal < tSetVal - 1)  
statoCald = HIGH; 
digitalWrite(Cald, statoCald); 
Serial.print("T ambiente = ");
 Serial.println(tSensVal);
 serial Serial.print("T set = ");
 Serial.println(tSetVal); 
 serial Serial.print("Caldaia = ");
 Serial.println(statoCald);
 lcd.clear(); // limpa o display LCD 
lcd.setCursor(10, 0); 
lcd.print(tSetVal); 
 lcd.setCursor(8, 1); 
lcd.print(tSensVal);  
lcd.setCursor(13, 0); lcd.print("C"); 
 lcd.setCursor(11, 1); 
lcd.print("C"); 
lcd.setCursor(0, 0); 
lcd.print("T. Impos.:"); 
lcd.setCursor(0, 1); 
lcd.print("T. Amb.:");
 delay(5000);  }
