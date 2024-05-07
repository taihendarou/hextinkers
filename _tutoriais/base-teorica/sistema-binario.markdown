---
layout: page
title:  "Sistema de Numeração Binária"
order: 30
---

Se ao aprender sobre o sistema hexadecimal você compreendeu bem o que queremos dizer com sistemas numéricos, então não terá dificuldades em entender o sistema binário.

No sistema decimal, utilizamos dez algarismos para representar todos os números; no sistema hexadecimal, utilizamos dezesseis algarismos para esse fim. Já no sistema binário, usamos apenas dois algarismos para representar todos os números.

Além disso, se você leu o tutorial anterior, já deve perceber que o sistema numérico binário está totalmente alinhado com o fato de que, na eletrônica digital e na computação, sempre trabalhamos com dois estados: sem energia ou com energia; zero ou um.

Ou seja, no sistema binário, utilizamos apenas os algarismos `0` e `1` para representar todos os números e realizar cálculos.

Veja a tabela:

{:border="1"}
Binário	| Decimal	|	Valor
------- | -------	|	-----
0		|0	|	zero
1		|1	|	um
10		|2	|	dois
11		|3	|	três
100		|4	|	quatro
101		|5	|	cinco
110		|6	|	seis
111		|7	|	sete
1000	|8	|	oito
1001	|9	|	nove
1010	|10	|	dez
1011	|11	|	onze
1100	|12	|	doze
1101	|13	|	treze
1110	|14	|	catorze
1111	|15	|	quinze
10000	|16	|	dezesseis
10001	|17	|	dezessete
10010	|18	|	dezoito
10011	|19	|	dezenove
10100	|20	|	vinte

E assim podemos continuar até o infinito...

Esta é a forma mais precisa e exata de representar bits, mas, obviamente, não é a mais prática, pois os números ficariam gigantescos.

## Relação entre os sistemas binário e hexadecimal

A maneira mais prática de representar bits e bytes é em hexadecimal, pois existe uma relação direta entre o sistema hexadecimal e o binário.

Sabendo que 1 byte equivale a 8 bits, o valor de 1 byte no sistema binário pode variar de `00000000` até `11111111`. Note que são 8 dígitos, cada um representando um bit.

Os algarismos do sistema hexadecimal vão de `0` a `F`. Ao convertermos `F` para o sistema binário, obtemos exatamente `1111`. Ou seja, todos os algarismos do sistema hexadecimal podem ser representados por quatro dígitos binários.

Veja a tabela:

{:border="1"}
Binário	|	Hexadecimal	|	Valor
-----	|	-----		|	-----
0000	|	0	|	zero
0001	|	1	|	um
0010	|	2	|	dois
0011	|	3	|	três
0100	|	4	|	quatro
0101	|	5	|	cinco
0110	|	6	|	seis
0111	|	7	|	sete
1000	|	8	|	oito
1001	|	9	|	nove
1010	|	A	|	dez
1011	|	B	|	onze
1100	|	C	|	doze
1101	|	D	|	treze
1110	|	E	|	catorze
1111	|	F	|	quinze

Sendo o valor de um byte um conjunto de oito dígitos binários, podemos dividi-lo em dois grupos de quatro dígitos e representar cada um desses conjuntos com um algarismo do sistema hexadecimal.

Vamos pegar um byte com um valor aleatório para exemplificar. Pode ser 10100011, o qual dividimos em dois grupos de quatro dígitos para verificar qual é o dígito hexadecimal correspondente:

`1010 = A
0011 = 3`

Ou seja, o byte com valor que, em sistema binário, seria representado por `10100011`, pode ser representado como A3 no sistema hexadecimal. Isso é muito mais simples, prático e visual.

O sistema hexadecimal é perfeito para representar o valor de um byte, pois esse valor sempre pode ser representado por dois dígitos hexadecimais, variando de `00` a `FF`.

Suponhamos que tenhamos uma sequência de 16 bytes de valor aleatório, o que, em termos computacionais, ainda é considerado pouco. Esses 16 bytes, em sistema binário, seriam representados como: `01101101 10100100 11101001 01001011 01100111 01101111 01010000 00010111 01110011 01100111 11010011 01010000 11101110 11111011 10011111 11101111`.

Veja como isso pode começar a ficar complicado. Mas, se convertermos cada um para hexadecimal, teremos: `6D A4 E9 4B 67 6F 50 17 73 67 D3 50 EE FB 9F EF`.

É por isso que, ao manipular bytes (e consequentemente bits), utilizamos o sistema hexadecimal.