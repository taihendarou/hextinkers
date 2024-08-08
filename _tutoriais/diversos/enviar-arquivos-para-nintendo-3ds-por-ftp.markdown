---
layout: tutorial
title:  "Enviar arquivos para o Nintendo 3DS via FTP"
---

Se você tem um Nintendo 3DS desbloqueado, pode utilizar FTP para transferir arquivos a partir de seu PC. Isto é particularmente útil em versões como o New Nintendo 3DS XL, em que precisamos tirar um parafuso para acessar o cartão de memória. Deus me livre ter que desparafuzar algo toda vez que quiser colocar uma ROM ou outro arquivo no aparelho!

Caso não saiba, FTP significa "File Transfer Protocol", sendo uma maneira de transferir arquivos entre computadores em uma rede. Ele permite que você envie e receba arquivos conectando-se a um servidor FTP através de um programa específico.

## Instale o ftpd

O ftpd é um aplicativo para Nintendo 3DS que abre um servidor de FTP para o mesmo. Feito isso, qualquer outro dispositivo pode conectar ao aparelho via FTP e assim transferir arquivos.

Existem duas formas de instalá-lo no console. A primeira consiste em baixar o arquivo ```.cia``` pelo próprio PC, colocá-lo no cartão SD (e assim essa seria a última vez que você teria que desparafuzar) e instalar o .cia através do FBI.

A segunda forma consiste em baixá-lo pelo Universal Updater e então executá-lo pelo **Homebrew Launcher**.

## Adicionando o ftpd manualmente no cartão SD

1. Baixe o ftpd.cia em seu [repositório do Github](https://github.com/mtheall/ftpd/releases/tag/v2.2){:target="_blank"}.
2. Coloque o cartão microSD no computador
3. Arraste o arquivo CIA para a pasta "cias" no cartão microSD do seu 3DS.
4. Coloque o cartão de volta no 3DS
5. Abra o FBI
6. Vá para "SD" e depois para ``cias``
7. Selecione o arquivo ``ftpd.cia``
8. Pressione "A" e selecione "Install and Delete CIA". Pressione "A" novamente e depois "Yes"
9. Após a instalação, clique em "OK" e pressione o botão "Home"
10. Pronto, agora o FTPD estará disponível na tela inicial do seu 3DS

## Instalando o ftpd pelo Universal Updater

1. Abra o Universal Updater
2. Clique na lupa e busque por ```ftpd```
3. Escolha o ```ftpd.3dsx``` para baixar
4. Abra o **Homebrew Launcher**
5. Execute o ```ftpd.3dsx```

## Iniciando o servidor

Ao abrir o ftpd, automaticamente o servidor estará ativo. Logo no começo, na tela de cima, você verá o endereço IP e a porta para conectar ao console via FTP.

## Conectando e transferindo arquivos

Para conectar ao aparelho e transferir arquivos, você precisará de um cliente de FTP. Existem inúmeras opções, mas vou recomendar o [Filezilla](https://filezilla-project.org/){:target="_target"}. Baixe e instale o Filezilla no seu computador. **Lembre-se de baixar o cliente**, não o servidor.

![alt text](/img/tutorial_ftp_3ds/filezilla.png){:class="centered"}