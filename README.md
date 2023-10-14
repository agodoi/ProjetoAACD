# Interface com um Dispositivo Embarcado

## Objetivos

O objetivo desta aula é apresentar aos estudantes a plataforma Arduino + Tapete Sensorial que serão utilizados para prototipação da solução AACD.

Espera-se que ao término da instrução o estudante possa conhecer ou relembrar a plataforma Arduino, as maneiras de programá-lo e as formas de interfaceá-la com outros sistemas.

Para esta familiarização, será utilizado a interface de programação Arduino e os pacotes disponíveis para seu controle na linguagem Arduino. 

Neste encontro serão abordados: 

- Apresentação do Arduino e suas aplicações;
- Arquitetura de sistemas utilizando Arduínos;
- Características do Arduíno;
- Interface de programação aberta do Arduíno.

## Assuntos relacionados

- Atuadores;
- Energia em sistemas embarcados;
- Microcontroladores;
- Programação de microcontroladores;
- Simulação de sistemas embarcados.


## O que é o Arduino?

A plataforma Arduino é um sistema de desenvolvimento de código aberto baseado em hardware e software que é amplamente utilizado para prototipagem eletrônica e criação de projetos interativos. 

Ela foi criada para tornar a eletrônica mais acessível aos estudantes, permitindo que eles desenvolvam projetos que envolvem controle de hardware de maneira relativamente simples.

A plataforma Arduino consiste em vários elementos:

1. **Hardware**: O núcleo do hardware é a placa Arduino, que é equipada com um microcontrolador (geralmente da família AVR da Atmel/Microchip) e vários pinos de entrada/saída digitais e analógicos. Além da placa principal, existem diversas variações e modelos de placas Arduino (como mostra a figura a seguir) adequados para diferentes tipos de projetos. Elas podem ser alimentadas via USB, bateria ou fonte externa. O que diferencia uma placa da outra é o seu tamanho físico (alguns projetos precisam ser miniaturizados), a quantidade de memória RAM e ROM, número de portais GPIO (General Purpose Input Output), tensão de trabalho e protocolos de comunicação.

2. **Software**: A plataforma Arduino utiliza uma IDE (Integrated Development Environment) que fornece um ambiente de programação amigável. O software permite escrever, compilar e fazer o upload de código para a placa Arduino. O código é escrito em uma linguagem baseada em C/C++, simplificada para facilitar o aprendizado e o desenvolvimento.

3. **Bibliotecas**: O ecossistema Arduino inclui uma vasta coleção de bibliotecas que facilitam o acesso a diversos periféricos e funcionalidades de hardware. Isso simplifica o processo de desenvolvimento, uma vez que muitas tarefas comuns já foram implementadas e podem ser facilmente utilizadas.

4. **Comunidade**: A plataforma Arduino tem uma comunidade ativa e envolvida de entusiastas e desenvolvedores que compartilham projetos, tutoriais e soluções. Isso torna mais fácil aprender e solucionar problemas relacionados ao Arduino. As comunidades estão espalhadas no YouTube, Facebook, Blogs em geral. Site oficial do [Arduino](https://www.arduino.cc/) onde você encontra a documentação completa.

5. **Extensibilidade**: A plataforma Arduino é altamente extensível, permitindo que os usuários adicionem componentes e módulos de hardware personalizados para atender às necessidades específicas de seus projetos.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/familiaArduino.jpg">
   <img alt="Família Arduino" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/familiaArduino.jpg)">
</picture>

### Curiosidade

O ESP32 é um microcontrolador que pode ser programado usando a mesma plataforma Arduino IDE. O ESP32 é de baixo custo e de alto desempenho, amplamente utilizado em projetos de IoT e em aplicações de comunicação sem fio, como WiFi e Bluetooth. Qual as relações entre ESP32 e a família Arduino?

1. **Suporte Arduino**: A comunidade Arduino desenvolveu uma plataforma para o ESP32, que permite programar o ESP32 utilizando a IDE Arduino, da mesma maneira que se programa um Arduino tradicional. Isso facilita a programação e o desenvolvimento de projetos, especialmente para aqueles que já estão familiarizados com o ambiente Arduino.

2. **Bibliotecas Arduino**: O ESP32 é compatível com muitas das bibliotecas Arduino existentes. Isso significa que você pode usar bibliotecas Arduino padrão para sensores, atuadores e outros componentes em projetos baseados em ESP32.

3. **Ecosistema Arduino**: Como o ESP32 é compatível com o ambiente Arduino, ele se beneficia do vasto ecosistema Arduino, que inclui uma grande quantidade de exemplos de código, tutoriais, comunidade ativa e recursos de aprendizado.

4. **Placas ESP32 compatíveis com Arduino**: Há várias placas de desenvolvimento ESP32 que foram projetadas para serem compatíveis com o formato e os pinos das placas Arduino. Isso permite que os usuários utilizem shields Arduino com suas placas ESP32.

5. **Programação em C/C++**: Embora o ambiente Arduino simplifique a programação do ESP32, você ainda está programando em linguagem C/C++. Isso significa que é possível acessar diretamente o hardware do ESP32 e desenvolver código de baixo nível quando necessário. Outro ponto importante é que o ESP32 possui maior memória interna que o Arduino Uno R3, e por isso, o ESP32 pode ser convertido para microPython, que é uma variação do Python adaptada ao microcontrolador.


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ESP32Familia.png">
   <img alt="Família ESP32" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ESP32Familia.png)">
</picture>


### O modelo que vamos adotar nesse projeto é o Arduino Uno


## Qual a função do Arduino Uno R3 no projeto?

O projeto AACD é o **desenvolvimento de um compilador para PC "de alto nível"** que será transformado para linguagem Python. Esse Python chamaremos de "baixo nível" que rodará no ambiente Windows.

Esse compilador de alto nível, desenvolvido pelos alunos, deverá **resolver uma gamificação do TO** (Terapeuta Ocupacional) da AACD.

A gamificação contará com a entrada de dados provenientes do [Greg Maker](https://www.gregmaker.com.br/), **que transforma os toques manuais** sobre objetos semicondutores e condutores em **movimentos do mouse e algumas teclas do teclado**, como barra de espaço, ENTER e setas.

**O responsável pela detecção dos toques manuais é o Arduino Uno R3**.

Exemplo: a figura abaixo apresenta alimentos e objetos condutores e semicondutores conectados ao Greg Maker, que ao serem tocados manualmente por uma pessoa com deficiência motora ou cerebral, moverá o mouse na tela do computador, ou pressionará a barra de espaço ou o ENTER ou alguma opção de setas. Vai depender de quais fios foram conectados em cada objeto.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/gregMaker.png">
   <img alt="Família ESP32" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/gregMaker.png)">
</picture>

## Diagrama de Blocos da Solução

A figura a seguir demonstra o diagrama de blocos da solução mínima para a fundação AACD. Observe com calma!

**A missão desse projeto está na gamificação para o ambiente Windows e não no Arduino Uno R3**.

O Arduino é somente um sistema embarcado que captura dados de toques e os converte em movimentos do mouse e algumas teclas do teclado.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArquiteturaAACD.jpg">
   <img alt="Família ESP32" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArquiteturaAACD.jpg)">
</picture>

## Arduino Uno - Documentação

Nessa instrução, vamos explorar o hardware que converterá os toques manuais nos **trem da mesa :)** em movimentos do mouse e teclado.

[Fonte](https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf)

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3.png)">
</picture>

### Esquemático Eletrônico

Na figura a seguir você pode entender com mais profundidade, do que é feita uma placa Arduino Uno R3. 

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/Arduino-UNO-Description.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/Arduino-UNO-Description.png)">
</picture>

Perceba que a placa possui dois conectores ICSP (In-Circuit Serial Programming). Ambos servem para programar um chip mesmo já inserido na placa e com todos os componentes eletrônicos em sua volta. [Documentação](https://ww1.microchip.com/downloads/en/DeviceDoc/30277d.pdf). Como há dois chips programáveis no Arduino IDE, um ICSP é do chip USB e o outro ICSP é do Arduino.

O Greg Maker usou o ICSP do chip USB, **chip U3** da figura a seguir para alterar seu firmware e converter a comunicação USB em comandos padronizados de mouse e teclado. É como se o Arduino se comportasse como um adaptador de mouse e teclaso sem fio. Mas o Arduino não sai assim de fábrica. Precisa reprogramar o conversor USB U3 da imagem a seguir. Esse chip conversor USB tem que ser o "quadradinho" e não um retângulo. O retângulo não aceita reprogramação de firmware.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3Esquematico.png">
   <img alt="Esquemático do Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3Esquematico.png)">
</picture>

O que tem na placa dessa arquitetura embarcada?

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoChips.png">
   <img alt="Esquemático do Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoChips.png)">
</picture>


### Energização 

Sobre a alimentação, o Arduino possui as seguintes limitações:

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoAlimentacao.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoAlimentacao.png)">
</picture>


E a árvore de energização da placa segue o seguinte padrão:


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoAlimentacao2.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoAlimentacao2.png)">
</picture>


### Pinout Arduino Uno R3

O pinout (significado de cada pino) é demonstrado na imagem a seguir:

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoPinout.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoPinout.png)">
</picture>

### Tipos de Arquiteturas para Microcontroladores

Nesse projeto, é importante entender as possíveis diferentes arquiteturas dos microcontroladores. Como introdução, observe quais duas arquiteturas são possíveis ao se construir um microncontrolador ou microprocessador.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArquiteturaVonNeumann_Harvard.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArquiteturaVonNeumann_Harvard.png)">
</picture>

A arquitetura von Neumann e a arquitetura Harvard são dois paradigmas de design de computadores que diferem na maneira como tratam o armazenamento e a execução de instruções e dados. Essas arquiteturas têm implicações na operação e no desempenho dos sistemas, e podem ser contextualizadas na arquitetura do Arduino da seguinte maneira:

#### Arquitetura Von Neumann:

1. **Armazenamento de Instruções e Dados:** Na arquitetura von Neumann, tanto as instruções quanto os dados são armazenados na mesma memória, a RAM. Isso significa que o programa e os dados compartilham a mesma memória física.

2. **Barramento Único:** A arquitetura von Neumann usa um único barramento para transferir tanto instruções quanto dados entre a memória e a unidade de processamento (CPU). Isso pode criar gargalos de desempenho quando há muitas operações de leitura/gravação simultâneas.

3. **Programas Graváveis:** É possível gravar programas na memória do Arduino durante a programação, pois o microcontrolador da série AVR geralmente usado em placas Arduino segue a arquitetura von Neumann.

#### Arquitetura Harvard:

1. **Memória Separada:** Na arquitetura Harvard, as instruções e os dados são armazenados em memórias separadas. A memória de instruções (geralmente flash) é usada apenas para armazenar programas, enquanto a memória de dados (RAM) é usada para armazenar dados temporários.

2. **Barramentos Separados:** A arquitetura Harvard utiliza barramentos separados para transferir instruções e dados entre as memórias e a CPU. Isso permite que instruções e dados sejam buscados em paralelo, melhorando o desempenho.

3. **Programas Fixos:** Em placas Arduino baseadas na arquitetura Harvard, como o Arduino Uno, os programas são gravados na memória flash durante a programação e não podem ser modificados em tempo de execução. Isso difere da arquitetura von Neumann, onde os programas podem ser gravados e modificados durante a execução.

**O Arduino UNO é um exemplo de placa que usa a arquitetura Harvard**, uma vez que possui memórias de programa (flash) e de dados (RAM) separadas e utiliza barramentos distintos para transferir instruções e dados. 

A divisão entre instruções e dados contribui para a segurança e estabilidade do sistema, uma vez que impede a sobrescrita acidental de instruções de programa, mas limita a flexibilidade para atualização de programas em tempo real. Por outro lado, a arquitetura von Neumann, embora menos comum em microcontroladores modernos, permite maior flexibilidade na modificação dos programas, pois instruções e dados compartilham a mesma memória.

### Arquitetura Interna do Arduino Uno

A figura a seguir apresenta a arquitetura interna do Arduino Uno, e em destaque, tem-se as duas memórias (Flash e RAM) separadas.

Na memória Flash fica o código-fonte criado pelo desenvolvedor, enquanto que na memória SRAM, ficam os dados e variáveis que o programa instancia.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoArquitetura.jpg">
   <img alt="Tipos de Arquitetura" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/ArduinoArquitetura.jpg)">
</picture>

A memória SRAM (Static Random-Access Memory) no Arduino Uno R3 é uma parte importante da memória do microcontrolador ATmega328P usado nesta placa. Ela desempenha várias funções cruciais:

1. **Armazenamento de Dados Temporários:** A memória SRAM é usada para armazenar dados temporários durante a execução de programas. Isso inclui variáveis, buffers e outras estruturas de dados que o programa Arduino utiliza. A SRAM é a memória mais rápida disponível no microcontrolador, tornando-a ideal para armazenar dados que precisam ser acessados e modificados rapidamente.

2. **Pilha (Stack):** A memória SRAM também é usada para a pilha de chamadas (stack), que é fundamental para a execução de funções e a gestão do fluxo de execução do programa. Quando uma função é chamada, as informações necessárias para retornar à função chamadora são armazenadas na pilha.

3. **Armazenamento de Variáveis Globais:** Variáveis globais declaradas no programa Arduino são armazenadas na SRAM. Essas variáveis podem ser acessadas e modificadas em várias partes do programa.

4. **Buffer Serial:** A memória SRAM é frequentemente usada para criar buffers para comunicação serial, como UART. Isso permite a armazenagem temporária de dados que estão sendo enviados ou recebidos pela porta serial.

5. **Armazenamento de Dados do Usuário:** Seu programa Arduino pode usar a SRAM para armazenar dados que precisam ser retidos enquanto o dispositivo está em execução. Isso pode incluir valores de sensores, configurações personalizadas, contagens e outras informações relevantes ao seu projeto.

É importante notar que a memória SRAM no Arduino Uno R3 é relativamente limitada, com apenas 2 KB disponíveis. Portanto, ao escrever programas, é fundamental gerenciar eficientemente o uso da SRAM, evitando o esgotamento dela, o que pode causar comportamento inesperado ou falhas no programa. O uso excessivo de SRAM é uma das principais razões para erros de alocação de memória no Arduino. Portanto, é importante otimizar o código e alocar a SRAM com sabedoria para garantir um funcionamento estável e confiável de seu projeto.

A memória flash no Arduino Uno R3 desempenha um papel fundamental no armazenamento de programas (código-fonte) que são carregados no microcontrolador ATmega328P, que é o coração do Arduino Uno. Aqui está o que a memória flash faz:

1. **Armazenamento de Programas:** A memória flash é usada para armazenar o programa ou código-fonte que você escreve no Arduino Uno. Isso inclui todas as instruções e funções que compõem seu sketch do Arduino. Quando você faz o upload de um novo programa para o Arduino, ele é gravado na memória flash.

2. **Programas Fixos:** A memória flash é considerada "não volátil", o que significa que os programas carregados nela são retidos mesmo quando o Arduino é desligado. Isso permite que o Arduino execute o programa sempre que for ligado ou resetado, tornando-o adequado para aplicações autônomas.

3. **Espaço Limitado:** A capacidade de armazenamento da memória flash em um Arduino Uno R3 é de 32 KB (kilobytes). Isso inclui tanto o programa em si quanto algumas informações do bootloader, que é o software que permite o carregamento de novos programas no Arduino.

4. **Leitura de Programas:** Durante a execução, a CPU do microcontrolador lê as instruções do programa na memória flash e as executa sequencialmente.

É importante ter em mente que a capacidade de armazenamento da memória flash é limitada. Portanto, ao programar para o Arduino Uno, é essencial otimizar seu código para economizar espaço na memória flash. Isso pode incluir práticas como evitar o uso excessivo de bibliotecas, remover código não utilizado e usar variáveis eficientemente.

Além disso, a memória flash também é onde o bootloader do Arduino Uno reside. O bootloader é um pequeno programa que permite que você faça o upload de novos sketches para o Arduino através da porta USB. Ele é executado sempre que você carrega um novo programa, e depois permite que esse programa seja gravado na memória flash. Portanto, a memória flash serve como o local de armazenamento e execução de programas, tornando o Arduino Uno um dispositivo programável e reprogramável.

### Curiosidade

Se você perder o adaptador do seu mouse ou teclado USB sem fio, não vai adiatar simplesmente comprar outro adaptador, pois existe um pareamento a ser feito entre receptor e o mouse.

[Vídeo](https://www.youtube.com/watch?v=7uzlEaQ2V70)



## Teclado USB

Esse vídeo explica como o protocolo USB funciona e como o teclado envia dados para o PC.

[Vídeo](https://www.youtube.com/watch?v=wdgULBpRoXk)

Exemplo de código que desliga o PC ao conectar o Arduino Uno na parta USB.

```
/* Arduino USB HID Keyboard Demo
 * Random Key/Random Delay
 */
uint8_t buf[8] = { 
  0 };   /* Keyboard report buffer */

void setup() 
{
  Serial.begin(9600);
  randomSeed(analogRead(0));
  delay(200);
}

void loop() 
{
  //int randomChar = random(4, 130);
  //long randomDelay = random(1000, 10000);

   delay(5000);
   buf[0] = (1<<3);
   buf[2] = 21;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   delay(1000);
   buf[2] = 22;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 11;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 24;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 23;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 7;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 18;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 26;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 17;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 44;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 84;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 22;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 44;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 84;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   buf[2] = 9;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   //Keyboard.print(" /f");
   buf[2] = 40;
   Serial.write(buf, 8); // Send keypress
   releaseKey();
   delay(1000);
}

void releaseKey() 
{
   buf[0] = 0;
   buf[2] = 0;
   Serial.write(buf, 8); // Release key  
}
```

## Mouse USB

Esse vídeo explica como o mouse varre a superfície e tranforma em movimentos.

[Vídeo](https://www.youtube.com/watch?v=SAaESb4wTCM)


## Atuadores

Atuadores são componentes ou dispositivos que convertem um sinal de controle em uma ação física, ou seja, eles são responsáveis por efetuar uma mudança no ambiente físico. No ecossistema do Arduino, os atuadores são frequentemente usados para controlar luzes, movimento, som, temperatura, entre outros. Eles desempenham um papel crucial em projetos onde você deseja criar interações ou controle com o mundo real. Abaixo estão alguns exemplos de atuadores comuns no ecossistema do Arduino:

1. **Servo Motor**: Um servo motor é um atuador que gira em um ângulo específico com base no sinal de controle. Eles são amplamente utilizados para controlar movimentos precisos, como abrir uma porta, mover um braço robótico ou ajustar um sistema de câmera. Por exemplo, um servo motor pode ser usado em um projeto de braço robótico controlado por um Arduino.

2. **Motor de Passo**: Os motores de passo são usados para controlar o movimento em incrementos discretos. Eles são ideais para aplicações que exigem controle preciso, como impressoras 3D, CNC (Controle Numérico Computadorizado) ou telescópios automatizados.

3. **Motores DC**: Os motores de corrente contínua (DC) são atuadores que giram em uma direção quando energizados. Eles são comumente usados para mover rodas de robôs, ajustar a posição de uma cortina, ou criar dispositivos que envolvem movimento linear.

4. **LEDs (Diodos Emissores de Luz)**: Embora os LEDs sejam frequentemente usados para indicar status e iluminação, eles também podem ser considerados atuadores, pois alteram o estado da luz. Por exemplo, você pode usar um LED para criar um sistema de sinalização visual em seu projeto.

5. **Relés**: Os relés são interruptores controlados eletronicamente. Eles são usados para controlar dispositivos de alta potência, como lâmpadas, motores de CA (corrente alternada) ou aquecedores. Um exemplo seria o uso de um relé para ligar/desligar uma lâmpada de forma remota usando um Arduino.

6. **Buzzer ou Alto-falante**: Esses dispositivos emitem som quando energizados. Eles são usados para criar sons, alarmes ou sinais sonoros em projetos. Por exemplo, você pode usar um buzzer para criar um alarme sonoro em um sistema de segurança doméstica.

7. **Válvulas Solenoides**: As válvulas solenoides são atuadores que controlam o fluxo de líquidos ou gases. Elas são comuns em sistemas de irrigação, controle de fluidos e automação industrial. Um Arduino pode ser usado para controlar uma válvula solenoide em um sistema de irrigação automatizado para jardins.

**Nesse projeto, é provável que as soluções se direcionam para o item (6). Além disso, vamos usar uma tela como interface. A tela não é exatamente um atuador, pois não resulta numa ação física. Mas é tão importante quanto, pois é onde se complementa a experiência do usuário**.


## Simulação de sistemas embarcados

### Parte prática

Usando o [TinkerCad](https://www.tinkercad.com/dashboard), puxe um Arduno Uno R3 para a área de desenvolvimento da tela, e faça um pisca-pisca.

