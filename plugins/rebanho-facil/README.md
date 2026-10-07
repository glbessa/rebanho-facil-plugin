# Rebanho Fácil

Plugin do [Rebanho Fácil](https://rebanhofacil.com) para Claude, ChatGPT e
Codex. Ele liga o assistente à sua conta do Rebanho Fácil para registrar e
consultar o rebanho da fazenda por conversa: cadastro de animais, pesagens e
GPD, medicamentos e carências, vacinas pendentes, IATF, diagnósticos de
prenhez, partos, lotes, campos e pastagens, tarefas da equipe e o financeiro
(despesas, receitas, fluxo de caixa e resumo).

Exemplos do que dá para pedir:

- "Registra pesagem de 380 kg no brinco 4471, hoje."
- "Quais animais estão com carência de medicamento ativa?"
- "Move o lote Recria 2 para o piquete 7."
- "Quanto gastei com sanidade este mês?"

## O que vem no plugin

- **Conector MCP** apontando para `https://app.rebanhofacil.com/mcp`.
- **Skill `manejo-rebanho`**, que ensina o assistente a escolher a fazenda,
  achar animais pelo brinco, usar as operações em lote e confirmar antes de
  excluir qualquer registro.

O plugin não roda código na sua máquina. Ele só declara o servidor remoto e a
skill.

## Conta e acesso

Você precisa de uma conta no Rebanho Fácil. Na primeira vez, o assistente abre
a tela de login do Rebanho Fácil (OAuth 2.1) para você autorizar o acesso. O
assistente enxerga apenas as fazendas a que sua conta tem acesso, e quem tem
papel de visualizador não consegue gravar nada.

## Dados e privacidade

As mensagens trocadas com o assistente seguem para o servidor do Rebanho Fácil
só quando uma operação é chamada, e somente com os dados daquela operação. O
servidor registra qual operação foi usada e quando, sem guardar os argumentos
nem as respostas. Nenhum dado é enviado a terceiros pelo plugin.

- Política de privacidade: https://app.rebanhofacil.com/privacidade
- Termos de uso: https://app.rebanhofacil.com/termos
- Suporte: suporte@rebanhofacil.com

## Instalação manual

Claude Code:

```bash
claude plugin marketplace add glbessa/rebanho-facil-plugin
claude plugin install rebanho-facil@rebanho-facil
```

Codex:

```bash
codex plugin marketplace add glbessa/rebanho-facil-plugin
codex plugin add rebanho-facil@rebanho-facil
```

## Licença

MIT. O plugin é aberto; o serviço Rebanho Fácil é um produto pago.
