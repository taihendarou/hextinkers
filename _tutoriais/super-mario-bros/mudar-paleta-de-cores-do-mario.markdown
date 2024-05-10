---
layout: tutorial
title:  "Transformar Mario em Wario mudando as cores"
order: 30
---

Esta será uma lição para introduzir o conceito de paleta de cores. Além disso, será mais um exercício de localização de dados na ROM que desejamos alterar. Nosso objetivo é transformar o Mario, de 'Super Mario Bros' do NES, em Wario. E como faremos isso? Da mesma forma que a Nintendo criou o Luigi: trocando a cor do Mario. Isso mesmo, o Luigi era apenas um 'Mario verde'. Exatamente o mesmo personagem, com a mesma mecânica e as mesmas rotinas de programação, alterando apenas a paleta de cores!

## As cores do NES

Os gráficos do NES não possuem cores por si só; eles são representados por um 'número de cor'. Cada pixel pode ter a cor 0, cor 1, cor 2 ou cor 3, mas estas cores são indefinidas. É por isso que, ao abrir uma ROM em um editor de tiles qualquer, encontram-se gráficos com cores diferentes daquelas que de fato se vê no jogo.

![Image](/img/tutorial_mario_wario/mw01.png){:class="custom-width-300 centered"}

São quatro cores, sendo que, no caso dos sprites, uma delas é uma cor de transparência. Essas cores não estão inicialmente definidas; os dados indicam apenas que são quatro cores. Existe um byte de atributos cujo objetivo é determinar qual paleta de cores será aplicada ao gráfico ao qual esse byte se refere. Uma paleta de cores consiste em um conjunto de quatro cores, ou seja, a cor 0, a cor 1, a cor 2 e a cor 3. São quatro cores dentre as 54 disponíveis no NES.

![Image](/img/tutorial_mario_wario/mw02.png){:class="centered"}

Portanto, o NES tem 54 cores, mas cada gráfico pode usar apenas quatro delas por vez. Não é possível trocar apenas uma cor de um gráfico; é necessário trocar a paleta inteira (conjunto de quatro cores) que está sendo usada para ele.

O NES carrega apenas quatro paletas de uma vez para os tiles e quatro paletas para os sprites. Ou seja, são oito paletas carregadas, totalizando, teoricamente, 32 cores diferentes disponíveis para serem usadas simultaneamente. Na prática, contudo, uma das quatro cores de cada paleta é destinada à transparência. A cor de transparência do sprite deve ser a mesma cor de transparência do tile de fundo. Assim, na prática, de quatro cores por paleta, temos apenas três disponíveis para o design dos elementos na tela.

Portanto, o NES suporta apenas 25 cores diferentes sendo exibidas simultaneamente.

## Visualizando as paletas em uso

Abra o emulador FCEUX e carregue o jogo 'Super Mario Bros'. Navegue em 'Debug' -> 'PPU Viewer'. Na parte inferior da janela que se abrir, você encontrará as oito paletas: a linha de cima mostra as quatro paletas usadas nos tiles de fundo e a linha de baixo, as quatro paletas usadas nos sprites.

![Image](/img/tutorial_mario_wario/mw03.png){:class="custom-width-600 centered"}

Se você jogar um pouco com esta janela aberta, perceberá que as cores de algumas dessas paletas mudam ao longo do jogo. É possível alterar as cores que compõem uma paleta durante o jogo, e é assim que as telas mudam de cor e o Mario se transforma em Luigi.

Essas oito paletas estão carregadas entre os endereços $3F00 a $3F1F da PPU. Observe que são os mesmos valores encontrados na PPU Viewer.

![Image](/img/tutorial_mario_wario/mw04.png){:class="custom-width-600 centered"}

## Encontrando a paleta do Mario

Agora, vamos descobrir qual dessas paletas está sendo usada para colorir o Mario. Embora seja possível encontrar esta resposta apenas olhando e comparando com o personagem, em situações em que duas ou mais paletas iguais estão carregadas, o método 'visual' não será suficiente.

Ainda no emulador, vá em 'Debug' -> 'Sprite Viewer'. Clique em um dos blocos de tiles que se pareça com o Mario e você terá a paleta que está sendo usada para ele, assim como o endereço dessa paleta na PPU.

![Image](/img/tutorial_mario_wario/mw05.png){:class="custom-width-600 centered"}

Ao abrir o editor hexadecimal do emulador, vá em 'View' e escolha 'PPU'. Você verá os bytes da PPU. Vá ao endereço indicado, $3F10, e encontrará exatamente os valores das cores dessa paleta.

![Image](/img/tutorial_mario_wario/mw06.png){:class="custom-width-600 centered"}

## Hora de colorir

Experimente alterar qualquer um desses quatro valores. Faça o teste: coloque qualquer coisa entre $00 e $FF, despause o jogo e veja o carnaval de cores. Você tem várias cores para escolher:

![Image](/img/tutorial_mario_wario/mw02.png){:class="centered"}

Vou trocar a segunda cor de $16 para $38, que é um amarelo semelhante ao do Wario. Também vou trocar a quarta cor de $18 para $03. Note que a cor da roupa do Mario é a mesma do cabelo e do bigode, então, se escolhermos um rosa próximo à cor da roupa do Wario, o personagem ficará com cabelo e bigode rosa. Por isso, escolhi o $03, que é um roxo escuro, para que o cabelo e o bigode mantenham destaque.

![Image](/img/tutorial_mario_wario/mw07.png){:class="centered"}

Acha que parece com o Wario? É o que dá para fazer com o NES em termos de cores.

![Image](/img/tutorial_mario_wario/mw08.png){:class="custom-width-300 centered"}

Lembre-se também que, naquela época, a cor do macacão do Mario (e do Luigi) era invertida em relação à de hoje. O macacão era vermelho, enquanto hoje é azul (e a cor da roupa é vermelha).

![Image](/img/tutorial_mario_wario/mw09.png){:class="centered"}

## Tornando a mudança definitiva

Se você leu o tutorial em que mudamos o nome de 'MARIO' para 'PEDRO', lembrará que alterar valores na PPU não muda os valores na ROM propriamente dita. Seria como colorir com lápis uma folha impressa em uma impressora preto e branco: a impressora continuaria sendo preto e branco. Precisamos depurar a ROM para encontrar onde estão os valores usados para escrever na PPU. Como primeira abordagem, podemos usar a força bruta. Pegue os valores originais da paleta do Mario: 22 16 27 18, abra a ROM no editor hexadecimal, use Ctrl + F para localizar e busque por esses valores.

Encontramos duas ocorrências desta sequência, uma em $0CC7 e outra em $05E7. Vamos testar a primeira, alterando o segundo valor de $16 para $38, conforme combinamos. Salve e recarregue a ROM (lembre-se de ter um backup da original).

![Image](/img/tutorial_mario_wario/mw10.png){:class="centered"}

Bingo, era isso mesmo! Mude as outras cores como desejar e pronto, a hack está pronta!

![Image](/img/tutorial_mario_wario/mw11.png){:class="centered"}

Mas não pare por aqui. Sabemos que esta simples mudança não é o objetivo final de um rom hacker, mas sim uma etapa para fins didáticos, com o objetivo de aprender os conceitos básicos.

Agora é com você continuar testando e explorando o jogo. Que tal tentar alterar a paleta do Luigi? Ou localizar a paleta referente ao Mario com o power-up de flor de fogo? Que tal alterar as cores dos Goombas e das tartarugas?

Além disso, por que encontramos duas ocorrências da sequência de bytes dessa paleta? O que acontece se alterar a outra? Há alguma mudança visível?

Estas e outras perguntas você deve começar a se fazer. A essência do hacking é questionar, levantar hipóteses, testar, quebrar e consertar para, no fim, aprender.

Espero que tenha gostado do tutorial e aprendido algo novo!

![Image](/img/tutorial_mario_wario/MarioCharactersWave.gif){:class="centered"}

PS: Pensando bem, a roupa roxa e o fato de não ser tão gordinho acabou lembrando até mais o Waluigi do que o Wario.
