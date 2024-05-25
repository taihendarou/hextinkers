---
layout: post
title:  "Implementações gráficas em Dragon Ball Z - Super Gokuuden: Totsugeki-hen"
date:   2024-05-25 00:00:00 -0300
---

Uns dias atrás, comuniquei aqui o lançamento de uma versão em português de Dragon Ball Z - Super Gokuuden: Totsugeki-hen, de SNES. Hoje trago algumas implementações de gráfico que fiz para o lançamento de uma atualização do projeto.

Estas implementações envolveram um trabalho de criação de ferramentas de descompressão e compressão. Agora, praticamente todos os assets do jogo estão acessíveis e prontos para serem alterados, caso necessários.

A primeira implementação foi na tela título, agora com um novo logo para "A Lenda de Goku" e uma nova fonte nos créditos dos desenvolvedores (e tradutores). Na versão anterior, a equipe tinha acesso apenas ao tileset desta tela, por isso não era possível fazer mudanças que envolviam estrapolar os limites já impostos pelo tilemap. Agora, isso foi possível. Veja o antes e depois:

{:.text-align-center}
![DBZ SGTH](/img/misc/dbz_sgth1.png){:class="custom-width-300"}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_000.png){:class="custom-width-300"}

Algumas telas apresentam capas de volumes do mangá de Dragon Ball. Uma delas continham erros de digitação dos próprios produtores, em que acabaram escrevendo "Red Ribon" (o correto é "Red Ribbon") e "Son Gokuh" (com este "h", que não faz parte da romanização oficial do nome). Em outra dessas capas, alteramos "Attack" para "Atacar!".

{:.text-align-center}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_002.png)
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_001.png)

Na parte em que aparecem as revistas safadinhas do Mestre Kame, há um "H" na capa, em referência a "Hentai" (ou talvez "ecchi", com foco na pronúncia). Alteramos para "18+":

{:.text-align-center}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_003.png)

"Capsule Corp." alterado para "Corp. Cápsula":

{:.text-align-center}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_004.png)

A fachada do torneio de artes marciais foi editada, escrevendo "Torneio". Aqui, utilizamos como inspiração a mesma fonte usada para mesmo fim no Dragon Ball Z de NES que traduzi anteriormente.

{:.text-align-center}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_007.png)

Essa mesma placa aparece de uma distância maior em outra cena. Neste caso, não há muito espaço para trabalhar a fonte de forma única.

{:.text-align-center}
![DBZ SGTH](/img/misc/DBZ-sgth-pt_GFX-Taihen_test_006.png)

Lembrando que o projeto tem um site oficial mantido pelo coordenador Nathan. Lá você pode encontrar o patch mais atualizado disponível ao público: [https://ntn-ss.github.io/Projetos_de_Traducao/DBZ-SGTH/](https://ntn-ss.github.io/Projetos_de_Traducao/DBZ-SGTH/){:target="_blank"}