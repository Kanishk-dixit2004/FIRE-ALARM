#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

#define MQ2_PIN A0
#define FLAME_PIN 8
#define BUZZER_PIN 9

int gasThreshold = 350;

void setup() {
  Serial.begin(9600);
  lcd.init();
  lcd.backlight();

  pinMode(MQ2_PIN, INPUT);
  pinMode(FLAME_PIN, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);

  lcd.setCursor(0, 0);
  lcd.print(" Smart Safety ");
  lcd.setCursor(0, 1);
  lcd.print("   System     ");
  delay(2000);
  lcd.clear();
}

void loop() {

  int gas = analogRead(MQ2_PIN);
  int flameRaw = digitalRead(FLAME_PIN);

  bool fireDetected = (flameRaw == LOW);  // LOW = fire

  // --------------------
  // LCD GAS DISPLAY
  // --------------------
  lcd.setCursor(0, 0);
  lcd.print("Gas:");
  lcd.print(gas);
  lcd.print("   ");

  // --------------------
  // FIRE ALERT ONLY
  // --------------------
  if (fireDetected) {
    lcd.setCursor(0, 1);
    lcd.print("FIRE ALERT !!! ");

    // Fire buzzer sound
    tone(BUZZER_PIN, 2000);
    delay(200);
    noTone(BUZZER_PIN);
    delay(200);
  }

  // --------------------
  // GAS ALERT (NO BUZZER)
  // --------------------
  else if (gas > gasThreshold) {
    lcd.setCursor(0, 1);
    lcd.print("Gas Leak Risk! ");
    noTone(BUZZER_PIN);  // buzzer OFF always
  }

  // --------------------
  // SAFE CONDITION
  // --------------------
  else {
    lcd.setCursor(0, 1);
    lcd.print("All Safe       ");
    noTone(BUZZER_PIN);
  }

  delay(100);
}
