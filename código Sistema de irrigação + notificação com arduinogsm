//Trabalho didático: Sistema de irrigação + notificação com arduinogsm


int valvula = 8; // sinal do rele para válvula

void setup() {
  pinMode(valvula, OUTPUT); // declara válvula como saída
}

void loop() {

 // Leitura do sensor no pino A0 e armazenamento em SensorValue

 int sensorValue = analogRead(A0);

 // verifica se valor de leitura está acima de 600 (umido abaixo de 600  e seco até 1023)

 if (sensorValue > 600){
   // se sim, libera água por 1s
   digitalWrite(valvula,LOW);
   delay(1000);
   digitalWrite(valvula,HIGH); // desliga válvula
 }

 else{
 // se não, interrompe a passagem de água
   digitalWrite(valvula,HIGH);
   delay(1000);
  }
  delay(3000); // Aguarda 3s para verificar se solo está umido novamente
}


***********************************************************************************************************
***********************************************************************************************************

//Programa : Envio SMS com o GSM Shield

 
#include "SIM900.h"
#include <SoftwareSerial.h>
//Carrega a biblioteca SMS
#include "sms.h"
 
SMSGSM sms;
 
int numdata;
boolean started=false;
char smsbuffer[160];
char n[20];
 
void setup()
{
     //Inicializa a serial 
     Serial.begin(9600);
     Serial.println("Testando GSM shield...");
     //Inicia a configuracao do Shield
     if (gsm.begin(2400)) 
     {
       Serial.println("nstatus=READY");
       started=true;
     } 
     else Serial.println("nstatus=IDLE");
 
     if(started) 
     {
       //Envia um SMS para o numero selecionado
       //Formato sms.SendSMS(<numero>,<mensagem>)
       if (sms.SendSMS("912345678", "Arduino SMS"))
       Serial.println("nSMS sent OK");
     }
}
 
void loop()
{
     if(started) 
     {
       //Aguarda SMS e mostra o texto no serial monitor
       if(gsm.readSMS(smsbuffer, 160, n, 20)) 
       {
          Serial.println(n);
          Serial.println(smsbuffer);
          delay(5000);
       }
       delay(1000);
     }
}
