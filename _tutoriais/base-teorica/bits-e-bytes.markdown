---
layout: page
title:  "Bits e Bytes: Computação em baixo nível"
order: 20
---

Talvez você já tenha ouvido falar que na computação tudo é 0 ou 1. No fim das contas, tudo o que está acontecendo no nosso computador, e também em nossos celulares e na maioria dos aparelhos eletrônicos, se resume a 0 e 1.

Neste tutorial você começará a entender o porquê. Você aprenderá a base teórica necessária para aprender o sistema binário, aprenderá o que de fato são bits e o que de fato são os bytes, que você está tão acostumado a falar quando se refere à velocidade da sua internet ou à quantidade de memória do seu computador.

Isto é importante porque, no processo de hackear um jogo, são aos arquivos binários que nós temos acesso. O processo de engenharia reversa consiste em buscar e interpretar os arquivos binários.

## Corrente alternada e corrente contínua

A eletricidade que trafega pelas redes elétricas e vem do poste até as nossas tomadas está em **corrente alternada**. Quando plugamos o fio na tomada de um equipamento que possui uma fonte, como um videogame, um notebook e um carregador de celular, o papel dessa fonte é gerar **corrente contínua** a partir dessa corrente alternada.

A corrente alternada pode ser abreviada como **AC (Alternate Current)**. A corrente contínua pode ser abreviada como **DC (Direct Current)**. Agora você entende a referência no nome da banda Ac/Dc!

Na corrente alternada, o fluxo de elétrons está constantemente mudando de direção, para frente e para trás, enquanto na corrente contínua os elétrons movem-se numa única direção constante.

O gráfico abaixo ilustra isso:

<img src="/img/tutorial_bits_e_bytes/corrente-eletrica-continua-e-alternada.png" class="centered custom-width-600" />

Na corrente alternada, a tensão está variando entre positivo e negativo. Em uma frequência que em alguns países é de 50 Hz e em outros países é de 60 Hz. Não é esta informação que é importante no momento. Mas fica a curiosidade, pois provavelmente você já deve ter ouvido falar nestes termos.

Já na corrente contínua, não há esta variação entre positivo e negativo. A tensão se mantém estável, sendo que em alguns equipamentos esta tensão é de 5 volts, muito comum em dispositivos eletrônicos como celulares e tablets, sendo esta a tensão padrão para USB, ou também 12 volts, muito comum em sistemas automotivos e alimentação de computadores.

Esta informação está bem presente em nossas vidas quando pegamos carregadores e vemos etiquetas informando 5V ou 12V.

## O princípio básico da eletrônica digital

Se eu tenho um fluxo contínuo de eletricidade, eu posso interromper esse fluxo várias vezes e assim gerar pulsos. Dessa forma, passamos a ter dois estados: **Com eletricidade** ou **sem eletricidade**. **Com corrente** ou **sem corrente**.

É disso que surge o conceito de 0 ou 1. 

O 0 é a nomenclatura que damos para o estado de sem nenhuma corrente passando. E 1 é o nome que damos ao estado para quando a corrente está passando.

- 0 - Não há corrente elétrica passando pelo circuito
- 1 - Há corrente elétrica passando pelo circuito

<img src="/img/tutorial_bits_e_bytes/sinal_digital.png" class="centered custom-width-600" />

Imagine que eu tenho uma lanterna e combino com você o seguinte: Se eu piscar duas vezes, estou dizendo "sim". Se eu piscar três vezes, estou dizendo "não". Neste exemplo, a lanterna também tem dois estados: apagado (0) e acesso (1). E através de uma sequência destes estados, nós estabelecemos entre nós um critério de comunicação.

Essa linguagem de sem corrente (0) e com corrente (1) é chamada de **código binário** e é a base para toda a eletrônica digital.

Por exemplo, a sequência **1011** quer dizer, em termos físicos: _Com corrente_ - _Sem corrente_ - _Com corrente_ - _Com corrente_.

<img src="/img/tutorial_bits_e_bytes/sinal_digital1011.png" class="centered custom-width-600" />

É isso que trafega pelas placas de nossos videogames, celulares e computadores. Um fluxo contínuo de corrente que, quando está ativo, atribuímos a nomenclatura de 1 e, quando interrompemos, atribuímos a nomenclatura de 0. Sequências de pulsos de eletricidade.

## Bit - A menor unidade de dados na computação

Cada uma dessas unidades de informação, que já vimos que podem ter o valor de 0 ou o valor de 1, **é o que chamamos de bit**. É a menor unidade de dados na computação.

Se eu falar "1 bit", você deve entender que estou falando em dois possíveis estados: 0 ou 1. Se eu falar "2 bits", você deve entender que estou falando em quatro possíveis estados: 00, 01, 10, 11 (todas as combinações de 0 ou 1 possíveis de se fazer com dois dígitos). E assim por diante...

Uma sequência de 8 bits recebe o nome de byte (repare no "y", pronuncia-se algo como "baite").

Existem algumas razões lógicas para isso, mas, por enquanto, entenda apenas que é uma nomenclatura. Quando falamos em 1 byte, estamos falando de 8 bits. E quando falamos de 8 bits, estamos falando de 8 unidades de informação representadas por 0 ou 1 (sem corrente ou com corrente).

- 1 byte equivale a 8 bits

## Bits e Bytes na vida cotidiana

Agora se prepare, pois tudo na sua vida passará a fazer sentido!

Estamos acostumados, no dia a dia, a chamar mil unidades de alguma coisa de quilo. Por exemplo, mil gramas se torna um quilograma. Cem metros se torna um quilômetro. E assim por diante...

Vamos fazer um pequeno ajuste para o mundo da computação. Aqui, **o "kilo" representa 1024**, ok?

Por exemplo, você tem um pequeno arquivo de texto em seu computador, bem pequenininho, onde o Windows diz que tem o tamanho de 2kb. Esse "b" é de byte, que acabamos de aprender que representa 8 bits. Já o "k" representa "kilo", que vimos que aqui no mundo do computador representa 1024.

Ou seja, um arquivo de 2kb consiste em um arquivo de um arquivo de _2 * 1024 * 8 bits_. O resultado desta conta é 16.384.

Isto significa que esse arquivo de 2kb é uma sequência de **dezesseis mil trezentos e oitenta e quatro sinais de 0 ou 1**!

Agora pensa quando você compra um HD de 500 gigabytes. O giga é a unidade que equivale a 1024 mega. O mega é a unidade que equivale a 1024 kilo. O kilo é a unidade que equivale a 1024.

- 1 gigabyte (GB) = 1.024 megabytes (MB)
- 1 megabyte (MB) = 1.024 kilobytes (KB)
- 1 kilobyte (KB) = 1.024 bytes

Com isso, podemos calcular que 500GB equivale a 536.870.912.000 de bytes. Mas, cada byte equivale a 8 bits, então multiplicamos isso por 8 e temos 4.294.967.296.000 de bits!

Sendo assim, o seu HD ter 500GB de armazenamento significa que ele é capaz de armazenar quatro trilhões duzentos e noventa e quatro bilhões novecentos e sessenta e sete milhões duzentos e noventa e seis mil sinais de 0 (sem corrente) ou 1 (com corrente).

## Programas de computador

Agora você sabe o que é um bit e o que é um byte. Dois termos muito presentes em nossa vida, mas que a maioria das pessoas não faz ideia do que significam em sua essência.

Todos os arquivos e todos os programas do seu computador, inclusive jogos, inclusive os dados presentes em um cartucho, CD, DVD ou Blue-Ray, são isso. **Uma sequência gigantesca de bits, que são sinais de 0 ou 1!**

Os circuitos elétricos têm condições de manipular estes dados em 0 ou 1 e realizar operações com eles, gerando novas sequências de 0 ou 1. É assim que surge tudo o que temos acesso no mundo digital. São cálculos complexos, na ordem de milhões por segundo. Todos utilizando apenas os sinais de 0 ou 1.

Quando escrevemos um programa de computador utilizando linguagens como C, C++, Java, Python, e praticamente todas que você conseguir imaginar, o papel do compilador é justamente pegar este texto (quando programamos, estamos escrevendo um texto, concorda?), que foi escrito utilizando uma destas linguagens, e transformar em código binário, ou seja, transformar em sequência de 0 ou 1.

Você pode, inclusive, ver a sequência de bits de um software usando alguns editores de hexadecimal, ativando o modo binário. Abaixo, você pode ver parte da sequência de bits do jogo Super Mario Bros, de NES:

<img src="/img/tutorial_bits_e_bytes/smb_binary.png" class="centered custom-width-600" />

Mas é só uma parte mesmo. No total, este jogo tem 327.808 bits. O que é pouco, se parar para pensar que, apenas com sinais de 0 ou 1, acontece tudo que você pode ver neste bom e velho jogo.

## Conclusão

Quando os programas, inclusive jogos, estão prontos, eles estão no formato binário. Ou seja, recebemos a sequência de 0 ou 1 que compõe este software. Isso é tudo que temos acesso em um momento inicial. E nosso objetivo é justamente iniciar uma engenharia reversa.

Falando assim, o caminho parece longo e complicado. E vou ser sincero com você, não é das coisas mais fáceis do mundo mesmo. Mas elas ficam mais fáceis na medida que você entende e desenvolve esta base que está sendo ensinada.

O próximo passo é aprender o básico sobre sistemas binários como sistema numérico, justamente para realizarmos alguns destes cálculos que os circuitos eletrônicos digitais fazem.