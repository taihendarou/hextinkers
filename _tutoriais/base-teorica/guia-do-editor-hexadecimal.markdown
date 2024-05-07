---
layout: page
title:  "Elementos do Editor Hexadecimal"
order: 40
---

Este é um tutorial para ajudá-lo a se familiarizar com os editores hexadecimais, compreendendo os principais elementos de sua interface e algumas terminologias. A maioria dos exemplos foram retirados do editor embutido no emulador FCEUX. Porém, os princípios são os mesmos para todos os editores, mudando apenas a interface.

## Offset

O offset é o termo utilizado para se referir a um endereço de memória no editor. Está em destaque na barra superior (em outros, em uma barra inferior).

Todo offset aponta para um byte. O endereço de cada byte é representado por um offset.

Repare que na imagem abaixo, selecionamos o byte localizado no offset 0x2086. Este "0x" é apenas uma nomenclatura de hexadecimal, sendo que em outros editores poderia aparecer como `$2086`.

<img src="/img/tutorial_editor_hexadecimal/hex01.png" class="centered">

A primeira linha dos dados representa o último dígito do offset. Repare que, ainda estando no offset `0x2086`, a coluna do `$06` está em destaque (pois o último dígito deste offset é `$06`).

<img src="/img/tutorial_editor_hexadecimal/hex02.png" class="centered">

Já a coluna da extrema esquerda representa os demais dígitos do offset (dezena, centena, milhar, todos...). Repare que todas terminam em `0`. Assim, temos uma espécie de sistema de coordenadas.

<img src="/img/tutorial_editor_hexadecimal/hex03.png" class="centered">

Você pode saltar direto para um offset indo em File -> Go to Address. O atalho neste editor é Ctrl + A, mas em outros editores, como HxD, é Ctrl + L.

## Bits e Bytes

Um editor hexadecimal serve para visualizar e editar bits. Hexadecimal é apenas o sistema numérico melhor utilizado para representá-los de forma amigável.

Um byte equivale a oito bits. Um byte pode ser representado por um número em hexadecimal de dois dígitos, indo de `$00` a `$FF`.

Sendo assim, cada número que você pode visualizar e editar no painel abaixo, equivale a um byte:

<img src="/img/tutorial_editor_hexadecimal/hex04.png" class="centered">

Ou seja, quando você altera um valor, não está correto dizer coisas como "Alterei o hexadecimal". Você alterou o valor de um byte. Hexadecimal é apenas o sistema numérico que estamos usando para representá-lo.

Inclusive, alguns editores permitem visualizar diretamente os bits (cada bit é um sinal de 0 ou 1). Abaixo, um print do editor Hex Fiend:

<img src="/img/tutorial_editor_hexadecimal/hex05.png" class="centered">

Cada `0` ou `1` é um bit. Cada uma destas colunas com 8 bits cada corresponde a um byte.

Repare como é mais confuso trabalhar assim. É melhor visualizar em hexadecimal e, caso queira manipular diretamente os bits, a própria calculadora do Windows pode ajudá-lo nesta conversão.

## Modo texto

A coluna da esquerda do editor representa o modo texto. O modo texto consiste em um caractere de texto associado a um byte. O caractere que corresponde a cada byte varia de jogo para jogo, por isso, para visualizar corretamente, você precisa criar uma tabela.

<img src="/img/tutorial_editor_hexadecimal/hex06.png" class="centered">

No exemplo acima, há uma tabela especificando que o valor de byte `$16` corresponde à letra "M", o valor de byte `$0A` corresponde à letra A, e assim por diante. Por isso, você consegue visualizar algumas palavras do jogo do MARIO na coluna do modo texto.

Caso não haja uma tabela carregada, os editores usam, por padrão, a tabela ASCII. Nem todos os editores tem suporte ao uso de uma tabela personalizada.

Neste editor, a tabela pode ser carregada acessando File -> Load TBL File:

<img src="/img/tutorial_editor_hexadecimal/hex07.png" class="centered">

Lembre-se que o conteúdo da coluna de texto é meramente uma representação em carácter de texto do byte equivalente da outra coluna. Ou seja, nem tudo ali de fato é um texto do jogo. Na verdade, o editor hexadecimal exibirá na coluna de texto tudo que tiver um carácter equivalente associado na tabela. O editor não tem condições de saber se aquilo é de fato um texto do jogo ou não. E, obviamente, nem todo byte se refere a um texto. Temos ali todos os gráficos, todas as linhas de programação e todo o áudio.

## Visualizações

É importante que você garanta sempre estar visualizando os dados corretos. Uma coisa é visualizar os dados da ROM, que normalmente é o que desejamos editar para realizar uma alteração permanente no jogo.

Mas, em editores hexadecimais embutidos nos próprios emuladores, é muito comum a possibilidade de visualizar os dados da memória RAM. E sabemos que estes dados são voláteis e se perderão assim que o jogo for reiniciado. Além de sofrerem atualizações em tempo real na medida que o jogo é executado. Também é possível visualizar os dados do chip de vídeo. Todos estarão nesta mesma visualização em hexadecimal, mas são dados diferentes.

No emulador FCEUX, as visualizações são as seguintes:

<img src="/img/tutorial_editor_hexadecimal/hex08.png" class="centered">

**CPU**: Dados relacionados ao processamento central da emulação. Isso inclui o código de máquina atualmente sendo executado, o estado dos registros da CPU, a pilha de execução, e outras informações cruciais para o funcionamento do jogo.

**PPU**: Dados relacionados à renderização gráfica do jogo. Isso inclui padrões de tiles (pequenos blocos gráficos que compõem imagens maiores), paletas de cores, e o status de sprites (objetos móveis na tela, como personagens e inimigos).

**OAM**: Ao visualizar o OAM, você está vendo uma parte específica da memória utilizada para armazenar informações sobre sprites, como sua posição na tela, qual tile eles estão usando, entre outras propriedades.

**ROM**: Aqui, você está acessando o conteúdo original e inalterável do jogo. Isso inclui todo o código de programação, dados gráficos, músicas, efeitos sonoros, e outros recursos que são parte integrante do jogo.
