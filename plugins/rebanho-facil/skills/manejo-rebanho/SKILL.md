---
name: manejo-rebanho
description: Como operar o Rebanho Fácil pelas tools MCP. Use quando o usuário falar de gado, rebanho, fazenda, brinco, pesagem, GPD, vacina, medicamento, carência, IATF, prenhez, parto, lote, piquete, pasto ou despesas e receitas da fazenda.
---

# Manejo do rebanho no Rebanho Fácil

As tools do servidor `rebanho-facil` leem e gravam na conta real do produtor.
Trate cada escrita como lançamento definitivo.

## Antes de tudo

1. Chame `list_farms` e descubra o `farm_id`. Se houver mais de uma fazenda e o
   usuário não disse qual, pergunte. Depois disso, reaproveite o mesmo `farm_id`.
2. O produtor fala em brinco, não em id. Use `get_animal` com `tag` (ou `sisbov`,
   `eid`) para achar o animal. Se `list_animals` devolver mais de um candidato,
   mostre as opções e pergunte.
3. Lote e campo também são falados pelo nome: resolva com `list_lots` e
   `list_fields` antes de mover ou vincular.

## Escritas

- Mais de um animal no mesmo manejo: use a versão em lote
  (`record_weighings_batch`, `record_medications_batch`, `create_animals_batch`,
  `record_births_batch`, `record_pregnancy_diagnoses_batch`,
  `update_animals_batch`). Uma chamada por animal é lenta e polui a auditoria.
- Datas em `AAAA-MM-DD`. "Hoje" e "ontem" são relativos à data atual do
  usuário. Peso em kg; valores em reais.
- Antes de qualquer `delete_*`, confirme com o usuário dizendo o que será
  apagado. Animal com histórico não se apaga: registre baixa com
  `register_animal_exit` ou `register_animal_death`.
- Se a tool responder `erro`, mostre a mensagem ao usuário em vez de tentar de
  novo com dados inventados. Usuário com papel de visualizador não grava.
- Ao terminar, resuma o que foi gravado (quantos registros, animais, datas).

## Consultas úteis

- Desempenho: `get_animal` já traz pesagens e GPD; não repita chamadas.
- Venda ou abate: confira `list_withdrawal_periods` antes. Animal em carência
  não pode ir para abate e o usuário precisa saber.
- Pendências do dia: `list_alerts`, `list_pending_vaccinations`,
  `list_protocol_schedule` e `list_field_tasks`.
- Financeiro: `get_financial_summary` para visão geral; `list_expenses`,
  `list_revenues` e `list_cash_flow_entries` para detalhe.

## Tom

Responda em português do Brasil, direto, como quem conversa com gente do campo.
Nada de jargão técnico de sistema (ids, JSON, nomes de tool) na resposta.
