---
layout: ferramenta
title:  "TBL to JSON Converter"
description: "Converter TBL para JSON"
---

O formato tradicional de tabelas de caracteres usado no ROM Hacking consiste em arquivos .tbl que são nada mais do que um arquivo de texto indicando o valor hexadecimal correspondente a determinado caractere do alfabeto.

Exemplo:

	0A=A
	0B=B
	0C=C
	0D=D
	0E=E
	...

No meu caso, utilizo o editor hexadecimal Hex Fiend para trabalhar pelo Mac. Este editor aceita codificação personalizada, mas não no tradicional formato de tabelas do ROM Hacking.

Para adicionar a codificação personalizada, o mapeamento deve estar em formato JSON, conforme o exemplo a seguir:

	json
	{
	  "name": "Nome de exibição",
	  "map": {
	    "01": "A",
	    "02": "B",
	    "04": "C",
	    "05": "D",
	    "06": "E",
	    "07": "F",
	    "08": "G"
	  }
	}

Esta ferramenta tem como objetivo traduzir do tradicional formato TBL para este formato em JSON e assim ser usado no Hex Fiend (ou outra ferramenta que necessite da tabela neste formato).

O uso é simples e intuitivo, bastando selecionar o arquivo de entrada e o nome do arquivo de saída (que estará no campo "name" do JSON).

Esta ferramenta tem como objetivo traduzir do tradicional formato TBL para este formato em JSON e assim ser usado no Hex Fiend (ou outra ferramenta que necessite da tabela neste formato).

O uso é simples e intuitivo, bastando selecionar o arquivo de entrada e o nome do arquivo de saída (que estará no campo "name" do JSON).

![Image](/img/tool_tbl2json/tbl2json.png){:class="centered custom-width-600"}

Para utilizar no Hex Fiend, coloque o arquivo gerado na seguinte pasta:

	~/Library/Application\ Support/com.ridiculousfish.HexFiend/Encodings

## Download

Faça o download da ferramenta pelos links abaixo:

- Versão para MacOS: [Download pelo Mega](https://mega.nz/file/gvkh1aSJ#7MxhiME4c2RAkGyHXPw06F86qPOQ4OpTIJhYEXGjf9o)
- Versão para Windows 64bits: (Link em breve)

## Links relacionados

- [Site oficial do Hex Fiend](https://hexfiend.com/)
- [Informações do recurso de codificação personalizada no Hex Fiend](https://github.com/HexFiend/HexFiend/issues/95#issuecomment-397858715)
