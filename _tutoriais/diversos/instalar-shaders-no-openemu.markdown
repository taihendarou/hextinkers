---
layout: tutorial
title:  "Instalar novos shaders no OpenEmu"
---

O OpenEmu é um excelente emulador multi-plataformas para macOS. Funciona em um princípio parecido com o RetroArch, utilizando núcleos de outros emuladores para cada plataforma.

Os shaders são uma espécie de filtros para modificar a forma com que a imagem é renderizada na tela, aplicando efeitos visuais. Eles podem ser usados para suavisar bordas, alterar a cor, deixar mais próximo das TVs CRTs e outros ajustes do tipo.

Existe um pacote muito legal de shaders chamado `slang-shaders`. Você pode acessá-lo no Github a seguir: [https://github.com/OpenEmu/slang-shaders](https://github.com/OpenEmu/slang-shaders){:target="_blank"}

Para instalá-lo, siga os seguintes passos:

1- Faça download clicando no botão verde "Code" e selecionando a opção "Download ZIP"

2- Descompacte o arquivo e vá na pasta `shaders`. Você deverá encontrar dentro dela 13 pastas. Cada uma destas pastas, contém um shader.

![slang-shaders](/img/misc/slang-shaders-1.png){:class="centered"}

3- Abra uma nova aba do Finder e vá até a pasta `~/Library/Application Support/OpenEmu`. Para fazer isso, basta utilizar o atalho `CMD + Shift + G` no Finder e colar este caminho.

4- Dentro da pasta que abriu, procure uma pasta chamada `Shaders`. Caso ela não existe, crie uma, exatamente com este nome.

5- Dentro dela, cole aquelas 13 pastas que vieram no pacote que fizemos o download.

Agora abra o OpenEmu e carregue um jogo. No menu inferior, clique na engrenagem e vá em "Selecionar Shader". Você encontrará uma lista com os shaders já previamente instalados e os que acabamos de instalar.

![slang-shaders instalados](/img/misc/slang-shaders.png){:class="centered"}

Eu, particularmente, gosto dos shaders **CRT Caligari** e **CRT Venom Fast**.

