# IOT Bootcamp Level-1

## About me
My name is **Abdul Hafeez Galib**. I am studying **CSE** at **College of Engineering Triandrum**. I am here to start my IOT journey.

### Experiment-1 **Hello world Led blinking**
![Circuit](https://user-images.githubusercontent.com/77202232/163368514-92f8737e-8796-467f-9d6e-c4b02b8f1f6a.png)
#### Code
```ino
void setup()
{
  pinMode(8, OUTPUT);
}

void loop()
{
  digitalWrite(8, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(8, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```
### Experiment-2 **Traffic Light**
![Circuit](https://user-images.githubusercontent.com/77202232/163369777-84a8a106-92c1-46fd-ab04-164adca000ed.png)
#### Code
```ino
int redled =10; 
int yellowled =7;
int greenled =4; 

void setup()
{
  pinMode(redled, OUTPUT);
  pinMode(yellowled, OUTPUT);
  pinMode(greenled, OUTPUT); 
}

void loop()
{
  digitalWrite(greenled, HIGH);
  delay(5000);
  digitalWrite(greenled, LOW); 
  
  for(int i=0;i<3;i++){
    delay(500);
    digitalWrite(yellowled, HIGH);
    delay(500);
    digitalWrite(yellowled, LOW);
  } 
  
  delay(500);
  digitalWrite(redled, HIGH);
  delay(5000);
  digitalWrite(redled, LOW);
}
```
### Experiment-3 **LED Chasing Effect**
![Circuit](https://user-images.githubusercontent.com/77202232/163370847-103784b9-5dea-4a8f-8eff-b3f1be54fa5b.png)
#### Code
```ino
int BASE = 13;  

void setup()
{
   for (int i = BASE; i >= 3; i=i-2){
     pinMode(i, OUTPUT);   
   }
}

void loop()
{
   for (int i = BASE; i >= 3; i=i-2){
     digitalWrite(i, LOW);    
     delay(200);        
   }
   for (int i = BASE; i >= 3; i=i-2){
     digitalWrite(i, HIGH);    
     delay(200);        
   }  
}
```
### Experiment-4 **Button Controlled LED**
![Circuit](https://user-images.githubusercontent.com/77202232/163371045-587a7e52-9643-4566-835a-c9f9956ca8ca.png)
#### Code
```ino
int ledpin=12;
int inpin=2;
int val;

void setup()
{
  pinMode(ledpin,OUTPUT);
  pinMode(inpin,INPUT);
}

void loop()
{
  val=digitalRead(inpin);
  if(val==LOW){ 
    digitalWrite(ledpin,LOW);
  }else{ 
    digitalWrite(ledpin,HIGH);
  }
}
```
### Experiment-5 **Buzzer**
![Circuit](https://user-images.githubusercontent.com/77202232/163371367-00641837-4729-4dac-ba8f-ba5845c1c833.png)
#### Code
```ino
int buzzer=8;

void setup()
{ 
  pinMode(buzzer,OUTPUT);
} 

void loop()
{
	digitalWrite(buzzer, HIGH);
}
```
### Experiment-6 **RGB LED**
![Circuit](https://user-images.githubusercontent.com/77202232/163371584-74d9ca80-322e-4588-bbbc-ccd6183f6d7e.png)
#### Code
```ino
int redpin = 11; 
int bluepin =10; 
int greenpin =9;
int val;

void setup()
{
  pinMode(redpin, OUTPUT);
  pinMode(bluepin, OUTPUT);
  pinMode(greenpin, OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  for(val=255; val>0; val--){
     analogWrite(11, val);
     analogWrite(10, 255-val);
     analogWrite(9, 128-val);
     delay(1); 
  }
  for(val=0; val<255; val++){
     analogWrite(11, val);
     analogWrite(10, 255-val);
     analogWrite(9, 128-val);
     delay(1); 
  }
  Serial.println(val, DEC);
}
```
### Experiment-7 **LDR Light Sensor**
![Circuit](https://user-images.githubusercontent.com/77202232/163371830-b82f83ad-3466-4c50-a8d2-abe114535752.png)
#### Code
```ino
int potpin=0;
int ledpin=11;
int val=0;

void setup()
{
  pinMode(ledpin,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  val=analogRead(potpin);
  Serial.println(val);
  analogWrite(ledpin,val/4);
  delay(10);
}
```
### Experiment-8 **Flame Sensor**
![Circuit](https://user-images.githubusercontent.com/77202232/163372026-6a3f770d-e3fa-4cd2-855c-10b9ea58a5fd.png)
#### Code
```ino
int flame=0;
int Beep=9;
int val=0;

void setup()
{
  pinMode(Beep,OUTPUT);
  pinMode(flame,INPUT);
  Serial.begin(9600);
}

void loop()
{ 
  val=analogRead(flame);
  Serial.println(val);
  if(val>=600){  
     digitalWrite(Beep,HIGH); 
  }else{  
     digitalWrite(Beep,LOW); 
  }
  delay(500); 
}
```
### Experiment-9 **TMP36 Temperature Sensor**
![Circuit](https://user-images.githubusercontent.com/77202232/163372529-49b03aaa-7d4b-46b1-b29d-80f6ce1f6d6b.png)
#### Code
```ino
int potPin = 0; 

void setup()
{
	Serial.begin(9600);
}

void loop()
{
  int val;
  int dat;
  val=analogRead(0);
  dat=val/2.048;
  Serial.print("Temp:");
  Serial.print(dat);
  Serial.println(" degree C");
  delay(500);
}
```
### Experiment-10 **IR Remote Control Using TSOP**
![Circuit](https://user-images.githubusercontent.com/77202232/163373369-6d992ad6-0153-4be6-a74f-44a19b334829.png)
#### Code
```ino
#include <IRremote.h>

int RECV_PIN = 11;
int LED1 = 2;
int LED2 = 3;
int LED3 = 4;
int LED4 = 5;
int LED5 = 6;
int LED6 = 7;
long on1  = 0x00FD30CF;
long off1 = 0x00FD28D7;
long on2 = 0x00FDB04F;
long off2 = 0x00FDA857;
long on3 = 0x00FD708F;
long off3 = 0x00FD6897;
long on4 = 0x00FD08F7;
long off4 = 0x00FD18E7;
long on5 = 0x00FD8877;
long off5 = 0x00FD9867;
long on6 = 0x00FD48B7;
long off6 = 0x00FD58A7;
IRrecv irrecv(RECV_PIN);
decode_results results;

void setup()
{
  pinMode(RECV_PIN, INPUT);   
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(LED3, OUTPUT);
  pinMode(LED4, OUTPUT);
  pinMode(LED5, OUTPUT);
  pinMode(LED6, OUTPUT);  
  Serial.begin(9600);
  irrecv.enableIRIn(); 
}

void loop()
{
  if (irrecv.decode(&results)){
    if (results.value == on1)
       digitalWrite(LED1, HIGH);
    if (results.value == off1 )
       digitalWrite(LED1, LOW); 
    if (results.value == on2 )
       digitalWrite(LED2, HIGH);
    if (results.value == off2 )
       digitalWrite(LED2, LOW); 
    if (results.value == on3 )
       digitalWrite(LED3, HIGH);
    if (results.value == off3 )
       digitalWrite(LED3, LOW);
    if (results.value == on4 )
       digitalWrite(LED4, HIGH);
    if (results.value == off4 )
       digitalWrite(LED4, LOW); 
    if (results.value == on5 )
       digitalWrite(LED5, HIGH);
    if (results.value == off5 )
       digitalWrite(LED5, LOW); 
    if (results.value == on6 )
       digitalWrite(LED6, HIGH);
    if (results.value == off6 )
       digitalWrite(LED6, LOW);           
    irrecv.resume(); 
  }
}
```
### Experiment-11 **Potentiometer analog Value Reading**
![Circuit](https://user-images.githubusercontent.com/77202232/163374759-5b592303-8a77-48db-9c81-6d10e77dec04.png)
#### Code
```ino
int potpin=0;
int ledpin=13;
int val=0;

void setup()
{
  pinMode(ledpin,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  digitalWrite(ledpin,HIGH);
  delay(50);
  digitalWrite(ledpin,LOW);
  delay(50);
  val=analogRead(potpin);
  Serial.println(val);
}
```
### Experiment-12 **7 Segment Display**
![Circuit](https://user-images.githubusercontent.com/77202232/163376234-ebd7a634-2cd5-4b70-bf3c-749a8913e9fb.png)
#### Code
```ino
int a=7;
int b=6;
int c=5;
int d=10;
int e=11;
int f=8;
int g=9;
int dp=4;

void digital_0(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e,HIGH);
  digitalWrite(f,HIGH);
  digitalWrite(g,LOW);
  digitalWrite(dp,LOW);
}

void digital_1(void) 
{
  unsigned char j;
  digitalWrite(c,HIGH);
  digitalWrite(b,HIGH);
  for(j=7;j<=11;j++)
  	digitalWrite(j,LOW);
  digitalWrite(dp,LOW);
}

void digital_2(void) 
{
  unsigned char j;
  digitalWrite(b,HIGH);
  digitalWrite(a,HIGH);
  for(j=9;j<=11;j++)
      digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(c,LOW);
  digitalWrite(f,LOW);
}

void digital_3(void) 
{
  digitalWrite(g,HIGH);
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(f,LOW);
  digitalWrite(e,LOW);
}

void digital_4(void)
{
  digitalWrite(c,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(a,LOW);
  digitalWrite(e,LOW);
  digitalWrite(d,LOW);
}

void digital_5(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b, LOW);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e, LOW);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
}

void digital_6(void) 
{
  unsigned char j;
  for(j=7;j<=11;j++)
  	digitalWrite(j,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(b,LOW);
}

void digital_7(void) 
{
  unsigned char j;
  for(j=5;j<=7;j++)
  	digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
  for(j=8;j<=11;j++)
  digitalWrite(j,LOW);
}

void digital_8(void) 
{
  unsigned char j;
  for(j=5;j<=11;j++)
      digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
}

void digital_9(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e, LOW);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
}

void setup()
{
  int i;
  for(i=4;i<=11;i++)
  	pinMode(i,OUTPUT);
}

void loop()
{
  while(1){
    digital_0();
    delay(1000);
    digital_1();
    delay(1000);
    digital_2();
    delay(1000); 
    digital_3();
    delay(1000); 
    digital_4();
    delay(1000); 
    digital_5();
    delay(1000); 
    digital_6();
    delay(1000);
    digital_7();
    delay(1000);
    digital_8();
    delay(1000); 
    digital_9();
    delay(1000); 
  }
}
```
### Assignment-1.1 **Automatic Night Lamp**
![Circuit](https://user-images.githubusercontent.com/77202232/163376767-5e78df43-1b1f-4885-a1ea-b6d5ada28c29.png)
#### Code
```ino
int potpin=0;
int ledpin=11;
int val=0;

void setup()
{
  pinMode(ledpin,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  val=analogRead(potpin);
  Serial.println(val);
  analogWrite(ledpin,974-val);
}
```
### Assignment-1.2 **Thermometer**
![Circuit](https://user-images.githubusercontent.com/77202232/163377099-9d63372f-6f44-4f55-a579-70fff6ea4f6e.png)
#### Code
```ino
int val; 

void setup()
{
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(A0, INPUT);
  Serial.begin(9600);
}

void loop()
{
  val = analogRead(A0);
  Serial.println(val);
  if(val>=76){
    digitalWrite(12, HIGH);
  }
  if(val>=132){
    digitalWrite(11, HIGH);
  }
  if(val>=188){
    digitalWrite(10, HIGH);
  }
  if(val>=244){
    digitalWrite(9, HIGH);
  }
  if(val>=300){
    digitalWrite(8, HIGH);
  }
  if(val>=350){
    digitalWrite(7, HIGH);
  }
  if(val>=300 && val<350){
  	digitalWrite(7, LOW);
  }
  if(val>=244 && val<300){
  	digitalWrite(8, LOW);
  }
  if(val>=188 && val<244){
  	digitalWrite(9, LOW);
  }
  if(val>=132 && val<188){
  	digitalWrite(10, LOW);
  }
  if(val>=76 && val<132){
  	digitalWrite(11, LOW);
  }
  if(val<76){
  	digitalWrite(12, LOW);
  }
}
```
### Assignment-2.1 **Digital Dice using 6 LED and Push Button**
![Circuit](https://user-images.githubusercontent.com/77202232/163377260-425d5253-7232-41ae-bb5d-b50e1a1789a0.png)
#### Code
```ino
void setup()
{
  pinMode(2, INPUT);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(13, OUTPUT);
  randomSeed(analogRead(0));
  Serial.begin(9600);
}

void loop()
{
  int var = digitalRead(2);
  if(var == 1){
  	int val = random(1,7);
    digitalWrite(13, HIGH);
    if(val>=2){
      digitalWrite(12, HIGH);
    }
    if(val>=3){
      digitalWrite(11, HIGH);
    }
    if(val>=4){
      digitalWrite(10, HIGH);
    }
    if(val>=5){
      digitalWrite(9, HIGH);
    }
    if(val>=6){
      digitalWrite(8, HIGH);
    }
  	Serial.println(val);
  }else{
  	for(int i=13; i>=8; i--){
  		digitalWrite(i, LOW);
  	}
  } 
  delay(2000);
}
```
### Assignment-2.2 **Digital Dice using 7 Segment Display and Push Button**
![Circuit](https://user-images.githubusercontent.com/77202232/163377490-85c29f6b-987e-4a76-a94d-f1fa75cd5cb4.png)
#### Code
```ino
int a=7;
int b=6;
int c=5;
int d=10;
int e=11;
int f=8;
int g=9;
int dp=4;

void digital_0(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e,HIGH);
  digitalWrite(f,HIGH);
  digitalWrite(g,LOW);
  digitalWrite(dp,LOW);
}

void digital_1(void) 
{
  unsigned char j;
  digitalWrite(c,HIGH);
  digitalWrite(b,HIGH);
  for(j=7;j<=11;j++)
  	digitalWrite(j,LOW);
  digitalWrite(dp,LOW);
}

void digital_2(void) 
{
  unsigned char j;
  digitalWrite(b,HIGH);
  digitalWrite(a,HIGH);
  for(j=9;j<=11;j++)
      digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(c,LOW);
  digitalWrite(f,LOW);
}

void digital_3(void) 
{
  digitalWrite(g,HIGH);
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(f,LOW);
  digitalWrite(e,LOW);
}

void digital_4(void)
{
  digitalWrite(c,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(a,LOW);
  digitalWrite(e,LOW);
  digitalWrite(d,LOW);
}

void digital_5(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b, LOW);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e, LOW);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
}

void digital_6(void) 
{
  unsigned char j;
  for(j=7;j<=11;j++)
  	digitalWrite(j,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(dp,LOW);
  digitalWrite(b,LOW);
}

void digital_7(void) 
{
  unsigned char j;
  for(j=5;j<=7;j++)
  	digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
  for(j=8;j<=11;j++)
  digitalWrite(j,LOW);
}

void digital_8(void) 
{
  unsigned char j;
  for(j=5;j<=11;j++)
      digitalWrite(j,HIGH);
  digitalWrite(dp,LOW);
}

void digital_9(void) 
{
  unsigned char j;
  digitalWrite(a,HIGH);
  digitalWrite(b,HIGH);
  digitalWrite(c,HIGH);
  digitalWrite(d,HIGH);
  digitalWrite(e, LOW);
  digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  digitalWrite(dp,LOW);
}

void setup()
{
  int i;
  pinMode(2, INPUT);
  for(i=4;i<=11;i++)
  	pinMode(i,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  int var = digitalRead(2);
  if(var == 1){
  	int val = random(1,7);
    if(val==1){
      digital_1();
    }else if(val==2){
      digital_2();
    }else if(val==3){
      digital_3();
    }else if(val==4){
      digital_4();
    }else if(val==5){
      digital_5();
    }else if(val==6){
      digital_6();
    }
  	Serial.println(val);
  }
  delay(2000);
}
```
Really enjoyed working with these projects. :smiley: 
