# Projeto AACD

## Objetivo

O objetivo desta aula é apresentar aos estudantes a plataforma Arduino + Tapete Tátil que será utilizada para prototipação da solução e suas respectivas interfaces de comunicação. 

Espera-se que ao término da instrução o estudante possa conhecer ou relembrar a plataforma Arduino, as maneiras de programá-lo e as formas de interfacear ela com outros sistemas. 

Para esta familiarização, será utilizado a interface de programação Arduino e os pacotes disponíveis para seu controle na linguagem Arduino. 

Neste encontro serão abordados: Apresentação do Arduino e suas aplicações; Arquitetura de sistemas utilizando Arduínos; Características do Arduíno; Interface de programação aberta do Arduíno.

## Assuntos relacionados

- Atuadores
- Energia em sistemas embarcados
- Microcontroladores
- Programação de microcontroladores
- Simulação de sistemas embarcados


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

Esse compilador de alto nível, desenvolvido pelos alunos, deverá **resolver uma gameficação do TO** (Terapeuta Ocupacional) da AACD.

A gameficação contará com a entrada de dados provenientes do [Greg Maker](https://www.gregmaker.com.br/), **que transforma os toques manuais** sobre objetos semicondutores e condutores em **movimentos do mouse e algumas teclas do teclado**, como barra de espaço, ENTER e setas.

**O responsável pela detecção dos toques manuais é o Arduino Uno R3**.

Exemplo: a figura abaixo apresenta alimentos semicondutores e objetos condutores (marmita de alumínio) conectados ao Greg Maker, que ao serem tocados, moverá o mouse na tela do computador, ou pressionará a barra de espaço ou o ENTER ou as setas. Vai depender de quais fios foram conectados em cada objeto.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/gregMaker.png">
   <img alt="Família ESP32" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/gregMaker.png)">
</picture>


## Arduino Uno - Documentação

[Fonte](https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf)

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3.png">
   <img alt="Arduino Uno R3" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/ProjetoAACD/blob/main/imgs/arduinoUnoR3.png)">
</picture>



