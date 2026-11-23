# AgendaFácil

> Agendamento online para barbearias pequenas, sem app para o cliente instalar.

**Status:** planning · **Target:** version 1 · **Language:** pt-BR

## Problem
Barbearias com 1 a 4 cadeiras marcam horários por WhatsApp. Perdem clientes por demora na resposta, trocam dezenas de mensagens para fechar um horário e têm faltas sem aviso.

## Users
- **Dono da barbearia:** quer a agenda cheia, menos faltas e menos tempo no WhatsApp.
- **Cliente:** quer marcar em menos de um minuto, pelo celular, sem criar conta.

## Scope (MoSCoW)
**Must (version 1)**
- Página pública de agendamento por barbearia — é a entrada de todos os clientes
- Cadastro de serviços, profissionais e horários de atendimento — sem isso não há o que agendar
- Agenda do dia e da semana para o dono — é o valor que ele vê todo dia
- Bloqueio automático de horários já ocupados — evita marcação dupla
- Login do dono por e-mail e senha — protege a agenda

**Should**
- Lembrete por WhatsApp um dia antes
- Cancelamento pelo cliente por link

**Could**
- Relatório mensal de faltas e horários mais cheios
- Várias unidades por conta

**Won't (for now)**
- Pagamento online — aumenta muito o risco jurídico e o prazo
- App nativo — a página no celular resolve a versão 1
- Fidelidade e cupons — não resolve a dor principal

## Constraints
- Prazo: 6 semanas, uma pessoa, meio período.
- Orçamento: até R$ 100 por mês de hospedagem e serviços.
- Hospedagem em servidor compartilhado ou VPS pequena (verify o plano escolhido).

## Success criteria
- Uma barbearia piloto recebe 20 agendamentos reais pela página em 2 semanas.
- Um cliente conclui o agendamento em menos de 60 segundos em um celular de entrada.
- Zero marcações duplas no piloto.

## Risks (pre-mortem)
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Donos não largam o WhatsApp | high | high | Link da página para colocar na bio e na resposta automática do WhatsApp |
| Dados pessoais de clientes (LGPD) | med | high | Coletar só nome e telefone, texto de consentimento, exclusão sob pedido |
| Marcação dupla por concorrência | med | high | Restrição única no banco e teste de duas requisições simultâneas |
| Escopo cresce com pedidos do piloto | high | med | Todo pedido novo passa por `/diazero:refine` e entra no backlog |
| Prazo estoura com o lembrete por WhatsApp | med | med | Lembrete é Should; o provedor só é escolhido após a fase 2 |

## Assumptions
- 1 barbearia por conta no início (confirmar)
- Horário de atendimento igual em todos os profissionais (confirmar)
- Cliente informa só nome e telefone; sem e-mail

## Open questions
- Qual provedor de WhatsApp será usado para lembretes? (decidir antes da fase 3)

## Change log
- 2026-01-10: created
