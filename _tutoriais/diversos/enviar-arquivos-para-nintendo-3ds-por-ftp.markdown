---
layout: tutorial
title:  "Enviar arquivos para o Nintendo 3DS via FTP"
---

Se você tem um Nintendo 3DS desbloqueado, pode utilizar FTP para transferir arquivos a partir de seu PC. Isto é particularmente útil em versões como o New Nintendo 3DS XL, em que precisamos tirar um parafuso para acessar o cartão de memória. Deus me livre ter que desparafuzar algo toda vez que quiser colocar uma ROM ou outro arquivo no aparelho!

Caso não saiba, FTP significa "File Transfer Protocol", sendo uma maneira de transferir arquivos entre computadores em uma rede. Ele permite que você envie e receba arquivos conectando-se a um servidor FTP através de um programa específico.

Antes de falarmos sobre o uso do FTP para transferir arquivos para o Nintendo 3DS, é importante entender alguns conceitos e ferramentas essenciais. Crio este tutorial como forma de anotação pessoal mesmo, pois eu mesmo estou aprendendo sobre isso com este processo de passar a jogar mais em um 3DS.

## Aplicativos em .cia e .3dsx

Ao instalar jogos, homebrews e aplicativos em seu Nintendo 3DS, eles podem estar no formato .cia ou .3dsx. Os arquivos .cia são instaláveis no sistema do 3DS, permitindo que os aplicativos apareçam no menu principal como se fossem jogos ou aplicativos oficiais. Isso oferece uma experiência mais integrada e persistente.

Já os arquivos .3dsx são executados diretamente através de um homebrew launcher, como o Homebrew Launcher, sem a necessidade de instalação. Esse formato é mais conveniente para testes e uso temporário, pois não altera permanentemente o sistema do 3DS.

Para o processo deste tutorial, instalaremos o **ftpd**, que está disponível nos dois formatos. Escolha o que considerar mais conveniente para você.

## Desbloqueio pelo Luma3DS

O Luma3DS é o custom firmware (CFW) mais amplamente utilizado para desbloquear o Nintendo 3DS. Ele permite que o console rode aplicativos não oficiais (homebrew), emulação e jogos de outras regiões. Com o Luma, você tem acesso total ao sistema, permitindo a instalação de jogos no formato .cia, bem como o uso de ferramentas avançadas.

## FBI: O Gerenciador de Arquivos para 3DS

O FBI é um gerenciador de arquivos essencial para quem desbloqueou o 3DS. Ele permite a instalação de arquivos .cia diretamente no console. Após o desbloqueio, você utilizará o FBI para instalar aplicativos como o FTPD, que abordaremos mais adiante no tutorial. Além disso, o FBI também pode ser usado para gerenciar arquivos e explorar o conteúdo do seu cartão SD.

Agora que você entende os formatos de arquivos e os principais programas como o Luma e o FBI, vamos para o passo a passo de como transferir arquivos para o 3DS usando o FTP.

## Universal Updater

O Universal Updater é uma ferramenta homebrew para o Nintendo 3DS que facilita a instalação de outros aplicativos e homebrews diretamente no console. Ele funciona como uma loja centralizada, permitindo que os usuários busquem e baixem uma variedade de softwares, como jogos, utilitários e emuladores, sem a necessidade de acessar um computador. Isso elimina o processo manual de transferir arquivos para o cartão SD, tornando a instalação de aplicativos como o FTPD ou gerenciadores de arquivos muito mais rápida e conveniente para quem tem o 3DS desbloqueado.

## Instale o ftpd

O ftpd é um aplicativo para Nintendo 3DS que abre um servidor de FTP para o mesmo. Feito isso, qualquer outro dispositivo pode conectar ao aparelho via FTP e assim transferir arquivos.

Existem duas formas de instalá-lo no console. A primeira consiste em baixar o arquivo .cia ou .3dsx pelo próprio PC, colocá-lo no cartão SD (e assim essa seria a última vez que você teria que desparafuzar) e instalar.

A segunda forma consiste em baixá-lo pelo **Universal Updater** e então executá-lo pelo **Homebrew Launcher**.

## Instalando o ftpd pelo Universal Updater

Se você tem o Universal Updater em seu aparelho, esta é a forma mais simples.

1. Abra o Universal Updater
2. Clique na lupa e busque por ```ftpd```
3. Escolha o ```ftpd.3dsx``` para baixar
4. Abra o **Homebrew Launcher**
5. Execute o ```ftpd.3dsx```

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

## Iniciando o servidor

Ao abrir o ftpd, automaticamente o servidor estará ativo. Logo no começo, na tela de cima, você verá o endereço IP e a porta para conectar ao console via FTP.

## Conectando e transferindo arquivos

Para conectar ao aparelho e transferir arquivos, você precisará de um cliente de FTP. Existem inúmeras opções, mas vou recomendar o [Filezilla](https://filezilla-project.org/){:target="_target"}. Baixe e instale o Filezilla no seu computador. **Lembre-se de baixar o cliente**, não o servidor.

![alt text](/img/tutorial_ftp_3ds/filezilla.png){:class="centered"}