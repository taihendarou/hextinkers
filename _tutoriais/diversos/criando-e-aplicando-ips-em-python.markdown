---
layout: tutorial
title:  "Criando ou aplicando patch IPS em Python"
---

Normalmente, usamos ferramentas como Lunar IPS para gerar ou aplicar os patches em formato IPS.

Entretanto, pode ser útil fazê-lo através de linha de comando de console. Assim, pode-se configurar em seu workflow para, quando uma nova ROM for gerada após ROM alterada via assembly, também ser gerado um arquivo IPS automaticamente dentro da mesma pasta.

Para isso, encontrei no Github o pacote IPS Util. Você pode acessá-lo em [https://github.com/nleseul/ips_util](https://github.com/nleseul/ips_util){:target="_blank"}.

Para instalá-lo (partindo do princípio que você já tem Python instalado em sua máquina), digite no terminal:

`pip install ips-util`

Agora, para gerar um arquivo IPS a partir de uma ROM modificada, basta seguir o modelo:

`ips_util create "rom_original" "rom_modificada" -o nome_do_patch.ips`

Isto gerará o arquivo `nome_do_patch.ips` que agora será capaz de aplicar as modificações de `rom_modificada` em qualquer `rom_original`.

Você também pode usá-lo apra aplicar IPS em uma ROM:

`ips_util apply nome_do_patch.ips "rom_original" -o "rom_patcheada"`

Isto gerará uma `rom_patcheada` criada a partir da `rom_original` com as alterações contidas em `nome_do_patch.ips`

Lembre-se de colocar extensões de arquivo nos comandos acima. Afinal, são apenas exemplos.

A verdadeira utilidade disso é colocar estes comandos em batches (arquivos .bat ou .sh que executam sequências de comandos) e já deixar pronto no seu workflow de ROM Hacking. Faço isso especialmente quando estou fazendo implementações pontuais em projetos de colegas e preciso sempre estar mandando apenas um patch com minhas alterações.

Também é possível usar este pacote dentro de scripts em Python. No readme do Git já tem dois excelentes exemplos.
