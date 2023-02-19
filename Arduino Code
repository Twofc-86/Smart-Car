#define ECHOpin 5
#define TRIGpin 3
#define RELAY_PIN1 9
#define RELAY_PIN2 10
#define RIGHT_SENSOR 6
#define LEFT_SENSOR 11
 
long duration; int distance;

void setup(){ pinMode(TRIGpin, OUTPUT); pinMode(ECHOpin, INPUT);
pinMode(RELAY_PIN1, OUTPUT); pinMode(RELAY_PIN2, OUTPUT); pinMode(RIGHT_SENSOR,INPUT); pinMode(LEFT_SENSOR,INPUT);
digitalWrite(RELAY_PIN2, HIGH); digitalWrite(RELAY_PIN1, HIGH); Serial.begin(9600); Serial.println("Running...");
}

void loop(){
int right = digitalRead(RIGHT_SENSOR); int left = digitalRead(LEFT_SENSOR); digitalWrite(TRIGpin, LOW); delayMicroseconds(4); digitalWrite(TRIGpin, HIGH); delayMicroseconds(15); digitalWrite(TRIGpin, LOW);
duration = pulseIn(ECHOpin, HIGH); distance = duration*(0.034/2); Serial.print("Distance: "); Serial.print(distance);
Serial.println(" cm"); if(distance <= 30) { stoped();
} else {
Serial.print("Right: "); Serial.println(right); Serial.print("Left: "); Serial.println(left); BotMakeMove(right, left);
}
}
 
void BotMakeMove(int right, int left) {
//If none of the sensors detects black line, then go straight if (right == 0 && left == 0){
Serial.println("Bot move: Forward"); go_forward();
}
//If right sensor detects black line, then turn right else if (right == 1 && left == 0){
Serial.println("Bot move: Right"); go_right();
delay(500);
}
//If left sensor detects black line, then turn left else if (right == 0 && left == 1){
Serial.println("Bot move: Left"); go_left();
delay(500);
}
//If both the sensors detect black line, then stop else {
Serial.println("Bot move: Stop"); stoped();
}
}
void go_forward() { digitalWrite(RELAY_PIN1, LOW); digitalWrite(RELAY_PIN2, LOW);
}

void go_left() { digitalWrite(RELAY_PIN1, HIGH); digitalWrite(RELAY_PIN2, LOW);
}

void go_right() { digitalWrite(RELAY_PIN1, LOW); digitalWrite(RELAY_PIN2, HIGH);
}

void stoped() {
 
digitalWrite(RELAY_PIN1, HIGH); digitalWrite(RELAY_PIN2, HIGH);
}
