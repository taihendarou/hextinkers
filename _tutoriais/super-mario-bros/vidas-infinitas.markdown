---
layout: page
title:  "Deixando o Mario com vidas infinitas"
order: 50
---

Esta é uma continuação direta do [tutorial anterior](/tutoriais/super-mario-bros/alterar-numero-de-vidas-iniciais), onde alteramos, em definitivo, o número inicial de vidas que temos ao iniciar o jogo.

Vamos aproveitar o que aprendemos em relação a debugging para fazer um outro tipo de modificação. Agora, faremos com que o número de vidas fique fixo, ou seja, não reduza caso o personagem não venha a morrer no jogo.

Eu vou partir do princípio que você já leu o tutorial anterior. Sendo assim, não vou repetir a explicação de conceitos fundamentais que já foram explicados lá.

Bom, já sabemos que o número de vidas do MARIO fica armazenado no endereço de memória $075a. Sabemos também que esse valor é definido no início da gameplay, que foi onde interferimos no tutorial anterior para alterar o número inicial.

Sabemos também que este número sofre uma alteração quando o Mario morre. É daqui que vamos partir.

Se o número de vidas reduz quando o Mario morre, então certamente há uma rotina no programa que decresce o valor presente em $075a neste evento. Nossa missão é encontrar esta rotina. Para isso, vamos iniciar uma gameplay e ativar um breakpoint de escrita em $075a.

![Image](/img/tutorial_mario_vidas_infinitas/01.png){:class="centered"}

A diferença para o que fizemos no tutorial anterior é que não colocaremos a condicional 'Value == $02'. Desta vez, a interrupção ocorrerá para qualquer novo valor escrito em $075a.

Agora, avançamos na gameplay até morrer. Certamente, em algum momento, a interrupção ocorrerá.

![Image](/img/tutorial_mario_vidas_infinitas/02.png){:class="centered"}

Ocorrendo a interrupção, o debugger abrirá com a seguinte instrução em destaque.

![Image](/img/tutorial_mario_vidas_infinitas/03.png){:class="centered"}

Considerando tudo o que já sabemos e o que esperamos, tudo parece bem sugestivo. Esta instrução está decrescendo o valor do endereço de memória $075a, exatamente o que estávamos procurando.

E para você entender melhor o que tudo isso quer dizer, veja que logo abaixo temos 'BPL $91E9'. A instrução BPL significa "Branch if Positive", indicando que, caso o resultado da operação da instrução anterior seja um valor positivo, ocorrerá um salto na execução do programa para $91E9. Ou seja, este salto só ocorrerá se o Mario ainda tiver vidas suficientes para continuar o jogo. Caso o número de vidas seja negativo, o programa irá "passar reto" pela instrução 'BPL $91E9' e as linhas de baixo serão executadas, sendo elas, provavelmente, relacionadas a preparar o jogo para o game over.

Sendo assim, temos algumas abordagens que poderíamos seguir para implementar nosso hack.

A primeira, e que considero mais simples, consiste em evitar que o decréscimo de vidas ocorra. Para isso, precisamos apenas anular a instrução 'DEC $075A', pois se o valor de $075A nunca decrescer, ficando com seu valor inicial, o número de vidas sempre será positivo e assim 'BPL $075A' sempre será executada (que é o que queremos).

Para fazer isso, vamos substitui-la pela instrução 'NOP'. Esta é uma instrução que, como o nome sugere, não faz nada!

Conforme podemos ver ao passar o mouse em cima da parte do endereço, ao lado da instrução, podemos ver que os opcodes para 'DEC $075A' são CE 5A 07.

![Image](/img/tutorial_mario_vidas_infinitas/04.png){:class="centered"}

'CE' é o opcode para a instrução 'DEC'. Os dois bytes seguintes representam o endereço de memória que estamos decrescendo.

A instrução NOP possui apenas um opcode, 'EA'. Sendo assim, precisamos trocar estes três bytes para 'EA', caso contrário estaremos prejudicando a localização de todas as outras instruções do programa e assim quebraríamos ele inteiro.

O print acima já mostra onde esta instrução está: $11D9 na ROM (PRG). Vamos abrir o Memory Viewer e ir até lá.

![Image](/img/tutorial_mario_vidas_infinitas/05.png){:class="centered"}

Agora, vamos alterar estes três bytes para 'EA', sendo este o opcode para a instrução NOP.

Com isso, anulamos completamente o 'DEC $075A'. Mas, temos uma outra hipótese para considerar... E se a flag N do processador, que é ativada quando o resultado de uma operação matemática é negativo, já estiver ativado vindo das instruções anteriores?

Considerando esta possibilidade, seria interessante garantirmos que a flag N esteja limpa antes de deixarmos o programa entrar na instrução 'BPL $91E9'. Assim, garantiremos que ele entrará nela sempre com um valor positivo.

Isto porque, após fazer o teste, foi exatamente isso que aconteceu. Veja que, mesmo após anularmos o decréscimo do número de vidas, a flag Negative ainda está ativada em função das operações anteriores.

![Image](/img/tutorial_mario_vidas_infinitas/06.png){:class="centered"}

Infelizmente o processador 6502 do NES não possui uma instrução para limpar a flag Negative. Sendo assim, o que faremos agora é mudar a condição para esse salto. Ao invés de saltar caso o número seja positivo (que, na verdade, é caso a flag Negative não esteja ativa), podemos fazer com que o salto ocorra caso a flag Carry não esteja ativada (que aparentemente sempre será o caso).

Para isso, trocamos o 'BPL' por 'BCC', que significa "Branch if Carry Clear".

![Image](/img/tutorial_mario_vidas_infinitas/07.png){:class="centered"}

O opcode atual, para a instrução 'BPL', é $10. Vamos alterar para o opcode da instrução 'BCC', que é $90.

![Image](/img/tutorial_mario_vidas_infinitas/08.png){:class="centered"}

Agora podemos reiniciar o jogo e testar. Verá que o número de vidas sempre ficará travado em 03 e assim o temido game over nunca ocorrerá! Fazendo a alteração pelo próprio Mesen, você pode salvar a ROM alterada e assim ter o MOD em definitivo. Lembrando que o Mesen também permite criar um arquivo de patch IPS que pode ser usado posteriormente para implementar as modificações em uma ROM limpa.

Vamos comparar o programa original com as nossas alterações. Inicialmente, estava da seguinte forma:

	DEC $075A ; Decrescer o valor presente em $075A
	BPL $91E9 ; Salto para $91E9 se flag Negative estiver desativada

E agora ficou:

	NOP ; Não faz nada
	NOP ; Não faz nada
	NOP ; Não faz nada
	BCC $91E9 ; Salto para $91E9 se Carry estiver desativado
	
Pronto, mais uma modificação feita com sucesso, que apesar de simples, acredito que deixa você mais familiarizado com todo o processo.