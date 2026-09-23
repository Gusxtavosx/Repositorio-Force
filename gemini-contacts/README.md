# Gemini Contatos

Versão 0.4.2.

Módulo para Foundry VTT v14 e a ficha `character` do sistema Mythras de Gemini Force. Insere cards na aba **Social**, sem alterar os arquivos do sistema.

## Recursos

- Tipos: **Contato**, **Instrutor** e **Retaguarda**. Registros antigos marcados como Inimigo/Nêmesis continuam na ficha como Contato, sem perder nome, imagem ou descrição.
- Contato: amizade entre 1% e 100%. Retaguarda aparece numa subseção própria, com cargo ou posto em texto livre. Qualquer tipo pode receber um grupo livre (por exemplo, DRACS ou CCN).
- Todos os tipos têm nome, imagem em destaque e descrição/sistemática. Com o **Gemini TinyMCE** ativo, a edição usa a biblioteca TinyMCE já instalada, com uma barra contendo **Salvar**, alinhamento e tabela. O botão Salvar dentro do editor salva o contato inteiro. Sem esse módulo, continua disponível a edição em Markdown com prévia. Descrições anteriores em Markdown são convertidas para HTML ao editar no TinyMCE.
- Na aba principal Social, as subabas de **Contatos** e **Círculos Sociais** são representadas por ícones centralizados com títulos acessíveis. Cada uma mantém seu espaço próprio; a seção de Contatos tem painel escuro delimitado e espaçamento interno, como os quadros da ficha.
- Um mestre pode arrastar um card de uma ficha para outra para copiar todos os seus dados.
- A **Central de Contatos** fica nos controles à esquerda do mapa, somente para mestres. Nela é possível criar, pesquisar, filtrar por tipo, editar, excluir, receber um contato arrastado de uma ficha e arrastar contatos para fichas. Os cards grandes destacam os retratos; a logo no rodapé da Central usa o endereço de imagem fornecido pelo projeto e precisa estar acessível ao navegador. O catálogo fica em um JournalEntry do mundo com permissão padrão **Nenhuma** para jogadores.
- A aba Social permite rolar para alcançar os cards e a Retaguarda.
- Mestre adiciona, edita, exclui e arrasta um Item para a seção. Jogadores com acesso à ficha veem os cards e as anotações, sem poder conceder ou alterar contatos.
- Os dados ficam em `flags.gemini-contacts.entries` de cada Ator, separados por personagem e mantidos mesmo quando a ficha muda de visual.

## Instalação local

Extraia a pasta `gemini-contacts` em `Data/modules/`, ative o módulo no mundo e abra a aba Social de uma ficha de personagem. Clique no ícone de livro de contatos e depois no **+** como mestre. Clique em um card para editar, arraste-o para outra ficha ou use o **×** para excluí-lo. Abra a Central pelo ícone de livro de contatos nos controles do mapa. Os arquivos do sistema Mythras não precisam ser modificados.

## Instalação por URL

Em **Configuração > Módulos > Instalar módulo**, informe:

`https://raw.githubusercontent.com/Gusxtavosx/Repositorio-Force/main/gemini-contacts/module.json`

O manifesto fica na pasta própria deste módulo no repositório. O `module.json` da raiz instala o módulo Gemini TinyMCE, que é separado e opcional. A URL de download do ZIP aponta para a versão 0.4.2; nas próximas versões, atualize o manifesto e publique o ZIP correspondente na mesma pasta. O Gemini TinyMCE pode ser instalado e ativado para habilitar o editor visual das descrições.

## Integração com a loja

O sistema compartilhado ainda não possui um subtipo de Item `contact`. O módulo permite arrastar um Item para a seção como mestre. Para definir o tipo e as demais propriedades em um Item modelo, use a flag `gemini-contacts.template`, por exemplo:

```js
await item.setFlag("gemini-contacts", "template", {
  kind: "support", role: "Analista de inteligência",
  description: "Fornece relatórios e acesso a arquivos."
});
```

Uma integração futura pode chamar `game.modules.get("gemini-contacts").api.grant(actor, item)` **no cliente de um mestre** quando a loja confirmar a entrega. A compra externa, a cobrança e a liberação automática ainda não estão ligadas a este módulo.

**Limite de privacidade:** jogadores que podem abrir a ficha conseguem ler as descrições armazenadas nela. Não inclua segredos exclusivos do mestre nesse campo.
