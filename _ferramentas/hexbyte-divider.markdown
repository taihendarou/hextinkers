---
layout: ferramenta
title:  "Hexbyte Divider"
description: "Formatar bytes copiados de editor hexadecimal em formato de Bass"
---

Muitas vezes fazemos ajustes diretamente no editor hexadecimal do emulador para ver as mudanças em tempo real, como ajustes no layout do jogo ou alteração de textos. Depois, precisamos copiar estes valores e inserir em nosso patch em assembly.

Para isso, estes valores precisam ter uma formatação específica, diferente do que é copiado diretamente do editor hexadecimal. Ajustar manualmente esta formatação, byte por byte, pode ser um trabalho penoso quando estamos falando de certa quantidade de valores. Por isso, esta ferramenta foi desenvolvida para, com apenas um clique, deixar os valores perfeitamente formatados para inserir em seu programa.

Para exemplificar, suponha que você tenha os seguintes valores:

	4E 45 53 1A 08 10 40 08 00 00 00 00 00 00 00 01 42 41 4E 4B 30 20 20 20 20 20 20 20 20 20 20 20 10 93 1C 93 40 93 10 93 64 93 70 93 94 93 94 93 94 93 B8 93 DC 93 E8 93 0C 94 18 94 3C 94 48 94 6C 94 78 94 9C 94 A8 94 78 94 78 94 78 94 78 94 78 94 78 94 78 94 E4 94 08 95 14 95 38 95 44 95 FC 9D 08 9E 2C 9E 38 9E 38 9E 38 9E 38 9E 38 9E 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 10 93 28 93 34 93 4C 93 58 93 7C 93 88 93 A0 93 AC 93 C4 93 D0 93 F4 93 00 94 24 94 30 94 54 94 60 94

O HexByte Divider o ajudará a formatar para:

	db $4E, $45, $53, $1A, $08, $10, $40, $08, $00, $00, $00, $00, $00, $00, $00, $01
	db $42, $41, $4E, $4B, $30, $20, $20, $20, $20, $20, $20, $20, $20, $20, $20, $20
	db $10, $93, $1C, $93, $40, $93, $10, $93, $64, $93, $70, $93, $94, $93, $94, $93
	db $94, $93, $B8, $93, $DC, $93, $E8, $93, $0C, $94, $18, $94, $3C, $94, $48, $94
	db $6C, $94, $78, $94, $9C, $94, $A8, $94, $78, $94, $78, $94, $78, $94, $78, $94
	db $78, $94, $78, $94, $78, $94, $E4, $94, $08, $95, $14, $95, $38, $95, $44, $95
	db $FC, $9D, $08, $9E, $2C, $9E, $38, $9E, $38, $9E, $38, $9E, $38, $9E, $38, $9E
	db $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93
	db $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93
	db $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93, $10, $93
	db $28, $93, $34, $93, $4C, $93, $58, $93, $7C, $93, $88, $93, $A0, $93, $AC, $93
	db $C4, $93, $D0, $93, $F4, $93, $00, $94, $24, $94, $30, $94, $54, $94, $60, $94

A interface permitirá que você escolha o prefixo para cada byte. Permitirá que você escolha se deseja inserir o comando db e se deseja separar os valores por vírgula.

![HexByte Divider](/img/tool_hexbyte/hexbytedivider.png){:class="centered"}

## Desenvolvimento

A ferramenta foi desenvolvida em Python com a interface visual desenvolvida utilizando a biblioteca tkinter. O arquivo executável foi gerado através do pyinstaller, portanto não é necessário instalar nenhuma biblioteca complementar para utilizá-la.

## Download

Faça o download da ferramenta pelos links abaixo:

- Versão para MacOS: [Download pelo Mega](https://mega.nz/file/M7EAWAJb#7D02-ai3u7MPiLRoegxME7h6sEhjDzpMaz0nGQRqpnA){:target="_blank"}
- Versão para Windows 64bits: Link em breve