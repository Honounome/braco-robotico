**Projeto Arduino: Braço Robótico**

-----------------------------

**O Braço Robótico implementado utilizando Arduino**

O projeto visa implementar um braço robótico de MDF controlado por dois joysticks.

Componentes do projeto:

 -  1 x Arduino Uno;
 -  1 x Sensor Shield V5.0;
 -  4 x Micro Servos 9g;
 -  2 x Módulos de Analógicos Ky023;
 -  Jumpers;
 -  Braço de MDF;

-----------------------------

**Projeto Montado**
![Projeto Montado](Imagens/1.jpg)

**Conexões no SensorShield V5.0**
![Projeto Montado](Imagens/close.jpg)

-----------------------------

O código a seguir é responsável por estabelecer a comunicação entre os Joysticks e os Servos que movimentam o braço robótico. Isto é feito por intermédio do Arduino Uno e do SensorShield:

    #include <Servo.h> 

    #define LEFT_X A0
    #define LEFT_Y A1
    
    #define RIGHT_X A3
    #define RIGHT_Y A4
    
    #define PIN_ALTURA 5
    #define PIN_FRENTE 3
    #define PIN_GARRA 10
    #define PIN_BASE 11
    
    Servo servo_base, servo_garra, servo_frente, servo_altura;   
     
    void setup() {
      Serial.begin(9600); 
    
      servo_altura.attach(PIN_ALTURA, 1, 180); 
      servo_frente.attach(PIN_FRENTE, 1, 180); 
      servo_garra.attach(PIN_GARRA, 1, 180);
      servo_base.attach(PIN_BASE, 1, 180); 
    }
     
    void loop() {
      int left_x; 
      int left_y; 
      int right_x; 
      int right_y; 
      
      left_x = analogRead(LEFT_X); 
      left_x = map(left_x, 0, 1023, 1, 180); 
      servo_altura.write(left_x); 
    
      left_y = analogRead(LEFT_Y); 
      left_y = map(left_y, 0, 1023, 1, 180); 
      servo_frente.write(left_y); 
      
      right_x = analogRead(RIGHT_X); 
      right_x = map(right_x, 0, 1023, 1, 180); 
      servo_garra.write(right_x); 
      
      right_y = analogRead(RIGHT_Y); 
      right_y = map(right_y, 0, 1023, 1, 180); 
      servo_base.write(right_y); 
      
      delay(100);
    }

--------------------------------

**Link para o vídeo explicativo do funcionamento do projeto:**

[Vídeo do Projeto](https://youtu.be/kIQm7T29txI)
