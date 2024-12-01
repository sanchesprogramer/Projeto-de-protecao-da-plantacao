# Projeto-IOT
Projeto IOT

Felipe de Almeida Parreira 10400771
Raphael Dias Sanches 10403418
Gabriel William Ribeiro Pauleti 10400878
Gustavo Augusto Pivatto 10401400

O nosso projeto consistirá no desenvolvimento de uma aplicação inovadora que visa otimizar tanto a irrigação quanto a proteção das plantações, fazendo uso da tecnologia de Internet das Coisas (IoT). Através dessa plataforma, pretendemos proporcionar melhorias significativas no manejo agrícola, garantindo um uso mais eficiente dos recursos hídricos e uma proteção mais eficaz das culturas, contribuindo assim para o aumento da produtividade e sustentabilidade no setor agrícola.

**Segue abaixo o PDF do nosso artigo:** [Melhorias.na.irrigacao.e.protecao.da.plantacao.utilizando.IOTV2.pdf](https://github.com/felipih/Projeto-IOT/files/15476665/Melhorias.na.irrigacao.e.protecao.da.plantacao.utilizando.IOTV2.pdf)


**Fotos do projeto:**

**Nodered:**
![image](https://github.com/felipih/Projeto-IOT/assets/111011642/9cb781e8-cf46-4660-a033-247be0cf870a)

**Servo motor:**

![image](https://github.com/felipih/Projeto-IOT/assets/111011642/4809aa43-09af-4159-968d-37d2c6c52fe3)

**Sensor de umidade do solo:**

![image](https://github.com/felipih/Projeto-IOT/assets/111011642/d4551904-8633-4550-acd7-97f16d5dfe7e)

**Sensor de umidade do ar:**

![image](https://github.com/felipih/Projeto-IOT/assets/111011642/0e498cd1-4bff-45c1-9f7c-a21c1937780d)


**Códigos do projeto:**

**Nodered:**
[
    {
        "id": "3fbf49387eea644f",
        "type": "tab",
        "label": "Flow 1",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "88f931d30ae8c7e5",
        "type": "inject",
        "z": "3fbf49387eea644f",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "30",
        "crontab": "",
        "once": false,
        "onceDelay": "1",
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 160,
        "y": 420,
        "wires": [
            [
                "ce59a7c80b0e9140"
            ]
        ]
    },
    {
        "id": "60bf62feb5e0a035",
        "type": "debug",
        "z": "3fbf49387eea644f",
        "name": "debug 1",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 2000,
        "y": 420,
        "wires": []
    },
    {
        "id": "ce59a7c80b0e9140",
        "type": "http request",
        "z": "3fbf49387eea644f",
        "name": "",
        "method": "GET",
        "ret": "obj",
        "paytoqs": "ignore",
        "url": "https://api.openweathermap.org/data/2.5/weather?lat=-23.533773&lon=-46.625290&appid=6680555ffe4a89915940ac57966a028e",
        "tls": "",
        "persist": false,
        "proxy": "",
        "insecureHTTPParser": false,
        "authType": "",
        "senderr": false,
        "headers": [],
        "x": 360,
        "y": 420,
        "wires": [
            [
                "abfe0b93fd3852e9"
            ]
        ]
    },
    {
        "id": "abfe0b93fd3852e9",
        "type": "change",
        "z": "3fbf49387eea644f",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.wind.speed",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 560,
        "y": 420,
        "wires": [
            [
                "e524f1df96780796"
            ]
        ]
    },
    {
        "id": "43fd7fb4e9311c2f",
        "type": "function",
        "z": "3fbf49387eea644f",
        "name": "function 1",
        "func": "var mensagem1 = msg.payload[0]; \nvar mensagem2 = msg.payload[1]; \nvar mensagem3 = msg.payload[2]; \nmsg.payload = \"A velocidade atual do vento é: \" + mensagem2 + \" Km/h, a umidade do solo é: \" + mensagem1 + \"%, a Umidade do ar é: \" + mensagem3 + \"%\";\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1640,
        "y": 420,
        "wires": [
            [
                "f32ced5c882bce93"
            ]
        ]
    },
    {
        "id": "ec80016fbae55717",
        "type": "mqtt in",
        "z": "3fbf49387eea644f",
        "name": "Umidade Solo",
        "topic": "RaphaelDS_10403418/Umidade",
        "qos": "2",
        "datatype": "auto-detect",
        "broker": "a5ad4478e939728f",
        "nl": false,
        "rap": true,
        "rh": 0,
        "inputs": 0,
        "x": 570,
        "y": 320,
        "wires": [
            [
                "5a3d55ceb62de181"
            ]
        ]
    },
    {
        "id": "0da113930da1ce04",
        "type": "mqtt in",
        "z": "3fbf49387eea644f",
        "name": "Umidade Ar",
        "topic": "RalphiteDS_10403418/Umidade",
        "qos": "2",
        "datatype": "auto-detect",
        "broker": "a5ad4478e939728f",
        "nl": false,
        "rap": true,
        "rh": 0,
        "inputs": 0,
        "x": 570,
        "y": 520,
        "wires": [
            [
                "af36ca0ca1952c76"
            ]
        ]
    },
    {
        "id": "b5ab82390e1b76f9",
        "type": "influxdb out",
        "z": "3fbf49387eea644f",
        "influxdb": "bfb5b8374a6bb772",
        "name": "Infuxdb",
        "measurement": "Umidade_Solo",
        "precision": "",
        "retentionPolicy": "",
        "database": "database",
        "precisionV18FluxV20": "s",
        "retentionPolicyV18Flux": "",
        "org": "b27cda99acb53f09",
        "bucket": "42fce197404a606d",
        "x": 760,
        "y": 380,
        "wires": []
    },
    {
        "id": "79e6ecfea17bab5b",
        "type": "influxdb out",
        "z": "3fbf49387eea644f",
        "influxdb": "bfb5b8374a6bb772",
        "name": "Infuxdb",
        "measurement": "Umidade_Ar",
        "precision": "",
        "retentionPolicy": "",
        "database": "database",
        "precisionV18FluxV20": "s",
        "retentionPolicyV18Flux": "",
        "org": "b27cda99acb53f09",
        "bucket": "42fce197404a606d",
        "x": 760,
        "y": 580,
        "wires": []
    },
    {
        "id": "436c4c119fcfe5fd",
        "type": "influxdb out",
        "z": "3fbf49387eea644f",
        "influxdb": "bfb5b8374a6bb772",
        "name": "Infuxdb",
        "measurement": "Velocidade_Ar",
        "precision": "",
        "retentionPolicy": "",
        "database": "database",
        "precisionV18FluxV20": "s",
        "retentionPolicyV18Flux": "",
        "org": "b27cda99acb53f09",
        "bucket": "42fce197404a606d",
        "x": 760,
        "y": 480,
        "wires": []
    },
    {
        "id": "5a3d55ceb62de181",
        "type": "function",
        "z": "3fbf49387eea644f",
        "name": "function 3",
        "func": "msg.payload = parseFloat(msg.payload);\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 760,
        "y": 320,
        "wires": [
            [
                "b5ab82390e1b76f9",
                "2cd445fff0827773"
            ]
        ]
    },
    {
        "id": "af36ca0ca1952c76",
        "type": "function",
        "z": "3fbf49387eea644f",
        "name": "function 4",
        "func": "msg.payload = parseFloat(msg.payload);\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 760,
        "y": 520,
        "wires": [
            [
                "79e6ecfea17bab5b",
                "b838a8bb722c2824"
            ]
        ]
    },
    {
        "id": "e524f1df96780796",
        "type": "function",
        "z": "3fbf49387eea644f",
        "name": "function 5",
        "func": "msg.payload = parseFloat(msg.payload) * 3.6;\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 760,
        "y": 420,
        "wires": [
            [
                "436c4c119fcfe5fd",
                "ba362330d03d8b78"
            ]
        ]
    },
    {
        "id": "2cd445fff0827773",
        "type": "change",
        "z": "3fbf49387eea644f",
        "name": "parts.index = 0",
        "rules": [
            {
                "t": "set",
                "p": "parts.index",
                "pt": "msg",
                "to": "0",
                "tot": "num"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 940,
        "y": 320,
        "wires": [
            [
                "5bed4176d9e302d9"
            ]
        ]
    },
    {
        "id": "ba362330d03d8b78",
        "type": "change",
        "z": "3fbf49387eea644f",
        "name": "parts.index = 1",
        "rules": [
            {
                "t": "set",
                "p": "parts.index",
                "pt": "msg",
                "to": "1",
                "tot": "num"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 940,
        "y": 420,
        "wires": [
            [
                "5bed4176d9e302d9"
            ]
        ]
    },
    {
        "id": "b838a8bb722c2824",
        "type": "change",
        "z": "3fbf49387eea644f",
        "name": "parts.index = 2",
        "rules": [
            {
                "t": "set",
                "p": "parts.index",
                "pt": "msg",
                "to": "2",
                "tot": "num"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 940,
        "y": 520,
        "wires": [
            [
                "5bed4176d9e302d9"
            ]
        ]
    },
    {
        "id": "5bed4176d9e302d9",
        "type": "change",
        "z": "3fbf49387eea644f",
        "name": "group id and count",
        "rules": [
            {
                "t": "set",
                "p": "parts.id",
                "pt": "msg",
                "to": "mygroup",
                "tot": "str"
            },
            {
                "t": "set",
                "p": "parts.count",
                "pt": "msg",
                "to": "3",
                "tot": "num"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1230,
        "y": 420,
        "wires": [
            [
                "ab15022db8820c61"
            ]
        ]
    },
    {
        "id": "ab15022db8820c61",
        "type": "join",
        "z": "3fbf49387eea644f",
        "name": "",
        "mode": "auto",
        "build": "string",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "\\n",
        "joinerType": "str",
        "accumulate": false,
        "timeout": "",
        "count": "",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "",
        "reduceFixup": "",
        "x": 1430,
        "y": 420,
        "wires": [
            [
                "43fd7fb4e9311c2f",
                "f31ee714dcdd840c"
            ]
        ]
    },
    {
        "id": "389e45b9d175b7b3",
        "type": "mqtt out",
        "z": "3fbf49387eea644f",
        "name": "",
        "topic": "RalphiteDS_10403418/Dado",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "a5ad4478e939728f",
        "x": 1860,
        "y": 340,
        "wires": []
    },
    {
        "id": "f31ee714dcdd840c",
        "type": "function",
        "z": "3fbf49387eea644f",
        "name": "function 6",
        "func": "var UmidadeSolo = msg.payload[0];\nvar Velocidade = msg.payload[1];\nvar UmidadeAr = msg.payload[2];\nif ((UmidadeAr >= 90 && UmidadeSolo >= 70) || Velocidade >= 50){\n    msg.payload = 1;\n}\nelse if (UmidadeAr < 90 && UmidadeSolo < 70 && Velocidade < 50){\n    msg.payload = 0;\n}\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1640,
        "y": 340,
        "wires": [
            [
                "389e45b9d175b7b3"
            ]
        ]
    },
    {
        "id": "f32ced5c882bce93",
        "type": "node-red-contrib-whatsapp-cmb-send-message",
        "z": "3fbf49387eea644f",
        "name": "",
        "credtype": "account",
        "account": "c3503dfcd830f958",
        "text": "payload",
        "phonenumbervalue": "",
        "apikeyvalue": "",
        "apikeyinputtypemessage": "msg",
        "phonenumberinputtypemessage": "msg",
        "inputtypemessage": "msg",
        "rejectssl": false,
        "x": 1820,
        "y": 420,
        "wires": [
            [
                "60bf62feb5e0a035"
            ]
        ]
    },
    {
        "id": "a5ad4478e939728f",
        "type": "mqtt-broker",
        "name": "",
        "broker": "broker.hivemq.com",
        "port": "1883",
        "clientid": "Ralphite_D",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": "4",
        "keepalive": "60",
        "cleansession": true,
        "autoUnsubscribe": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthRetain": "false",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closeRetain": "false",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willRetain": "false",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    },
    {
        "id": "bfb5b8374a6bb772",
        "type": "influxdb",
        "hostname": "https://us-east-1-1.aws.cloud2.influxdata.com",
        "port": "8086",
        "protocol": "http",
        "database": "database",
        "name": "Raphael Dias Sanches",
        "usetls": false,
        "tls": "",
        "influxdbVersion": "2.0",
        "url": "https://us-east-1-1.aws.cloud2.influxdata.com",
        "timeout": "10",
        "rejectUnauthorized": true
    },
    {
        "id": "c3503dfcd830f958",
        "type": "node-red-contrib-whatsapp-cmb-account",
        "name": ""
    }
]

**Sensor de Umidade do solo:**

//Incluir bibliotecas
#include <DHTesp.h>
#include <EspMQTTClient.h>

//Para saber mais sobre esta biblioteca, acessar https://github.com/plapointe6/EspMQTTClient

//Definicoes e constantes
char SSIDName[] = "Wokwi-GUEST"; //nome da rede WiFi
char SSIDPass[] = ""; //senha da rede WiFI

const int DHT_PIN = 15; //terminal do sensor de temperatura e umidade

char BrokerURL[] = "broker.hivemq.com"; //URL do broker MQTT
char BrokerUserName[] = ""; //nome do usuario para autenticar no broker MQTT
char BrokerPassword[] = ""; //senha para autenticar no broker MQTT
char MQTTClientName[] = "Raphael_10403418"; //nome do cliente MQTT
int BrokerPort = 1883; //porta do broker MQTT

String TopicoPrefixo = "RaphaelDS_10403418"; //prefixo do topico
String Topico_01 = TopicoPrefixo+"/Temperatura"; //nome do topico 01
String Topico_02 = TopicoPrefixo+"/Umidade"; //nome do topico 02

//Variaveis globais e objetos
DHTesp dhtSensor; //instancia o objeto dhtSensor a partir da classa DHTesp

EspMQTTClient clienteMQTT(SSIDName, SSIDPass, BrokerURL, BrokerUserName, BrokerPassword, MQTTClientName, BrokerPort); //inicializa o cliente MQTT

//Este prototipo de funcao deve estar sempre presente
void onConnectionEstablished() {
}

void enviarDados() {
  TempAndHumidity temp_umid = dhtSensor.getTempAndHumidity(); //instancia o objeto temp_umid a partir da classe TempAndHumidity
  
  //Serial.println("Temperatura: " + String(temp_umid.temperature, 2) + "°C");
  //Serial.println("Umidade: " + String(temp_umid.humidity, 1) + "%");
  //Serial.println("---");
    
  clienteMQTT.publish(Topico_01, String(temp_umid.temperature, 2) + "°C"); 
  clienteMQTT.publish(Topico_02, String(temp_umid.humidity, 1) + "%");
}

//Setup
void setup() {
  Serial.begin(9600);
  
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22); //inicializa o sensor de temperatura e umidade

  clienteMQTT.enableDebuggingMessages(); //habilita mensagens de debug no monitor serial
  //clienteMQTT.enableHTTPWebUpdater(); // Enable the web updater. User and password default to values of MQTTUsername and MQTTPassword. These can be overridded with enableHTTPWebUpdater("user", "password").
  //clienteMQTT.enableOTA(); // Enable OTA (Over The Air) updates. Password defaults to MQTTPassword. Port is the default OTA port. Can be overridden with enableOTA("password", port).
  //clienteMQTT.enableLastWillMessage("TestClient/lastwill", "Vou ficar offline");
}

//Loop
void loop() {
  //clienteMQTT.enableMQTTPersistence(); //estabelece uma conexao persistente
  clienteMQTT.loop(); //funcao necessaria para manter a conexao com o broker MQTT ativa e coletar as mensagens recebidas
  enviarDados(); //funcao para publicar os dados no broker MQTT

  if (clienteMQTT.isWifiConnected() == 1) {
    Serial.println("Conectado ao WiFi!");
  } else {
    Serial.println("Nao conectado ao WiFi!");
  }

  if (clienteMQTT.isMqttConnected() == 1) {
    Serial.println("Conectado ao broker MQTT!");
  } else {
    Serial.println("Nao conectado ao broker MQTT!");
  }

  Serial.println("Nome do cliente: " + String(clienteMQTT.getMqttClientName())
    + " / Broker MQTT: " + String(clienteMQTT.getMqttServerIp())
    + " / Porta: " + String(clienteMQTT.getMqttServerPort())
  );

  delay(5000);
}
https://wokwi.com/projects/397356988202270721

Sensor de umidade Ar:

//Incluir bibliotecas
#include <DHTesp.h>
#include <EspMQTTClient.h>

//Para saber mais sobre esta biblioteca, acessar https://github.com/plapointe6/EspMQTTClient

//Definicoes e constantes
char SSIDName[] = "Wokwi-GUEST"; //nome da rede WiFi
char SSIDPass[] = ""; //senha da rede WiFI

const int DHT_PIN = 15; //terminal do sensor de temperatura e umidade

char BrokerURL[] = "broker.hivemq.com"; //URL do broker MQTT
char BrokerUserName[] = ""; //nome do usuario para autenticar no broker MQTT
char BrokerPassword[] = ""; //senha para autenticar no broker MQTT
char MQTTClientName[] = "RaphaelDS_10403418"; //nome do cliente MQTT
int BrokerPort = 1883; //porta do broker MQTT

String TopicoPrefixo = "RalphiteDS_10403418"; //prefixo do topico
String Topico_01 = TopicoPrefixo+"/Temperatura"; //nome do topico 01
String Topico_02 = TopicoPrefixo+"/Umidade"; //nome do topico 02

//Variaveis globais e objetos
DHTesp dhtSensor; //instancia o objeto dhtSensor a partir da classa DHTesp

EspMQTTClient clienteMQTT(SSIDName, SSIDPass, BrokerURL, BrokerUserName, BrokerPassword, MQTTClientName, BrokerPort); //inicializa o cliente MQTT

//Este prototipo de funcao deve estar sempre presente
void onConnectionEstablished() {
}

void enviarDados() {
  TempAndHumidity temp_umid = dhtSensor.getTempAndHumidity(); //instancia o objeto temp_umid a partir da classe TempAndHumidity
  
  //Serial.println("Temperatura: " + String(temp_umid.temperature, 2) + "°C");
  //Serial.println("Umidade: " + String(temp_umid.humidity, 1) + "%");
  //Serial.println("---");
    
  clienteMQTT.publish(Topico_01, String(temp_umid.temperature, 2) + "°C"); 
  clienteMQTT.publish(Topico_02, String(temp_umid.humidity, 1) + "%");
}

//Setup
void setup() {
  Serial.begin(9600);
  
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22); //inicializa o sensor de temperatura e umidade

  clienteMQTT.enableDebuggingMessages(); //habilita mensagens de debug no monitor serial
  //clienteMQTT.enableHTTPWebUpdater(); // Enable the web updater. User and password default to values of MQTTUsername and MQTTPassword. These can be overridded with enableHTTPWebUpdater("user", "password").
  //clienteMQTT.enableOTA(); // Enable OTA (Over The Air) updates. Password defaults to MQTTPassword. Port is the default OTA port. Can be overridden with enableOTA("password", port).
  //clienteMQTT.enableLastWillMessage("TestClient/lastwill", "Vou ficar offline");
}

//Loop
void loop() {
  //clienteMQTT.enableMQTTPersistence(); //estabelece uma conexao persistente
  clienteMQTT.loop(); //funcao necessaria para manter a conexao com o broker MQTT ativa e coletar as mensagens recebidas
  enviarDados(); //funcao para publicar os dados no broker MQTT

  if (clienteMQTT.isWifiConnected() == 1) {
    Serial.println("Conectado ao WiFi!");
  } else {
    Serial.println("Nao conectado ao WiFi!");
  }

  if (clienteMQTT.isMqttConnected() == 1) {
    Serial.println("Conectado ao broker MQTT!");
  } else {
    Serial.println("Nao conectado ao broker MQTT!");
  }

  Serial.println("Nome do cliente: " + String(clienteMQTT.getMqttClientName())
    + " / Broker MQTT: " + String(clienteMQTT.getMqttServerIp())
    + " / Porta: " + String(clienteMQTT.getMqttServerPort())
  );

  delay(5000);
}

https://wokwi.com/projects/397356886001759233

**Servo motor:**

//Incluir bibliotecas
#include <EspMQTTClient.h>
#include <ESP32Servo.h>

//Para saber mais sobre esta biblioteca, acessar https://github.com/plapointe6/EspMQTTClient

//Definicoes e constantes
char SSIDName[] = "Wokwi-GUEST"; //nome da rede WiFi
char SSIDPass[] = ""; //senha da rede WiFI

#define ServoPin GPIO_NUM_2
int msg = 0;
int fechado = 0;
int pos = 0;
Servo servo;

char BrokerURL[] = "broker.hivemq.com"; //URL do broker MQTT
char BrokerUserName[] = ""; //nome do usuario para autenticar no broker MQTT
char BrokerPassword[] = ""; //senha para autenticar no broker MQTT
char MQTTClientName[] = "Ralphite_10403418"; //nome do cliente MQTT
int BrokerPort = 1883; //porta do broker MQTT

String TopicoPrefixo = "RalphiteDS_10403418"; //prefixo do topico
String Topico_01 = TopicoPrefixo+"/Dado"; //nome do topico 01

//Variaveis globais e objetos
EspMQTTClient clienteMQTT(SSIDName, SSIDPass, BrokerURL, BrokerUserName, BrokerPassword, MQTTClientName, BrokerPort); //inicializa o cliente MQTT

//Este prototipo de funcao deve estar sempre presente
void onConnectionEstablished() {
}

void lerDados() {
  clienteMQTT.subscribe(Topico_01, [](const String & topic, const String & payload){
    msg = payload.toInt();
  });
  return;
}

//Setup
void setup() {
  servo.attach(ServoPin);
  Serial.begin(9600);
  servo.write(0);

  clienteMQTT.enableDebuggingMessages(); //habilita mensagens de debug no monitor serial
  //clienteMQTT.enableHTTPWebUpdater(); // Enable the web updater. User and password default to values of MQTTUsername and MQTTPassword. These can be overridded with enableHTTPWebUpdater("user", "password").
  //clienteMQTT.enableOTA(); // Enable OTA (Over The Air) updates. Password defaults to MQTTPassword. Port is the default OTA port. Can be overridden with enableOTA("password", port).
  //clienteMQTT.enableLastWillMessage("TestClient/lastwill", "Vou ficar offline");
}

//Loop
void loop() {
  //clienteMQTT.enableMQTTPersistence(); //estabelece uma conexao persistente
  clienteMQTT.loop(); //funcao necessaria para manter a conexao com o broker MQTT ativa e coletar as mensagens recebidas
  lerDados(); //funcao para ler os dados no broker MQTT
  Serial.println(msg);
  Serial.println(fechado);

  if (clienteMQTT.isWifiConnected() == 1) {
    Serial.println("Conectado ao WiFi!");
  } else {
    Serial.println("Nao conectado ao WiFi!");
  }

  if (clienteMQTT.isMqttConnected() == 1) {
    Serial.println("Conectado ao broker MQTT!");
  } else {
    Serial.println("Nao conectado ao broker MQTT!");
  }

  Serial.println("Nome do cliente: " + String(clienteMQTT.getMqttClientName())
     + " / Broker MQTT: " + String(clienteMQTT.getMqttServerIp())
     + " / Porta: " + String(clienteMQTT.getMqttServerPort())
  );

  if (msg == 1 && fechado == 0){
      Serial.println(msg);
      servo.write(90);
      fechado = 1;
      Serial.println("Fechado");

  }
  else if (msg == 0 && fechado == 1){
      Serial.println(msg);
      servo.write(0);
      fechado = 0;
      Serial.println("Aberto");
  }

  delay(2000);
}

https://wokwi.com/projects/397992828649088001

**Link do Vídeo:**

https://youtu.be/yAEQ6NSzmdk
