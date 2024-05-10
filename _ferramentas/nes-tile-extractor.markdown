---
layout: ferramenta
title:  "NES Tile Extractor"
description: "Extrator de tiles de NES (ou qualquer outro 2bpp) para arquivos externos"
---

O **NES Tile Extractor** é uma ferramenta para extrair gráficos de jogos do NES/Famicom (ou para qualquer sistema que use gráficos 2bpp) e gerar arquivos binários avulsos com eles.

Isto permite que você edite gráficos de forma isolada da ROM, em editores como TileMolester. Depois, pode inseri-la na ROM através de um assembler.

![Image](/img/tool_nestileeditor/ntl4.png){:class="centered custom-width-300"}

O uso é bem intuitivo. Carregue a ROM, escolha o nome e local do arquivo de saída, coloque o offset do primeiro tile e especifique a quantidade de tiles que deseja extrair a partir dele.

## Exemplo

Por exemplo, abaixo temos uma ROM aberta no TileMolester.

![Image](/img/tool_nestileeditor/ntl1.png){:class="centered custom-width-300"}

Repare que nesta região da ROM, estão os gráficos da fonte em japonês. Com o NES Tile Extractor, podemos gerar um arquivo contendo apenas estes tiles isolados, para trabalhar neles e depois reinseri-los na ROM.

Ao extrair estes tiles, geramos um arquivo de nome **fontset_jp.chr**. Agora, podemos abri-lo no TileMolester:

![Image](/img/tool_nestileeditor/ntl2.png){:class="centered custom-width-300"}

Dessa forma, fica muito mais fácil trabalhar, eliminando o risco de acidentalmente danificar a ROM ao alterar regiões indesejadas.

Após concluir a edição neste arquivo, salvei-o com o nome de **fontset_br.chr**, conforme a imagem abaixo:

![Image](/img/tool_nestileeditor/ntl3.png){:class="centered custom-width-300"}

Agora, basta inseri-lo na ROM utilizando um assembler. Neste caso, com o assembler BASS, inseri o comando abaixo no projeto:

	origin 0x2a810
	insert "fontset_br.chr"

O primeiro comando (**origin**) define o offset em que o gráfico será inserido. O segundo comando insere o arquivo propriamente dito.

É importante salientar que o arquivo gerado deve ser aberto em editores de tiles, como o TileMolester, Tile Layer, NES CHR, entre outros.

## Download

Faça o download da ferramenta pelos links abaixo:

- Versão para Windows 64bits: [Download pelo Mega](https://mega.nz/file/d20RBBiL#zYFT5vttXlUv5YoVRHpYOHrAfO2T1HNYvXkpR-g3qtE)
- Versão para MacOS: [Download pelo Mega](https://mega.nz/file/Yv1UXJwC#KBU-fwgTA7fCxWMHcKrGfXTOfjR682lFzPQ8Y1nRkyU)

