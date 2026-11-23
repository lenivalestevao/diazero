# Example: the quality bar

A condensed set of the four files for a made-up project. It shows the level of specificity expected. Do not copy its content. A full, unabridged set lives in `examples/agendafacil/` at the repository root (not shipped as a skill file).

## PROJECT.md (excerpt)

```markdown
# AgendaFácil

> Agendamento online para barbearias pequenas, sem app para o cliente instalar.

**Status:** planning · **Target:** version 1 · **Language:** pt-BR

## Problem
Barbearias com 1 a 4 cadeiras marcam horários por WhatsApp. Perdem clientes por demora na resposta e têm faltas sem aviso.

## Users
- Dono da barbearia: quer a agenda cheia e menos faltas.
- Cliente: quer marcar em menos de um minuto, pelo celular.

## Scope (MoSCoW)
**Must (version 1)**
- Página pública de agendamento por barbearia — é a entrada de todos os clientes
- Cadastro de serviços, profissionais e horários — sem isso não há o que agendar
- Agenda do dia para o dono — é o valor que ele vê

**Should**
- Lembrete por WhatsApp um dia antes

**Won't (for now)**
- Pagamento online — aumenta muito o risco jurídico e o prazo

## Risks (pre-mortem)
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Donos não largam o WhatsApp | high | high | Link da página para colocar na bio e na resposta automática |
| Dados pessoais de clientes (LGPD) | med | high | Coletar só nome e telefone, texto de consentimento, exclusão sob pedido |

## Assumptions
- 1 barbearia por conta no início (confirmar)
```

## ARCHITECTURE.md (excerpt)

```markdown
## Stack
| Layer | Choice | Why |
|---|---|---|
| Backend and UI | Laravel + Livewire | O desenvolvedor já domina, entrega rápida |
| Database | MySQL | Já disponível na hospedagem escolhida |

## Decisions
| ID | Decision | Why | Rejected alternatives | Revisit when |
|---|---|---|---|---|
| D1 | Monolito Laravel | Time de uma pessoa | API separada + SPA | Mais de 3 desenvolvedores |
```

## TASKS.md (excerpt)

```markdown
## Phase 1: Walking skeleton
- [ ] **T1.1 Projeto Laravel com CI** (S) · depends: none
  What: criar o projeto, configurar testes e pipeline.
  Done when: o pipeline roda os testes verdes a cada push.

- [ ] **T1.2 Agendamento mínimo ponta a ponta** (M) · depends: T1.1
  Feature: Página pública de agendamento
  What: uma página que lista horários fixos e grava um agendamento.
  Done when: na URL de staging, um agendamento criado aparece no banco.
```

## CLAUDE.md (excerpt)

```markdown
## Commands
- Instalar: `composer install && npm install`
- Rodar: `php artisan serve`
- Testar: `php artisan test`

## Do not
- Não adicionar pagamento online na versão 1.
```
