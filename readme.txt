--- OceanGuard: Sistema de Monitoramento e Preservação do Oceano ---

Simulação no Wokwi: https://wokwi.com/projects/399889287137810433

Integrantes do grupo:
 - Bruno Carneiro Leão - 555563
 - Paulo Akira Okama-556840
 - Victor Capp - 555753

-- Descrição do Projeto --

OceanGuard é um sistema desenvolvido para monitorar e preservar o oceano da melhor maneira possível. 
Utilizando o Arduino como plataforma principal, o sistema coleta, exibe e armazena dados ambientais, tais como temperatura e umidade por enquanto, 
fornecendo alertas visuais e sonoros quando as condições ultrapassam limites predefinidos. 
Este projeto é essencial para manter ambientes sensíveis, como aquários e tanques de reprodução marinha, 
dentro de parâmetros seguros e analisar os dados para que melhores decisões sobre os problemas que permeiam o oceano hoje em dia, sejam tomadas.

-- Funcionalidades --

 - Leitura de Temperatura e Umidade: Utiliza um sensor DHT22 para medir e monitorar constantemente a temperatura e a umidade do ambiente.
 - Exibição em Display LCD: Mostra as leituras de temperatura, umidade, data e hora em um display LCD 16x2 com interface I2C.
 - Armazenamento de Dados: Registra as leituras na memória EEPROM do Arduino, permitindo um histórico de até 100 registros.
 - Notificações Visuais e Sonoras: LEDs indicam se as condições estão dentro dos limites aceitáveis, em estado de aviso ou em situação crítica. 
   Um buzzer é ativado em condições críticas.
 - Comunicação Serial: Envia os dados coletados para o monitor serial para uma análise em tempo real.

-- Componentes Utilizados --

 - Arduino Uno
 - Sensor DHT22
 - Display LCD 16x2 com Interface I2C
 - Módulo RTC DS1307
 - EEPROM
 - LEDs (Verde, Amarelo, Vermelho)
 - Buzzer
 - Jumpers e Protoboard

-- Bibliotecas Necessárias -- 

As bibliotecas utilizadas no projeto, e que devem ser instaladas no Arduino IDE:

 - LiquidCrystal_I2C -> LiquidCrystal I2C: Para controle do display LCD.
 - RTClib -> RTClib: Para manipulação do módulo RTC.
 - Wire: Para comunicação I2C.
 - EEPROM: Para manipulação da memória EEPROM.
 - DHT22 -> DHT sensor library: Para o sensor de temperatura e umidade.

-- Intruções de Montagem -- 

Conecte os componentes da seguinte maneira:

 - DHT22: Pino de dados no pino digital 2 do Arduino.
 - LCD: Interface I2C nos pinos SDA e SCL.
 - RTC DS1307: SDA e SCL nos pinos analógicos A4 e A5, respectivamente.
 - LEDs: Pinos 8, 9 e 10 para LEDs verde, amarelo e vermelho, respectivamente.
 - Buzzer: Pino 11 do Arduino.

-- Instalação --

1. Clone ou baixe o repositório.
2. Abra o arquivo do projeto no Arduino IDE.
3. Instale as bibliotecas necessárias utilizando o Gerenciador de Bibliotecas do Arduino IDE.
4. Conecte os componentes conforme as instruções de montagem.
5. Faça o upload do código para o Arduino.


 --- Instruções de Uso ---

-- Inicialização --

1. Após fazer o upload do código e conectar os componentes, o display LCD exibirá uma mensagem de inicialização seguida por uma mensagem de carregamento.

-- Operação --

O display LCD alternará a exibição entre a data/hora e os valores de temperatura/umidade a cada 15 segundos.
LEDs indicarão o estado das leituras:
 - Verde: Condições normais (temperatura entre 20-35°C e umidade acima de 40%).
 - Amarelo: Estado de aviso (temperatura entre 35-40°C ou umidade entre 30-40%).
 - Vermelho: Situação crítica (temperatura acima de 40°C ou umidade abaixo de 30%), com o buzzer soando para estados críticos.

-- Armazenamento de Dados --

A cada minuto, os dados de temperatura e umidade são armazenados na EEPROM.
Os dados podem ser acessados via monitor serial, exibindo o timestamp, temperatura e umidade.

-- Monitor Serial -- 

Ative a opção de comunicação serial (SERIAL_OPTION) para visualizar os dados coletados em tempo real.
Ative a opção do log (LOG_OPTION) e use o comando get_log() para visualizar o histórico de dados armazenados na EEPROM.

-- Funções --

 - get_log: Lê e mostra no monitor serial o que esta guardado na memória EEPROM.
 - getNextAddress: pega o próximo endereço da EEPROM, para registro dos dados.

--- Objetivos do Projeto ---

O OceanGuard visa oferecer uma solução eficiente para monitorar as condições ambientais dos oceanos, 
proporcionando dados precisos e em tempo real para ajudar na preservação dos ecossistemas marinhos. 
O sistema alerta os operadores sobre mudanças nas condições ambientais, 
permitindo respostas rápidas e informadas para diminuir impactos adversos.

--- Público-Alvo ---

O OceanGuard é destinado a pesquisadores, ambientalistas, autoridades governamentais e organizações não governamentais que trabalham na preservação e monitoramento dos oceanos. 
Ele também pode ser útil para indústrias que dependem de dados ambientais marinhos, como a pesca e o turismo. Mas no geral ele pode ser usado por qualquer pessoa, 
visando o aprendizado e conscientização sobre a saúde dos oceanos e proporcionando assim um futuro e pessoas com pensamentos sustentáveis.

--- Benefícios Oferecidos ---

 - Monitoramento Contínuo: Coleta constante de dados ambientais críticos.
 - Alertas Imediatos: Notificações visuais e sonoras para condições adversas.
 - Armazenamento de Dados: Registro histórico para análise de tendências.
 - Acesso Remoto: Conectividade para monitoramento e controle a distância.
 - Interface Amigável: Exibição clara e direta dos dados coletados.

--- Melhorias para Melhorar o projeto --- 

1. Sensores Adicionais:
	- pH Sensor: Medir a acidez da água pode fornecer dados críticos sobre a saúde do ambiente marinho.
	- Sensor de Salinidade: A salinidade é um parâmetro crucial em ambientes marinhos e deve ser monitorada constantemente.

2. Conectividade e Comunicação:
	- Módulo Wi-Fi ou GSM: Permitir a transmissão de dados para a nuvem ou para um servidor central. 
	  Isso facilita o monitoramento remoto e a análise de dados em tempo real por pesquisadores e autoridades ambientais.
	- Notificações SMS/Email: Enviar alertas diretamente para smartphones ou emails dos operadores em caso de condições críticas.

3. Painel Solar: 
	- Integrar um painel solar para alimentação autônoma do sistema, garantindo operação contínua em ambientes remotos.

4. Geolocalização: 
	- Adicionar um módulo GPS para registrar a localização exata dos pontos de monitoramento, útil para grandes áreas e estudos geográficos.

5. Interface de Usuário Amigável:
	- Aplicativo Móvel ou Web: Desenvolver um aplicativo ou interface web para visualizar os dados coletados, 
	  configurar parâmetros de alerta e acessar o histórico de dados de maneira mais intuitiva.

6. Análise de Dados:
	- Integração com Plataformas de Análise de Dados: Enviar os dados coletados para plataformas de análise como ThingSpeak ou Google Cloud, 
	  permitindo o uso de ferramentas avançadas de análise de dados e machine learning para prever condições ambientais adversas.

7. Sistema de Filtragem e de detecção:
	- A adição de um sistema de filtragem e detecção no projeto OceanGuard visa melhorar a qualidade dos dados coletados, 
	  e fornecer alertas mais precisos sobre a presença de substâncias nocivas na água. Por exemplo: Sensores de Poluentes, Sistemas de Filtragem e Módulos de Processamento.

-- Contribuição --

Contribuições são bem-vindas! Sinta-se à vontade para enviar sugestões ao nosso projeto, como podemos deixa-lo melhor por exemplo,
e mais próximo de um projeto funcional e acessível.

-- Licença -- 

@2024 SeaTech Solutions - Todos os direitos reservados

Este README foi elaborado para fornecer uma visão abrangente do projeto OceanGuard, suas funcionalidades e como ele pode ser utilizado e aprimorado. 
O foco está em garantir clareza e organização para facilitar o entendimento e uso do sistema.



