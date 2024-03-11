// DC-Motor-with-Potentiometer
//DC Motor Control with Potentiometer


#define VCC2 26 // define pin 5 or any other digial pin here as VCC2
#define GND2 33 // define pin 2 or any other digital pin as Ground 2

void setup(){
 ledcSetup(0,1000,8);
 ledcAttachPin(0,0);
 pinMode(23, OUTPUT);
 pinMode(19, OUTPUT);
 
 pinMode(VCC2,OUTPUT);//define a digital pin as output
 digitalWrite(VCC2, HIGH);// set the above pin as HIGH so it acts as 5V

 pinMode(GND2,OUTPUT);//define a digital pin as output
 digitalWrite(GND2, LOW);// set the above pin as LOW so it acts as Ground 
}
void loop(){
 int p = analogRead(35);
 p = map(p,0,4095,0,511);
 if(p==256){
 digitalWrite(19, 0); digitalWrite(23, 0); delay(2000);
 }
 else if(p<256){
 digitalWrite(19, 1); digitalWrite(23, 0);
 ledcWrite(0, 256-p);
 }
 else if(p>256){
 digitalWrite(19, 0); digitalWrite(23, 1);
 ledcWrite(0,p-256);
 }
}
