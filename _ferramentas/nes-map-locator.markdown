---
layout: ferramenta
title:  "NES Map Locator"
description: "Converter valor de coordenada cartesiana em hexadecimais para PPU do NES"
---

O NES MAP Locator é uma ferramenta de terminal desenvolvida para realizar conversões da localização de tiles de jogos de NES na tela, entre coordenadas cartesianas e o valor em hexadecimal que deve ser enviado para a PPU.

Por exemplo, suponha que, mexendo nos códigos do jogo, encontramos a sequência de bytes com os valores E8 20. Identificamos que esta sequência se refere à posição de início de impressão de um texto na tela. Sabemos que o NES trabalha no formato little endian. Ou seja, o byte menos significativo vem antes do mais significativo. Isto significa que a posição do tile é 0x20E8.

A ferramenta nos dirá que este valor equivale a (8, 7). Ou seja, tile 8 na horizontal e tile 7 na vertical.

![Image](/img/tool_nesmaplocator/nes_map_locator.png){:class="centered custom-width-600"}

## Instruções de uso

**Conversão de Coordenadas para Hexadecimal:**

- Insira as coordenadas no formato "x, y" ou "x y" (por exemplo, "19, 17" ou "19 17").
- A ferramenta retornará o endereço hexadecimal correspondente na NameTable do NES.

**Conversão de Hexadecimal para Coordenadas:**

- Forneça o endereço hexadecimal desejado (por exemplo, "22 33").
- A ferramenta exibirá as coordenadas cartesianas correspondentes.

## Metodologia de cálculo

**Conversão para hexadecimal**

O programa começa com a base hexadecimal 0x2000 pré-definida, que equivale a 8192 em base decimal.

Ao receber as coordenadas (x, y), o cálculo é realizado da seguinte forma:

	Posição = Base_decimal + x + (y * 32)


Nesta equação, a multiplicação de y por 32 ocorre porque a Name Table do NES tem uma largura de 32 tiles. Ao deslocar verticalmente por uma unidade, estamos, na verdade, deslocando 32 posições horizontalmente. A soma com x ajusta o deslocamento horizontal.

O resultado é então convertido de volta para um formato hexadecimal.

**Conversão de hexadecimal para as coordenadas**

Quando fornecido um endereço hexadecimal, a ferramenta faz o processo inverso. O cálculo é feito subtraindo o endereço hexadecimal fornecido da base predefinida para determinar o "número de passos" (quantidade de tiles) desde o início da Name Table.

Utilizando operações de divisão inteira e módulo, o programa determina as coordenadas cartesianas:

	x = passos % 32
	y = passos // 32


O primeiro cálculo serve para retornar o resto da divisão de "passos" por 32, fornecendo a posição x horizontal. A divisão inteira (//) retorna o quociente inteiro, que nos dá a posição y vertical.

## Download

Faça o download da ferramenta pelos links abaixo:

- Versão para MacOS: [Download pelo Mega](https://mega.nz/file/ArsBEbaD#1p78rwtR2s8p7nLAOnV6bYbg3F4xsvtzaHYNLZNmTHc){:target="_blank"}
- Versão para Windows 64bits: Link em breve
