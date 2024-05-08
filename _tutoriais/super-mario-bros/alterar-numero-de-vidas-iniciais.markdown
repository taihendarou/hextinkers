---
layout: page
title:  "Alterando o número inicial de vidas do Mario"
order: 40
---

Esta mudança simples será uma oportunidade de se familiarizar melhor com os endereços da memória RAM, dar os primeiros passos no uso do depurador e fazer uma pequena mudança já em Assembly, a famosa linguagem de máquina.

Como o próprio título diz, vamos alterar o número de vidas inicial do Mario, que originalmente é de três.

O número de vidas do jogador é um valor que se altera durante a jogatina. Você pode ganhar ou perder vidas. Então determinada variável pode aumentar ou diminuir. Provavelmente o programa faz uma verificação nessa variável antes de iniciar um jogo, para verificar se devemos avançar para a próxima tela ou se é hora do famigerado GAME OVER. Sendo assim, esse valor está na **memória do processador**, também conhecida como memória RAM.

Nosso primeiro desafio é encontrar o endereço da memória RAM que armazena esse valor. Para chegar lá, precisamos partir do que temos em mãos. Sabemos que o Mario começa com 3 vidas e sabemos em quais circunstâncias esse número aumenta ou diminui. É observando essas variações que vamos encontrar.

Vou utilizar o emulador Mesen. Abrindo o **Memory Viewer** (Visualizador de Memória) e selecionando **CPU Memory** (Memória da CPU) como tipo de memória (seleção em **Memory Type**), conseguimos visualizar a memória RAM.

![Image](/img/tutorial_mario_vidas/mariovidas01.png){:class="centered"}

Poderíamos procurar manualmente aí, mas veja que temos sessenta e cinco mil quinhentos e trinta e seis bytes. Mesmo supondo que esse tipo de informação normalmente está armazenada no começo, não seria prático buscar manualmente.

Então, para isso, usaremos uma ferramenta chamada **Memory Search**. O princípio dessa ferramenta é o mesmo de antigas ferramentas como o [Cheat-O-Matic](https://pt.wikipedia.org/wiki/Cheat_Engine), que usávamos para alterar atributos em jogos como [Elifoot 98](https://pt.wikipedia.org/wiki/Elifoot).

Consiste em filtrar os endereços de memória com determinado valor e depois, em cima desses endereços filtrados, realizar uma nova filtragem com base nos que sofreram a variação que desejamos. O Mesen possui essa ferramenta integrada. Basta acessar **Debug** -> **Memory Search**.

Inicie o jogo na primeira fase, pause a emulação e abra o **Memory Search**. Sabemos que o Mario começa com três vidas, então, na aba **Compare To**, selecione **Specific value** e vamos buscar pelos endereços de memória com o valor 02.

Por que 02 e não 03? Aqui vai um pouco de familiaridade com programação de baixo nível. Eu sei que é mais comum, neste tipo de verificação, o programa verificar se um valor é positivo ou negativo. Então, quando o valor está em 00, ainda temos uma vida.

- 00 - Uma vida 
- 01 - Duas vidas 
- 02 - Três vidas 

Após fazer a busca, teremos filtrados todos os endereços de memória atualmente com o valor 02:

![Image](/img/tutorial_mario_vidas/mariovidas02.png){:class="centered"}

Agora, precisamos mudar a quantidade de vidas que temos. O jeito mais fácil de fazer isso é... morrendo! 💀

![Image](/img/tutorial_mario_vidas/mariovidas03.png){:class="centered"}

Volte ao **Memory Search** e faça uma nova busca. Coloque "01" em **Specific Value** e clique novamente em **Apply Filter**. Agora, teremos todos os endereços de memória que anteriormente tinham o valor de 02 e agora possuem o valor de 01.

![Image](/img/tutorial_mario_vidas/mariovidas04.png){:class="centered"}

Como pode ver no print acima, sobrou apenas um, no endereço **$075a**. Provavelmente, esse é o endereço de memória que armazena a quantidade atual de vidas do Mario.

Vamos testar se é isso mesmo. Abra o **Memory Viewer** (editor hexadecimal do emulador) e, com **CPU Memory** selecionado, vá ao endereço **$075a**.

Chegando lá, vamos alterar o valor para qualquer coisa entre 00 a FF (lembrando que é hexadecimal). Vou experimentar alterar para 08.

Feita a mudança, voltamos ao jogo e morremos de novo, para voltar até a tela que mostra a quantidade de vidas do Mario.

![Image](/img/tutorial_mario_vidas/mariovidas05.png){:class="centered"}

Bingo! É isso mesmo. O valor presente no endereço $075a representa a quantidade de vidas atuais do Mario.

Nosso próximo passo é fazer com que essa mudança seja permanente, no sentido de que, sempre que o jogo iniciar, já começar com essas 8 vidas (ou qualquer outro número que escolhermos).

Para isso, precisamos entender que o programa do jogo, em algum momento durante sua execução, escreverá o valor 02 no endereço de memória $075a. Isso provavelmente será feito durante o início da execução do gameplay.

Para encontrar a instrução que faz isso, usaremos um recurso chamado **Break Point** (ponto de interrupção), que consiste em interromper a execução do programa (e mostrar onde a interrupção ocorreu) quando determinada condição for correspondida.

A condição aqui, no caso, será: "*Escrever o valor 02 no endereço $075a*".

Para isso, vá ao endereço $075a pelo visualizador de memória (**Memory Viewer**, onde estávamos), clique com o botão direito do mouse e selecione **Edit Breakpoint**, conforme imagem abaixo:

![Image](/img/tutorial_mario_vidas/mariovidas06.png){:class="centered"}

Na janela que se abrir, marque que queremos que o breakpoint ocorra durante a escrita (**Write**) e preencha a condição conforme indicado. Estamos exatamente dizendo que queremos interromper a execução quando ocorrer uma escrita do valor 02 no endereço $075a.

![Image](/img/tutorial_mario_vidas/mariovidas07.png){:class="centered"}

Clique em OK e reinicie o jogo (para dar oportunidade ao jogo de escrever 02 no endereço de memória e assim ocorrer a interrupção).

Logo no início, antes de aparecer qualquer coisa na tela, já teremos a interrupção! O depurador do emulador abrirá com a interrupção ocorrendo na seguinte instrução.

![Image](/img/tutorial_mario_vidas/mariovidas08.png){:class="centered"}

Aqui, meu amigo, temos o mais puro assembly do processador 6502. A instrução **STA $075A** é a que está escrevendo o valor $02 neste endereço de memória. Isto porque **STA** é a instrução que escreve o valor presente no registrador A em um endereço de memória específico. E, atualmente, o valor presente nesse registrador é $02.

Também chamamos esse registrador A de **Acumulador**.

Na linha acima, temos a instrução **LDA #$02**. Esta instrução está carregando o valor literal $02 no acumulador. Ou seja, o que o programa faz é:

	LDA #$02 ;; Carrega o valor $02 no Acumulador
	STA $025A ; Escreve o valor atual de A no endereço $025A
	

Então, o que precisamos fazer é alterar essa primeira linha. Mais especificamente, o valor após **LDA**. Temos duas formas de fazer isso. Uma delas é usando o próprio editor de assembly do emulador. Para isso, clique com o botão direito sobre a linha que queremos editar e vá em **Edit selected code**.

![Image](/img/tutorial_mario_vidas/mariovidas09.png){:class="centered"}

Abrirá uma janela com um editor. Do lado esquerdo, poderá editar o código como bem entender. No nosso caso, vamos alterar o #$02 para #$08.

![Image](/img/tutorial_mario_vidas/mariovidas10.png){:class="centered"}

Clique em Apply e pronto, a ROM está alterada (ao menos enquanto estiver aberta). Para tornar a mudança definitiva, você deve, na própria janela do depurador, ir em **File** -> **Save ROM as**. Desta forma, poderá salvar um novo arquivo da ROM com a mudança aplicada.

Outra opção interessante ali disponível é salvar as alterações como um arquivo de[patch do tipo IPS](tutorial_patch_ips.html). Assim, você terá um patch apenas com as modificações que fez neste momento e poderá facilitar o seu controle de versões.

![Image](/img/tutorial_mario_vidas/mariovidas11.png){:class="centered"}

A outra opção para fazer a mudança seria editar diretamente no editor hexadecimal. Para isso, passe o mouse sobre a linha da instrução que queremos alterar. Ali, você verá o endereço da instrução tanto na memória de CPU quanto na ROM (PRG). Anote o endereço da PRG.

![Image](/img/tutorial_mario_vidas/mariovidas12.png){:class="centered"}

Neste caso, é $1069. Vamos até este endereço por um editor hexadecimal qualquer. Porém, o emulador Mesen desconsidera o cabeçalho da ROM. Então, em outros editores hexadecimais, precisaremos somar $10 para chegar ao endereço correto. No caso, então, fica $1079.

![Image](/img/tutorial_mario_vidas/mariovidas13.png){:class="centered"}

Veja que isso nos levou ao valor A9, seguido de 02. O valor A9 é o opcode para a instrução **LDA**. Logo após, temos o operando, que neste caso é 02. Sendo assim, é esse 02 que devemos alterar para modificar o número de vidas inicial do Mario.

Edite o valor e salve uma nova ROM. Lembre-se sempre de manter backups e um bom controle de versões. As chances de estragar tudo ao fazer este tipo de modificação são grandes.

Pronto!

O mais importante, no fim das contas, são os princípios que você aprendeu com este exercício. O processo para encontrar outros valores de atributos do jogo na memória será semelhante, assim como o processo para modificar o valor inicial desse valor também será muito parecido.

Com este conhecimento, você pode começar a criar versões hackeadas de diversos jogos, diminuindo ou aumentando o nível de dificuldade!

![Image](/img/tutorial_mario_vidas/gif_mariojam.gif){:class="centered"}	
