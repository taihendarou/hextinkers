---
layout: tutorial
title:  "Introdução à compressão de dados"
---

Compressão é provavelmente o tema que mais trava projetos de tradução de jogos, principalmente os mais antigos. De fato, para enfrentar as compressões, é necessária uma soma de conhecimentos em várias áreas: fundamentos das próprias técnicas de compressão, operações bitwise, debugging, linguagem de máquina do sistema em questão, uma linguagem de alto nível para criar ferramentas e, além de tudo isso, tempo e perseverança.  

Ou seja, é um assunto bastante interdisciplinar. Por isso, não é simples aprender tudo em um único tutorial prático.  

Você precisa ir acumulando conhecimento e prática nessas áreas aos poucos, até que tudo comece a convergir e fazer sentido. Além do mais, compressão de dados é, por si só, uma área de estudo muito profunda, com pessoas especialistas apenas nisso.  

Aqui neste tutorial quero te dar um ponto de partida no tema, para que você comece a entender como as coisas funcionam e possa se sentir mais encorajado a explorar dados comprimidos em seus projetos de *rom hacking*.

Leia com atenção, absorva cada conceito e, acima de tudo, **não subestime o básico**.

## Um exemplo lúdico: Atribuindo referências

Imagine a seguinte frase:

<pre>ABRACADABRA PÉ DE CABRA!</pre>

Como pode ver, esta frase possui 24 carácteres (o espaço em branco deve ser considerado).

Podemos notar um padrão que se repete: ABRA

<pre><u>ABRA</u>CAD<u>ABRA</u> PÉ DE C<u>ABRA</u>!</pre>

E se criássemos uma espécie de dicionário de padrões?

1. ABRA

Ao escrever a frase, ao invés de repetir "ABRA" toda vez que essa sequência aparecer, nosso programa poderia ser capaz de entender a seguinte lógica: <strong>Abra o dicionário e coloque o padrão 1.</strong>

Para isso, o programa precisa saber que é hora de consultar o dicionário. Suponha que deixemos definido o caractere ^ como indicação de busca no dicionário.

Agora, nossa brase poderia ser:

<pre><strong>^1</strong>CAD<strong>^1</strong> PÉ DE C<strong>^1</strong>!</pre>

Veja que agora a frase possui 18 caracteres, **uma economia de 25% na quantidade de dados**!

Ao invés de repetir por três vezes a sequência ABRA de forma **literal**, nós a "cadastramos" em uma tabela e substituímos por uma **referência** que pode ser acessada usando apenas dois caracteres (o caractere de controle ^ e o índice 1).

Trocamos quatro por dois.

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td>ABRACADABRA PÉ DE CABRA!</td>
    <td>24 caracteres</td>
  </tr>
  <tr>
    <td>^1CAD^1 PÉ DE C^1!</td>
    <td>18 caracteres</td>
  </tr>
</table>


Este é um princípio básico de compressão presente na maioria dos métodos: **Substituir dados literais por referências.**

Agora, veja que, para fazer isso acontecer, precisamos escrever um programa que faça essa busca na tabela de referências.

Então, como o programa saberia quando deve pegar algo do dicionário e quando deve apenas copiar o caractere literal? Ele precisa de uma lógica clara.

<pre>para cada caractere em TEXTO:
    se caractere == '^':
        indice = próximo_caractere()
        padrão = DICIONARIO[indice]
        adicionar_saida(padrão)
    senão:
        adicionar_saida(caractere)</pre>

Ou seja, o caractere ^ funciona como uma espécie de "sinal de trânsito", que muda o comportamento da leitura. Sem esse sinal, o programa nunca saberia diferenciar um texto literal de uma referência.

Além disso, precisamos do próprio dicionário.

Tanto estas linhas de programação quanto o próprio dicionário consomem bytes.

Chamamos estes bytes de **custo da compressão**. Obviamente já podemos ver que não vale a pena fazer uma única frase. Gastamos mais bytes para escrever a rotina e armazenar o dicionário do que a economia de 6 caracteres que tivemos nessa frase. Porém, imagine todo o texto de um longo RPG da Square para Super Nintendo. A economia é superior ao custo e assim um espaço considerável é economizado no cartucho.

A economia de dados com a compressão deve ser superior ao custo da compressão, para que esta valha a pena.

Existe um outro fator que entra no custo da compressão: **O trabalho a mais que o processador terá para executar essa rotina de consulta (descompressão)**. Nos tempos antigos, na época do Nintendinho, Mega Drive e Game Boy, tudo isso deveria ser levado em conta. Uma economia de espaço ao custo de mais processamento.

Vale a pena esse processamento extra? Ele prejudicará outros aspectos da jogabilidade ou até mesmo do consumo de energia? Tudo isso era levado em conta pelos grandes desenvolvedores dessa época áurea.

Portanto, toda compressão tem dois lados: a economia de espaço e o custo (bytes extras e esforço do processador). Sempre que a economia supera o custo, a compressão compensa.

## DTE e MTE

O fundamento por trás do exemplo que acabamos de ver é o mesmo usado em técnicas clássicas de compressão conhecidas como **DTE** e **MTE**, muito populares no início do rom hacking, quando gringos traduziam jogos do japonês para o inglês.  

O problema era simples: em japonês, dá para dizer muito com poucos caracteres. Já em inglês — e em português ainda mais — a mesma ideia exige muito mais espaço. Nos cartuchos de 8 e 16 bits, com memória bem limitada, isso se tornava um grande desafio. A saída era comprimir o texto para caber no espaço originalmente pensado para o japonês.  

- **DTE (Dual Tile Encoding):** um único byte representa dois caracteres.  
- **MTE (Multiple Tile Encoding):** um único byte pode representar uma sequência maior (não só pares, como no DTE).  

O exemplo lúdico do “ABRA” é, na prática, uma forma simplificada de **MTE**. No fim, tudo se resume a substituir sequências de dados por referências.  

Esse foi exatamente o desafio que enfrentei ao traduzir o jogo de NES [Dragon Ball Z Kyoushuu Saiyajin](/traducoes/nes-dbz-kyoushuu-saiyajin.html), que adaptei para **Dragon Ball Z Invasão Sayajin**. O espaço para texto era muito pequeno, já que tudo estava em japonês. Então programei uma rotina de descompressão e criei um dicionário com os pares de caracteres mais comuns. Isso reduziu em cerca de **40%** o tamanho do texto em português, tornando possível aproveitá-lo dentro da ROM.  

Este tutorial é mais conceitual, elementar e lúdico. A ideia é que você entenda os fundamentos antes de mergulhar na prática. Por isso, não vou detalhar agora as especificações técnicas de DTE e MTE. Esse momento vai chegar, ou talvez você mesmo consiga deduzir. Eu, por exemplo, muitas vezes deduzo o funcionamento de compressões porque tenho os fundamentos bem claros. E são esses fundamentos que quero ensinar aqui. 

## Segundo exemplo lúdico: Compressão por Repetição

Vamos para mais um exemplo lúdico para que você aprenda outro padrão de compressão.

Em determinado jogo, temos a seguinte frase:

<pre>AAAAAAAAAHHHHHHHH SEU MALDITO!</pre>

Repare que o "A" se repete por 9 vezes e depois o "H" se repete por 8 vezes. Dessa forma, nossa frase possui 30 caracteres.

E se definíssemos uma lógica para isso? De modo que o programa entenda que "É hora de repetir o próximo caractere por X vezes". Assim, teríamos uma economia de dados.

Suponha que definimos o caractere ```*``` como indicação para o programa que é hora de repetir. Logo após o ```*```, definimos que apresentaremos o número de repetições desejada. Em seguida, o caractere em si.

Dessa forma, *9A gerará **AAAAAAAAA**, enquanto *8H gerará **HHHHHHHH**.

Agora, nossa frase fica:

<pre>*10A*8H SEU MALDITO!</pre>

**Agora, a frase possui apenas 20 caracteres, uma economia de 33%!**

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td>AAAAAAAAAHHHHHHHH SEU MALDITO!</td>
    <td>30 caracteres</td>
  </tr>
  <tr>
    <td>*10A*8H SEU MALDITO!</td>
    <td>20 caracteres</td>
  </tr>
</table>

Obviamente, precisamos também de uma rotina capaz de entender esse padrão e realizar a descompressão. Essa rotina deverá fazer algo como:

- Se o programa encontra *, ele sabe que deve entrar na rotina de repetição.
- Em seguida, lê o número (quantas vezes repetir).
- Depois lê o símbolo que deve ser repetido.
- E finalmente escreve na saída o símbolo repetido N vezes.
- Se não encontrar *, apenas copia o caractere literal.

Para escrever essa rotina, também teremos um custo.

Esse exemplo consiste exatamente no método de compressão chamado de **Run-Lenght Encoding (RLE)**. Essa técnica é muito usada em jogos 2D, principalmente na construção de janelas e interfaces, onde as bordas e fundos se repetem com muita frequência.

## A técnica do desvio

Em muitos projetos de tradução de ROMs, principalmente do japonês para o inglês (e depois para o português, usando essas versões como base), você vai ouvir falar sobre a técnica do desvio.

Ela era muito usada por ROM hackers que não conseguiam entender ou recriar o algoritmo de compressão do jogo, mas tinham conhecimento suficiente de assembly para contornar o problema. O raciocínio é o seguinte:

1. O jogo carrega e descomprime um bloco de dados.

2. Esses dados descomprimidos ficam disponíveis na memória de vídeo (VRAM).

3. O hacker copia esses mesmos dados já descomprimidos, coloca em outra região da ROM (caso haja espaço) e edita ali o que precisa.

4. Depois, escreve uma rotina em assembly que, logo após o jogo terminar a descompressão normal, desvia para essa nova região e sobrescreve os gráficos com a versão modificada.

Na prática, isso evita ter que entender o algoritmo de compressão e, principalmente, evita ter que programar um compressor em C++ ou Python para gerar os dados no formato exato que o jogo espera. Essa técnica economiza muito tempo, mas tem um preço: gasta mais espaço na ROM. Por isso, não dá para aplicar em todos os gráficos.

Ainda assim, como normalmente são poucos os gráficos que precisam de edição para tradução, se houver espaço livre na ROM (ou se for possível expandi-la), o desvio pode ser uma solução bastante prática.

## Pseudo-compressão

Quero explicar rapidamente uma técnica que eu utilizo muito quando preciso fazer um ajuste rápido em um jogo, ou até dar uma ajuda para alguém que está prestes a finalizar um projeto mas encontrou alguns gráficos comprimidos e não consegue, por exemplo, colocar uma acentuação ou traduzir um texto que está em forma de imagem. Essa técnica é a pseudocompressão.

Em muitos jogos antigos, principalmente no Super Nintendo, praticamente todos os gráficos estão comprimidos. Isso significa que todo bloco de dados passa por uma rotina de descompressão antes de aparecer na tela. E aí vem a grande sacada: e se eu pegar um bloco de dados sem compressão nenhuma, mas adicionar nele os bytes de controle necessários para que a rotina de descompressão consiga processá-lo sem falhar? O resultado final será o gráfico descomprimido que eu editei.

É importante entender: eu não posso simplesmente colocar o gráfico descomprimido direto na ROM. A rotina de descompressão vai estragar o dado, porque ela espera encontrar ali não só os gráficos, mas também os bytes de controle. A pseudocompressão, portanto, consiste em preparar um bloco aparentemente “comprimido”, mas que na prática contém os gráficos já descomprimidos junto com os bytes de controle que permitem que ele passe pela rotina sem problemas.

O efeito disso é o inverso da compressão real: os dados ficam maiores. Afinal, temos os gráficos descomprimidos mais os bytes de controle. Em outras palavras, estamos colocando um arquivo maior para gerar na saída um arquivo menor. Mas como normalmente essa técnica é usada em poucos gráficos — por exemplo, para adicionar caracteres acentuados ou trocar uma plaquinha de “OPEN” para “ABERTO” — o aumento de espaço não chega a prejudicar a performance nem a inviabilizar o projeto. Claro que seria impossível aplicar essa técnica em todos os gráficos de um jogo inteiro.

E por que usar pseudocompressão ao invés de comprimir de fato? A resposta é simples: **programar um compressor é muito mais demorado e complexo do que entender a rotina de descompressão que já existe no jogo**.

A ROM já vem com instruções prontas para descomprimir dados. Mas os dados foram originalmente comprimidos por ferramentas internas dos desenvolvedores, que nem sempre temos acesso. Fazer engenharia reversa disso e recriar um compressor compatível não é impossível, mas exige muito tempo e dedicação.

Eu mesmo já passei por isso. Junto com o colega vervalkon, desenvolvemos uma ferramenta de compressão para a tradução do jogo [Yu Yu Hakusho 2: Kakuto no Sho](/traducoes/snes-yu-yu-hakusho-kakutou-no-shou.html) de Super Nintendo. Ela funcionou bem, mas não conseguiu atingir o mesmo nível de compressão do jogo original — ainda assim, foi suficiente para que os textos editados coubessem na ROM. Chegou próximo.

Já no caso do [Alcahest](/traducoes/snes-alcahest.html), eu até criei um compressor próprio, mas com taxa de compressão bem inferior à original. E não é por acaso: esse jogo foi dirigido por ninguém menos que Satoru Iwata, ex-presidente da Nintendo e um verdadeiro mestre em compressão de dados. A compressão do Alcahest é uma obra-prima de engenharia de software. Foi um prazer estudá-la e fazer debugging, principalmente sabendo que veio da mente de alguém tão lendário na área. Mas tentar atingir o mesmo nível de precisão não fazia sentido prático para o projeto. Eu queria traduzir o jogo, não gastar meses replicando um compressor tão avançado. No fim, mesmo com um compressor mais simples, consegui reduzir um pouco os dados e realizar a tradução.

Eu particularmente prefiro usar pseudocompressão a fazer desvios. Acho que assim o código fica mais limpo, menos suscetível a bugs, e preserva mais a originalidade da ROM. Também me força a estudar o algoritmo de descompressão, o que na maioria das vezes considero muito prazeroso, mas sem a necessidade de sempre encarar o desafio maior, que é criar o próprio compressor.

## Principais técnicas de compressão

Chegando próximo de finalizar este material, vejamos uma apresentação geral das técnicas de compressão mais conhecidas. Não vamos entrar a fundo na implementação de cada uma delas, mas é importante que você entenda que quando estiver desbravando um jogo e encontrar conteúdo comprimido, o primeiro passo será inevitavelmente identificar qual é a técnica de compressão que está sendo utilizada nele.

### RLE (Run-Length Encoding ou Compressão por Repetição)

Uma das técnicas mais simples. Substitui sequências longas de um mesmo caractere por um código que indica quantas vezes ele deve se repetir. É muito eficiente quando há repetições grandes, como fundos ou bordas em jogos 2D.

### DTE (Dual Tile Encoding)

Muito usada em traduções de jogos. Um único byte passa a representar dois caracteres, reduzindo pela metade o espaço necessário em casos comuns.

### MTE (Multiple Tile Encoding)

Segue a mesma lógica do DTE, mas permite que um único byte represente sequências ainda maiores de caracteres, e não apenas pares.

### Substituição por Dicionário

Um conceito mais amplo. Consiste em criar uma tabela onde ficam armazenados padrões que se repetem, e no texto são gravadas apenas referências a eles. É muito útil em jogos para nomes de itens, personagens ou habilidades, já que esses nomes aparecem várias vezes no texto. Em vez de escrever “POÇÃO” repetidamente, o jogo guarda “POÇÃO” apenas uma vez no dicionário e faz referência a ele sempre que precisar. O dicionário pode ser fixo (pré-definido) ou dinâmico (construído durante a leitura, como nos algoritmos da família LZ).

### Algoritmos da família LZ

Exemplos avançados de compressão baseada em dicionário. A lógica deles é referenciar trechos que já apareceram anteriormente no próprio fluxo de dados, em vez de repetir a informação. Em termos práticos, dizem algo como: “volte X posições e copie Y caracteres”. Variantes como LZ77, LZ78, LZW e LZSS são bastante usadas em jogos e formatos de arquivo.

### Huffman

Uma técnica de codificação que atribui códigos curtos para símbolos frequentes e códigos maiores para símbolos raros. Mesmo que alguns símbolos passem a ocupar mais espaço, o resultado final é uma grande economia porque a maior parte do texto usa os códigos mais curtos.

### Codificação Aritmética

Parte da mesma ideia do Huffman, mas utiliza intervalos matemáticos para representar probabilidades. Isso permite atingir taxas de compressão ainda melhores, embora à custa de maior complexidade e maior demanda de processamento.

## Terminologias e glossário

Para finalizar, é importante entender que conhecer o significado das palavras facilita muito o aprendizado de qualquer nova disciplina. No caso da compressão de dados, existe um conjunto de termos que aparecem o tempo todo. Se você já estiver familiarizado com eles, mesmo antes de entrar a fundo na prática, seu estudo flui muito melhor.

Por isso, reuni aqui uma lista de terminologias muito utilizadas no mundo da compressão, que certamente você encontrará em materiais e explicações sobre o tema.

### Custo

É o espaço extra que precisa ser reservado para que a compressão funcione. Inclui o tamanho das rotinas de descompressão, tabelas auxiliares e até o processamento adicional que o sistema terá que fazer. Compressão só vale a pena quando a economia é maior que o custo.

### Referência

É um marcador que aponta para algum dado já existente. Em vez de repetir uma informação, o algoritmo escreve uma referência dizendo onde encontrar ou como reconstruir o dado original.

### Relativa

Muitas referências em algoritmos de compressão são relativas, ou seja, não dizem “vá até a posição X”, mas sim “volte N passos a partir da posição atual e copie Y bytes”. Essa é a base de algoritmos como LZ77.

### Literal

É o dado gravado exatamente como está, sem compressão. Em muitos algoritmos, quando algo não pode ser compactado de forma útil, ele é armazenado como literal.

### Token

É a menor unidade de informação manipulada pelo compressor. Pode ser um caractere, um par de bytes, ou até um símbolo especial que indica “referência” ou “literal”.

### Dicionário

Estrutura que guarda padrões ou sequências comuns, permitindo que no texto original eles sejam substituídos por uma referência. Pode ser fixo ou dinâmico.

### Janela (ou Sliding Window)

Conceito usado em algoritmos como LZ77. É uma faixa de dados já processados que o compressor/descompressor mantém em memória. As referências apontam para dentro dessa janela, indicando trechos repetidos.

### Entropia

Medida matemática que representa o quanto há de incerteza ou desordem em um conjunto de dados. Quanto maior a entropia, menor a possibilidade de compressão. Arquivos de texto geralmente têm entropia baixa (bons para comprimir), enquanto arquivos já comprimidos têm entropia alta.

### Prefixo

Em compressão por frequência (como Huffman), os códigos são montados de forma que nenhum código seja prefixo de outro. Isso garante que o decodificador consiga interpretar o fluxo de bits sem ambiguidade.

### Bitstream

É o fluxo contínuo de bits gerado por um compressor. Em vez de pensar em bytes organizados, imagine uma fita de 0s e 1s que o algoritmo produz. Essa camada é onde entram conceitos como códigos de tamanho variável e alinhamento de bits. Assunto mais avançado.

### Bitwise

São operações realizadas diretamente em nível de bits (AND, OR, XOR, shifts e afins). Na compressão de dados, isso é usado o tempo todo para manipular e interpretar informações de forma compacta.

Muitas vezes, alguns poucos bits dentro de um byte já carregam instruções: se é um literal, se é uma referência, se é relativa ou até quantos bytes devem ser lidos a seguir. É por meio dessas operações que o programa consegue “quebrar” os dados em pedaços mínimos e reconstruir a lógica da compressão.