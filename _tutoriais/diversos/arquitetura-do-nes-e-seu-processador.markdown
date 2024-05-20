---
layout: tutorial
title:  "A arquitetura do NES e seu processador 6502"
---

Esta é uma explicação introdutória sobre a arquitetura geral do NES / Super Famicom, algumas informações relevantes sobre os cartuchos e sobre o processador 6502.

## O cartucho e suas ROMs

Nos cartuchos de NES, temos na verdade duas ROMs:

- PRG-ROM: Contém o programa do jogo, incluindo as rotinas e o código.
- CHR-ROM: Armazena os assets gráficos e de som.

Essa separação é física no próprio cartucho, com dois chips distintos para cada uma.

Porém, nas ROMs que baixamos da internet, temos um arquivo único. No caso, o conteúdo das duas ROMs estão condensadas no arquivo. Geralmente estes arquivos contém um cabeçalho de 16 bytes com informações sobre o tamanho da PRG-ROM e da CHR-ROM. Quase sempre a PRG-ROM vem primeiro.

### Mappers

Os mappers são circuitos adicionais que gerenciam os bancos de memória da ROM e podem adicionar recursos específicos que apenas cartuchos com aquele mapper podem utilizar. Os mappers trazem recursos como espelhamento gráfico, interrupções (IRQ), memória RAM com bateria para permitir o salvamento, efeito de paralax, compressão de dados e outros.

### Bancos

Dependendo do mapper do cartucho, todo conteúdo da ROM é carregado na memória do processador ao mesmo tempo. Porém, em casos de jogos maiores, este conteúdo deve ser carregado em partes. Nisso surge a figura dos bancos.

Entenda os bancos como pedaços da ROM, falando de forma esdrúxula. O mapper controla qual destes pedaços está carregado na memória do processador no momento. O banco pode ser trocado dinamicamente de acordo com a demanda, através de uma técnica chamada bank switching. Isso permite que jogos utilizem mais memória do que o espaço diretamente disponível na memória RAM do processador.

A troca de bancos é controlada pelo software do jogo, que envia comandos específicos ao mapper para alternar entre diferentes bancos de PRG-ROM e CHR-ROM. Isso significa que apenas uma parte da ROM está acessível ao processador de cada vez, mas diferentes partes podem ser carregadas conforme necessário para diferentes níveis, gráficos ou rotinas do jogo.

## Arquitetura geral do console

A arquitetura geral do NES é deveras simples. Por isso é um excelente console para aprender os fundamentos básicos de um hardware (e também, pelo mesmo motivo, ele é até hoje extremamente clonável). De modo geral, consiste em uma placa com:

- Processador (CPU)
- Unidade de processamento de áudio (APU) no mesmo chip da CPU
- 2Kb de memória RAM para o processador
- Unidade de processaomento de vídeo (PPU)
- 2Kb de memória RAM para a PPU
- Um _lockout chip_, para reset do console e proteção

Claro que além disso temos elementos como as entradas para controles, entrada para cartucho, saída de áudio e vídeo, capacitores e outros componentes eletrônicos referentes a montagem da placa e controle de energia.

![Arquitetura do NES](/img/tutorial_nes_arch/arquitetura-do-nes.png){:class="centered"}

## O processador do NES

O NES utiliza o clássico processador 6502, utilizado nos primeiros computadores da Apple, nos Ataris 2600, 5200 e 7800, no Commodore 64 e no TurboGrax-16. É uma versão levemente modificada em relação ao processador original, mas todo princípio de funcionamento é basicamente o mesmo.

O processador trabalha com endereçamento de dados de 16 bits. Por consequência, sua "memória interna" é de 65.535 bytes (`0xFFFF` em hexadecimal, maior valor possível de ser representado com 16 bits).

Ao usar um emulador com ferramentas de depuração e visualizar a memória da CPU, é exatamente isso que visualizamos. Dados entre `0x0000` à `0xFFFF`.

![Memória da CPU do NES](/img/tutorial_nes_arch/cpu_memory.png){:class="centered"}

Estes 64Kb de memória estão dividos da seguinte forma:

{:.tabela}
Endereço        |   Descrição
---             |   ---
0x0000 - 0x07FF |   2kB de memória RAM para uso do programa
0x0800 - 0x0FFF |   Espelhamento da memória RAM
0x1000 - 0x17FF |   Espelhamento da memória RAM
0x1800 - 0x1FFF |   Espelhamento da memória RAM
0x2000 - 0x2007 |   Registradores de comunicação com a PPU
0x2008 - 0x3FFF |   Espelhamento dos registradores anteriores
0x4000 - 0x401F |   Comunicação com APU e com os controles
0x4020 - 0x5FFF |   Espaço não mapeado, disponível para uso pelo cartucho
0x6000 - 0x7FFF |   RAM de trabalho ou de backup com bateria (conhecida como WRAM ou PRG-RAM)
0x8000 - 0xFFFF |   ROM do cartucho e registradores de mapeamento

De modo geral, ao analisarmos a memória do processador a partir de `0x8000`, nos deparamos com o início da execução do programa. No caso de ROMs de jogos, a execução do jogo começa por ali.