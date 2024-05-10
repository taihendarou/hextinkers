---
layout: tutorial
title:  "Como mudar o nome do Mario"
order: 10
---

Este é um tutorial mostrando o passo a passo para fazer um hack bem simples no clássico Super Mario Bros, do NES. Para você, iniciante no assunto, este tutorial visa a ensinar alguns conceitos fundamentais e ajudar a começar a se aventurar neste universo. Nossa missão: Mudar o nome de **MARIO** para **PEDRO**, no canto superior esquerdo da tela!

![Image](/img/tutorial_primeira_romhack/primeiraromhack01.png){:class="centered"}

# Ferramentas

Tudo o que precisamos é de um emulador com recursos de debugging. Aqui, usaremos o [**FCEUX**](https://fceux.com/web/home.html). Ele é tudo o que precisamos para fazer esta alteração. As ferramentas de debugging presentes em emuladores servem para analisar os jogos a fundo. Com elas, podemos acompanhar as instruções executadas pelo processador, visualizar a manipulação dos gráficos e os dados presentes na memória RAM, entre outras coisas.

# Análise da Pattern Table

Engenharia reversa consiste em partir do resultado final e encontrar o processo que levou até ele. Temos que começar a partir das informações que já temos. É a partir deste pensamento que começaremos o processo.

Abra o jogo no emulador. O que temos em mãos? A tela. Imagine que é a tela da TV que está ligada ao videogame (o emulador só está simulando isso). Então a primeira pergunta é: Quem manda a imagem para a TV? No caso do NES, é um chip chamado PPU: Picture Processing Unit. Literalmente: Unidade de Processamento de Imagem. Então faça o seguinte: Abra o emulador FCEUX, abra o jogo do Mario, vá ao menu Debug e clique em PPU Viewer.

![Image](/img/tutorial_primeira_romhack/primeiraromhack02.png){:class="centered"}

Aqui estão todos os gráficos que o processador enviou para a PPU no momento atual do jogo. Cada um destes bloquinhos, chamados de tile, tem 8 pixels de largura por 8 pixels de altura (8x8). Apesar de estar tudo embaralhado, você pode ver aí todos os elementos presentes na tela do jogo no momento. Todas as poses do Mario, os elementos que formam o cenário e também a fonte.

O nome desses dois conjuntos de tiles é **Pattern Table** (tabela de padrões). O NES tem duas, a Pattern Table 0 e a Pattern Table 1.

Veja que na parte superior da tabela da direita, encontramos tiles referentes a letras e números. Além disso, sempre que você clicar em um tile, poderá ver um valor.

Por exemplo, o gráfico da letra M está mapeado no tile $16. Estes valores estão em [hexadecimal](tutorial_hexadecimal.html) e vão de $00 a $FF.

![Image](/img/tutorial_primeira_romhack/primeiraromhack03.png){:class="centered"}

Agora, vamos anotar os valores dos tiles que formam a palavra MARIO.

<pre>M = $16
A = $0A
R = $1B
I = $12
O = $18</pre>

Vamos já adiantar nossa vida e anotar os valores para formar a palavra que queremos colocar no lugar. No caso, PEDRO.

<pre>P = $19
E = $0E
D = $0D
R = $1B
O = $18</pre>


Certo, podemos fechar a PPU Viewer por enquanto.

# Análise da Name Table

No PPU Viewer, encontramos todos os gráficos que estão carregados no processador de vídeo. Agora, acessaremos uma outra tabela, que é responsável por dizer como estes tiles são organizados e alinhados na tela. Esta é a função da **Name Table**. Na janela principal do emulador, clique em Debug e acesse Name Table Viewer.

![Image](/img/tutorial_primeira_romhack/primeiraromhack04.png){:class="centered"}

Basicamente o que temos aí é tudo que está sendo exibido no jogo no momento, com exceção dos sprites. No NES, temos duas camadas de gráfico: Os backgrounds e os sprites. Não vamos entrar em detalhes quanto a isso agora, mas, de forma resumida, normalmente são considerados sprites os elementos que se movem, como personagens, tiros e inimigos, e como background as coisas que compõem o cenário, como o chão, nuvens, montanhas e plataformas.

Na Name Table Viewer, você pode clicar nos tiles que a compõe e ver informações sobre ele. Na imagem acima, eu cliquei no "M" do "MARIO" do canto superior esquerdo. Veja que, em Tile Info, temos um campo chamado "Tile Index", com o mesmo valor de $16 que coletamos ali atrás. Além disso, o primeiro campo se chama "PPU Addr", que representa o endereço na PPU dessa região que clicamos. Ou seja, o que estes dados estão nos dizendo é que, no endereço $2043 da PPU, o jogo está exibindo o tile $16.

Ainda com o tile do "M" selecionado, clique nele com o botão direito e acesse a opção conforme imagem abaixo:

![Image](/img/tutorial_primeira_romhack/primeiraromhack05.png){:class="centered"}

O emulador abrirá um editor hexadecimal diretamente no endereço $2043 da PPU.

![Image](/img/tutorial_primeira_romhack/primeiraromhack06.png){:class="centered"}

Em teoria, estamos vendo exatamente a mesma coisa que estávamos na Name Table Viewer, só que sem uma interface gráfica mostrando os tiles. Mas é a mesma coisa, veja, no endereço $2043, temos o valor $16, que equivale ao tile da letra "M". Repare que logo após ele temos **0A, 1B, 12 e 18**, que são os valores que anotamos para as outras letras que formam a palavra "MARIO"!

# Alterando dados direto na PPU

Agora é só trocar esses valores pelos valores dos tiles que quero colocar no lugar? Bom, vamos fazer isso e despausar a emulação (caso esteja pausada).

![Image](/img/tutorial_primeira_romhack/primeiraromhack07.png){:class="centered"}

Pronto? O MARIO virou PEDRO?

Não exatamente. Nós apenas alteramos o valor diretamente na "placa de vídeo" do console. Assim que o processador enviar dados atualizados para a PPU, esta mudança será desfeita.

É como se você tivesse uma impressora branco e preto, imprimisse uma imagem e colorisse com o lápis. A imagem ficará colorida, mas isso não fará com que a impressora passe a ser colorida. Foi isso que nós fizemos.

Para que nossa mudança seja definitiva, o que nós precisamos é encontrar qual parte do programa da ROM escreve estes dados na PPU, para assim alterar estes dados diretamente na ROM. Aí sim o processador passará a escrever PEDRO em definitivo.

Mas de qualquer forma é legal ver que mudamos alguns números e isso gerou uma mudança no que vemos, não é? Estas mudanças diretamente na PPU são sim úteis, tanto para aprendizado, quanto para visualizarmos o que queremos e depois aplicar mudanças em definitivo.

# Encontrar os valores na ROM

Bom, temos uma sequência de valores que representam a palavra Mario. E agora, o que fazemos? Bom, o nosso instinto hacker manda procurar por essa sequência de valores diretamente na ROM, através do editor hexadecimal. Esse é nosso trabalho, considerar todas as possibilidades e hipóteses possíveis até descobrir a informação que queremos.

Então, vamos lá: abrir a ROM e procurar pela sequência **$16 $0A $1B $12 $18** (o uso do "$", aqui, refere-se apenas a notação hexadecimal). Podemos usar o próprio editor do emulador, acessando Debug e HEX Editor. Apenas lembre-se de ir em View e selecionar ROM, para que você veja os dados da ROM e não dados voláteis como da memória RAM ou da PPU.

![Image](/img/tutorial_primeira_romhack/primeiraromhack08.png){:class="centered"}

Agora Ctrl + F para abrir a janela de procurar, cole o valor que temos e busque.

![Image](/img/tutorial_primeira_romhack/primeiraromhack09.png){:class="centered"}

Bingo! Em meio ao aparente caos, encontramos uma ocorrência para esta sequência.

E agora? Bom, agora tem que dar uma coceira na mão para alterar estes valores e ver o que acontece na ROM. Algumas vezes, isto estragará o jogo, por isso é importante sempre manter backups e fazer mudanças aos poucos.

Vamos experimentar alterar de 16 para 19, recarregar a ROM e ver o que acontece.

![Image](/img/tutorial_primeira_romhack/primeiraromhack10.png){:class="centered"}

Parece que deu certo! Podemos agora alterar os demais valores, conforme testamos anteriormente, recarregar a ROM para conferir se deu certo.

![Image](/img/tutorial_primeira_romhack/primeiraromhack11.png){:class="centered"}

Agora você pode ir em File -> Save ROM As, salvar com um novo nome e pronto, você tem a sua primeira ROM hackeada! Você mudou o nome de MARIO para PEDRO, no canto superior esquerdo da tela!

"É só isso mesmo?"

Sim, nesse caso, é só isso mesmo. Encontramos tudo o que precisávamos para esta efetuar esta alteração!

# Ponderações finais

Não existe garantia nenhuma que teríamos encontrado esta sequência de valores ao fazer um CTRL-F na ROM. Pode ser que os valores que representam as letras na PPU sejam produzidos pelo programa através de cálculos a partir de outros valores. Deu a calhar que neste caso, deu certo. Então, claro, fique atento que cada caso é um caso, e à medida que você acumula conhecimento, você conseguirá fazer as análises para encontrar os dados que precisa

Além disso, se você continuar procurando, encontrará outras ocorrências desta mesma sequência de valores. É bem provável que também sejam a palavra Mario sendo utilizadas em outros textos e áreas do jogo. Foi uma coincidência logo o primeiro ser aquele que procurávamos. Na prática, você fará os testes. Por isso que eu recomendo alterar apenas um valor e ver o que aconteceu. Se não é o que você queria, volte para o valor original e só mude aquilo que você tem condições de conferir na prática o efeito causado no jogo.

Por fim, este é um tutorial para iniciantes. Por isso, não entramos em algumas estratégias mais avançadas, das quais considero necessário que você já tenha certa experiência ou conhecimento básico acumulado para executar. Então, são assuntos que ficariam para outros tutoriais. Mas, para já te dar uma abertura, utilizando o recurso de Debugger e estabelecendo breakpoints, ou seja, pontos de interrupção, é possível chegar aos valores que queremos sem a necessidade de fazer essa busca com o CTRL-F, mas também sem o risco de chegar em dados diferentes daqueles que buscamos. Além de esta ser a metodologia para quando os valores presentes na ROM não coincidirem com os valores atribuídos aos tiles presentes na PPU.

# Faça mais testes!

Um dos motivos de terem tão poucos tutoriais tão detalhados e passo a passo sobre ROM Hacking disponíveis é justamente por causa do perfil de um ROM Hacker. Normalmente é uma curiosidade aguçada, onde a partir de uma informação descoberta já ficamos curiosos para descobrir mais sobre aquilo, fazendo alterações e testes. Por isso, eu mesmo percebi que boa parte do conhecimento acumulado não vem do estudo de tutoriais, mas sim da tentativa de realizar mudanças e explorar, e aí sim buscar respostas para pontos técnicos específicos que surgiram pelo caminho.

Então, se você gostou deste processo, fica o desafio. Quando este jogo está no modo de dois jogadores e é a vez do segundo jogador, temos o nome do "LUIGI" no lugar do "MARIO". Tente alterar o nome do "LUIGI" para "CARLOS", seguindo o mesmo processo.

Tente também alterar a palavra "WORLD" para "MUNDO".

Depois, experimente também alterar a palavra "TIME" para "TEMPO". Aqui, será a primeira vez em que o número de caracteres será diferente ("TIME" tem quatro caracteres, enquanto "TEMPO" tem cinco!). Não tenha medo, vá alterando e fuçando, pois as descobertas disso é que trarão aprendizado. Faça sempre backup, pois é comum estragar a ROM durante o processo!

