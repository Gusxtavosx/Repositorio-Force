# Gemini TinyMCE

Editor TinyMCE 6 para campos de texto no Foundry VTT v14. Inclui atalhos Gemini, tabela, alinhamento e botão para salvar o conteúdo na ficha.

## Instalação por URL

Em **Configuração > Módulos > Instalar módulo**, cole esta URL:

`https://github.com/Gusxtavosx/Repositorio-Force/releases/latest/download/module.json`

Ative **Gemini TinyMCE** no mundo e recarregue a página.

O manifesto publicado aponta para o ZIP da mesma versão; versões novas podem ser instaladas pelo gerenciador de módulos. Este módulo foi testado pelo usuário em Foundry v14 com sua ficha Mythras. Outros sistemas e fichas que criam seu próprio editor podem precisar de adaptação.

O código completo, as instruções detalhadas (`LEIA-ME.txt`) e a licença MIT do TinyMCE 6.8.3 (`vendor/tinymce/license.txt`) estão no arquivo `gemini-tinymce-codigo-github-v0.6.0.zip` deste repositório. O ZIP de instalação `gemini-tinymce-v0.6.0.zip` e o manifesto `module.json` ficam nos arquivos do release.

## Publicação

O workflow `.github/workflows/release.yml` cria os arquivos de instalação ao enviar uma tag igual a `v` seguida da versão do `module.json` (por exemplo, `v0.6.0`). O manifesto instalado usa um URL estável para verificar atualizações e um ZIP fixo por versão.
