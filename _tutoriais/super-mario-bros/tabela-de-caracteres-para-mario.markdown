---
layout: tutorial
title:  "Criando tabela de caracteres"
order: 20
---

Criar uma tabela de caracteres para a ROM que você está traduzindo tem basicamente duas funções. A primeira é melhorar a visualização em editores hexadecimais, facilitando a localização dos textos presentes no jogo.

A segunda função é útil caso você desenvolva ferramentas de "dumper" e "inserter" para automatizar a extração e inserção de textos. Como os dados extraídos estão em formato binário, eles precisam ser convertidos para caracteres equivalentes para permitir a visualização e edição, e depois reconvertidos para binário na hora da inserção.

Curiosamente, essa abordagem é utilizada tanto por iniciantes, para melhor visualização no editor hexadecimal, quanto em situações mais avançadas, que exigem conhecimento de programação para criar um "dumper" e "inserter".

![Image](/img/tutorial_tbl/tbl01.png){:class="centered"}

A imagem acima ilustra como fica a ROM de Super Mario Bros. aberta em um editor hexadecimal após a criação de sua respectiva tabela de caracteres. Note que os textos se tornam legíveis, facilitando a localização.

Este tutorial pode, inclusive, ser considerado uma continuação direta do tutorial introdutório, no qual modificamos o jogo Super Mario Bros., alterando o nome "MARIO" para "PEDRO". Ele é voltado para ensinar os conceitos mais básicos e iniciais do ROM Hacking.

## O que são arquivos .tbl

Os arquivos .tbl, conhecidos como arquivos de tabela, são essencialmente arquivos de texto que indicam aos editores hexadecimais ou a outros programas a correspondência entre valores hexadecimais e caracteres específicos.

Esses arquivos são salvos e manipulados com a extensão .tbl. No entanto, na prática, são apenas arquivos de texto comuns, podendo ser criados e editados em qualquer editor de texto, como Bloco de Notas, Notepad++, Textmate, entre outros.

A título de exemplo, é a tabela que instrui o editor hexadecimal a exibir a letra "M" para o valor $16.

![Image](/img/tutorial_tbl/tbl02.png){:class="centered"}

Se, após o tutorial anterior, o desafio era encontrar palavras como "WORLD", "TIME", "LUIGI", "GAME OVER", entre outras, agora perceba que este problema está resolvido.

## Criando sua primeira tabela

Abra um arquivo em branco com o Bloco de Notas (ou outro editor de texto puro) e salve-o como **mario.tbl** na mesma pasta da ROM. Mantenha o arquivo aberto no editor.

No tutorial anterior, havíamos descoberto os seguintes valores para os caracteres que formam a palavra "MARIO":

	M = $16
	A = $0A
	R = $1B
	I = $12
	O = $18

Vamos colocar estes valores em nossa tabela, mas seguindo a formatação a seguir:

	16=M
	0A=A
	1B=R
	12=I
	18=O

Nota: Faz diferença o uso de letras maiúsculas e minúsculas. Lembre-se que, computacionalmente, "M" é algo completamente diferente de "m".

Agora salve o arquivo.

## Verificando se funcionou

Abra o emulador FCEUX e carregue a ROM. Em seguida, acesse "Debug" e abra o "Hex Editor". No editor que se abrirá, vá em "View" e escolha "ROM" (caso contrário, estará visualizando os dados da memória RAM, da PPU ou de outra fonte).

Agora, selecione "File" e clique em "Load TBL File". Escolha o arquivo **mario.tbl** que acabamos de criar.

Navegue um pouco pelo editor e perceba que, no campo à direita, começaram a aparecer algumas das letras que configuramos. Desça um pouco até encontrar a palavra "MARIO".

![Image](/img/tutorial_tbl/tbl03.png){:class="centered"}

Se preferir, navegue diretamente ao endereço 0x0765, onde está a primeira ocorrência da palavra.

Bom, se estiver como na imagem acima, deu certo! Você tem sua primeira tabela!

## Criando a tabela completa

Agora que confirmamos o funcionamento, podemos criar a tabela completa. Em nosso teste inicial, preenchemos os valores de apenas 5 caracteres. Além disso, é essencial que eles estejam organizados em ordem para facilitar a visualização e edição.

Começaremos descobrindo o valor do primeiro caractere disponível no jogo. Isso pode ser feito acessando os gráficos carregados na PPU, através do menu "PPU Viewer". Já realizamos este procedimento no tutorial anterior para descobrir os valores que compõem os caracteres da palavra "MARIO". Agora, repetiremos o processo, mas desta vez coletaremos os valores de todos os caracteres de texto presentes ali.

![Image](/img/tutorial_tbl/tbl04.png){:class="centered"}

Podemos observar que a sequência começa com os algarismos de 0 a 9, sendo o valor para 0 representado por $00 em hexadecimal. Em seguida, temos o alfabeto de A a Z, todos em letras maiúsculas. Após isso, identificamos quatro tiles que parecem representar espaços em branco, cada um para uma cor de fundo diferente. Logo depois, encontramos um "-", um "x" (sinal de vezes, possivelmente usado em pontuações, tempo, vidas, etc.), um tile que parece ser uma borda e provavelmente não será usado para textos, e, por fim, o sinal de exclamação.

Portanto, são esses os caracteres que mapearemos. Incluiremos também o valor para o espaço em branco, considerando apenas uma cor, e ignoraremos os demais por enquanto.

Agora é hora de reabrir o arquivo .tbl e começar a trabalhar. A configuração ficará da seguinte forma:

	00=0
	01=1
	02=2
	03=3
	04=4
	05=5
	06=6
	07=7
	08=8
	09=9
	0A=A
	0B=B
	0C=C
	0D=D
	0E=E
	0F=F
	10=G
	11=H
	12=I
	13=J
	14=K
	15=L
	16=M
	17=N
	18=O
	19=P
	1A=Q
	1B=R
	1C=S
	1D=T
	1E=U
	1F=V
	20=W
	21=X
	22=Y
	23=Z
	24=
	28=-
	29=×
	2B=!
	CF=©
	

Salve o arquivo e carregue novamente no editor hexadecimal do emulador. Agora você poderá ver mais texto!

![Image](/img/tutorial_tbl/tbl05.png){:class="centered"}

## Cuidado, nem tudo é texto

Quando você abre uma ROM em um editor hexadecimal, está visualizando não apenas o texto, mas 100% da programação do jogo. Isso inclui todos os dados, como gráficos, sons e rotinas. Ao criar uma tabela como esta, você está simplesmente instruindo o editor para substituir determinado valor hexadecimal por um caractere de texto na visualização. No entanto, isso não significa que esse mesmo valor hexadecimal seja sempre utilizado para representar um caractere de texto. Na verdade, isso seria impossível, pois o intervalo hexadecimal vai de $00 a $FF.

Portanto, é completamente normal encontrar sequências que pareçam palavras estranhas ou caracteres aleatórios durante a visualização.

## Editores Hexadecimais com Suporte a Tabelas

Nem todos os editores hexadecimais oferecem suporte para a exibição de tabelas como esta. Na verdade, este é um recurso bastante específico do mundo do ROM Hacking. Existem editores que suportam codificações personalizáveis, mas para isso, é necessário um formato diferente, adaptado às exigências do próprio editor.

Alguns editores que suportam este tipo de tabela incluem:

- WindHex32
- Thingy32
- ImHex
- Hexposure (um dos mais antigos!)

Também é recomendável verificar se o emulador que você está usando possui um editor hexadecimal embutido com suporte a tabelas. Neste tutorial, utilizei o FCEUX, que é ideal para este propósito.

# Cuidado ao Editar Textos

Ao editar textos diretamente no editor hexadecimal, acompanhe sempre os valores hexadecimais, em vez de confiar apenas no que está visualizando em texto. Tenha atenção especial aos valores utilizados para espaços em branco e fim de frase. Inicialmente, mantenha o tamanho original das frases (para alterá-las, é necessário aprender sobre ponteiros).

# Caracteres Ausentes no Jogo

Note que, no jogo Super Mario Bros., não há, por exemplo, um caractere para o ponto de interrogação. Isso significa que você não pode simplesmente usar um ponto de interrogação ao editar o texto. Da mesma forma, letras minúsculas não funcionarão, pois não estão inclusas no jogo. Para utilizá-las, seria necessário outro tipo de edição, mais avançada do que o ensinado neste tutorial específico. O mesmo se aplica à acentuação de palavras.

# Faça Backup e Quebra o Jogo sem Dó!

Não tenha medo de explorar. O aprendizado mais valioso surge ao criar hipóteses e testá-las.

Por exemplo, o que aconteceria se você inserisse uma palavra maior do que a existente no jogo? E se trocar "TIME" por "TEMPO"? Provavelmente algo irá falhar. Mas qual era o valor do byte após a letra "E" em "TIME"? E se colocarmos o mesmo valor após a letra "O" em "TEMPO"? Quais serão as consequências?

Esses questionamentos e experimentos são fundamentais para o aprendizado. Foi assim que todas essas técnicas foram descobertas. Alguém teve que testar, validar hipóteses e quebrar o jogo. Com um backup, você pode explorar sem preocupações.
