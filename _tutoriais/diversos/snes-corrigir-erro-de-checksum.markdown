---
layout: tutorial
title:  "Corrigir erro de 'Bad Checksum' em jogos de SNES"
---

Checksum é um valor calculado a partir de um conjunto de dados para verificar sua integridade. Como o próprio nome diz, "checagem de soma".

O checksum é usado para garantir que o conteúdo do jogo não foi alterado ou corrompido. É feito a partir de um dado já armazenado com um dado calculado a partir dos dados do jogo. Quando há uma mudança nos dados do jogo, o resultado desse cálculo passa a ser diferente e assim passa a ser discrepante com o valor de referência.

Qualquer alteração em uma ROM de SNES, como aplicação de um patch de tradução ou qualquer outra simples modificação, resultará em uma alteração do checksum e fará com que diversos emuladores apresentem a mensagem de erro. Felizmente, na maioria deles, isto não impedirá a execução do jogo.

Para eliminar esse erro, atualizamos o checksum. Existem diversas ferramentas que fazem isso e o algoritmo para SNES já é amplamente conhecimento.

## Ferramentas para recalcular checksum

O **IpsAndSum Snes Tool** é uma ferramenta simples e direta ao ponto para recalcular e atualizar checksum de SNES.

![IPS Check and Sum](/img/tutorial_misc/ips_checkandsum.png){:class="centered"}

[Download do IPS and SUM para SNES](https://mega.nz/file/VzkUGK6I#JB1c_Hl4Da6GrsBUeryOUcoKcgSEfWVfP94eaUPT98E){:target="_blank"}