---
layout: tutorial
title:  "Como Instalar o Emulador de NES no Nintendo 3DS "
---

Este tutorial mostra como jogar jogos de NES (Famicom) no Nintendo 3DS utilizando o emulador **VirtuaNES 3DS**. O método recomendado instala o emulador diretamente no menu do 3DS, permitindo acesso rápido sem precisar do Homebrew Launcher.

## O que você precisa  
- Um **Nintendo 3DS desbloqueado** com Homebrew  
- O emulador **VirtuaNES 3DS** ([baixe aqui](https://github.com))  
- ROMs de NES no formato `.nes`  
- O aplicativo **FBI** instalado para instalar arquivos `.cia`  

## Escolhendo o Formato: .CIA vs .3DSX  
- `.CIA` → Instala o emulador diretamente no menu do 3DS. **Recomendado** para praticidade  
- `.3DSX` → Precisa do Homebrew Launcher sempre que quiser abrir o emulador  

## Instalando o VirtuaNES no 3DS  
1. Baixe o **VirtuaNES 3DS** e extraia o arquivo `.zip`  
2. Pegue o arquivo **`virtua3ds.cia`** e mova para a pasta **`cias`** do seu cartão SD  
   - Se a pasta **`cias`** não existir, crie uma  
3. Mova o arquivo **`virtuaNES_3DS_top.png`** para a raiz do cartão SD  
4. Insira o cartão SD de volta no 3DS e abra o **FBI**  
5. Vá até **SD → cias → virtua3ds.cia** e instale  
6. Pressione **Home**, e o VirtuaNES aparecerá como um novo ícone no menu  

## Adicionando Jogos (ROMs)  
1. No cartão SD, crie uma pasta chamada **"NES ROMs"** (ou use a pasta `roms/nes` se já tiver o Twilight Menu++)  
2. Copie os arquivos **`.nes`** para essa pasta  
3. Ejetar o cartão SD e inserir de volta no 3DS  

## Rodando os Jogos  
1. Abra o **VirtuaNES** no menu do 3DS  
2. Navegue até a pasta onde colocou as ROMs  
3. Selecione um jogo e jogue normalmente  

## Transferindo arquivos via FTP  
Se você tem um **New Nintendo 3DS XL**, pode enviar os arquivos via FTP sem precisar remover o cartão microSD manualmente:  
1. Instale o **FTPD** pelo FBI  
2. Abra o app e conecte-se pelo PC via um cliente FTP (ex: WinSCP ou FileZilla)