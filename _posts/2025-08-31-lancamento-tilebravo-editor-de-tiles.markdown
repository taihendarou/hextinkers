---
layout: post
title:  "TileBravo: editor de tiles direto no navegador"
date:   2025-08-31 00:00:00 -0300
---

Acabei de liberar a primeira versão pública do **TileBravo**, um editor de tiles que roda direto no navegador, sem necessidade de instalação.

A proposta é ser uma ferramenta que possa complementar ou substituir editores clássicos como **TileMolester, YY-CHR e Crystal Tile**. Uma interface rápida, intuitiva, com muitos atalhos de teclado para facilitar.

![TileBravo Screenshot](/img/tool_tilebravo/tilebravo-1.png){:style="width:70%; display:block; margin:auto;"}

Por enquanto, suporta os seguintes formatos de imagem:

- 2bpp planar  
- 4bpp planar  
- 2bpp planar composite  
- 4bpp chunky zip16 (formato estranho presente em alguns gráficos do *Yu Yu Hakusho Final* que estou traduzindo)

Na próxima atualização, já trarei todos os codecs presentes no **Tile Molester**.

As paletas usam um formato simples em **JSON**. Você pode ajustar uma paleta, exportar o arquivo e reutilizar depois em outra sessão. Ainda não há suporte para importar paletas de emuladores, mas isso já está no roadmap.

Um uso interessante é o seguinte: abrir o gráfico desejado, ajustar a paleta, exportar como **PNG**, editar esse PNG no Photoshop ou em outro editor tradicional, importar de volta o PNG editado no TileBravo e então salvar no formato binário para usar na ROM. Mas pode editar os pixels direto no **TileBravo** mesmo.

- [Link público para utilizar](https://tilebravo.hextinkers.org)
- [GitHub do projeto](https://github.com/taihendarou/tilebravo)

### História do projeto

Apenas um desafio pessoal e estudos. Aproveitei a oportunidade para estudar **React.js** ao mesmo tempo que busquei implementar coisas que me incomodam em outros editores. Pretendo evoluir a ferramenta conforme surge necessidade em meu próprio uso e uso dos colegas.

Plano futuro é ter um editor de **tilemap** embutido.

Espero que possa ajudar.
