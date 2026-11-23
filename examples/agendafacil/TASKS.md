# Tasks

Tamanhos são estimativas relativas, não prazos.

## Phase 1: Walking skeleton
- [ ] **T1.1 Projeto Laravel com CI** (S) · depends: none
  What: criar o projeto, configurar testes e pipeline.
  Done when: o pipeline roda os testes verdes a cada push.

- [ ] **T1.2 Agendamento mínimo ponta a ponta** (M) · depends: T1.1
  Feature: Página pública de agendamento
  What: uma página que lista horários fixos e grava um agendamento.
  Done when: na URL de staging, um agendamento criado aparece no banco.

- [ ] **T1.3 Deploy em staging** (S) · depends: T1.2
  What: publicar a aplicação com migrações automáticas.
  Done when: a URL de staging responde 200 e o agendamento do T1.2 funciona lá.

## Phase 2: Must features
- [ ] **T2.1 Login do dono** (S) · depends: T1.1
  Feature: Login do dono
  What: cadastro e login por e-mail e senha, com proteção das rotas de `/admin`.
  Done when: sem login, `/admin` redireciona; com login, abre o painel.

- [ ] **T2.2 Cadastro de serviços e profissionais** (M) · depends: T2.1
  Feature: Cadastro de serviços, profissionais e horários
  What: telas para criar, editar e remover serviços, profissionais e horário de atendimento.
  Done when: o dono cadastra um serviço e um profissional e eles aparecem na página pública.

- [ ] **T2.3 Cálculo de horários livres** (M) · depends: T2.2
  Feature: Bloqueio de horários ocupados
  What: `SlotCalculator` com duração do serviço, horário de atendimento e agendamentos existentes.
  Done when: testes unitários cobrem encaixe, borda do expediente e horário ocupado.

- [ ] **T2.4 Agendamento sem marcação dupla** (M) · depends: T2.3
  Feature: Bloqueio de horários ocupados
  What: restrição única no banco e tratamento do erro na página pública.
  Done when: um teste com duas requisições simultâneas para o mesmo horário cria só um agendamento.

- [ ] **T2.5 Agenda do dia e da semana** (M) · depends: T2.4
  Feature: Agenda do dia e da semana para o dono
  What: lista por dia e visão semanal com nome, telefone e serviço.
  Done when: o dono vê os agendamentos criados pela página pública, em ordem de horário.

## Phase 3: Should features and hardening
- [ ] **T3.1 Texto de consentimento e exclusão de dados** (S) · depends: T2.4
  What: aviso na página pública e comando para apagar os dados de um cliente.
  Done when: o aviso aparece antes de confirmar e o comando remove os dados do cliente.

- [ ] **T3.2 Cancelamento pelo cliente por link** (M) · depends: T2.4
  Feature: Cancelamento pelo cliente
  What: link único por agendamento que o cancela e libera o horário.
  Done when: o horário volta a aparecer livre após o cancelamento.

- [ ] **T3.3 Lembrete por WhatsApp** (L) · depends: T3.2
  Feature: Lembrete por WhatsApp
  What: escolher o provedor, enviar o lembrete um dia antes por tarefa agendada.
  Done when: um agendamento de teste recebe a mensagem no número de teste.

## Phase 4: Release
- [ ] **T4.1 Produção e piloto** (M) · depends: T2.5, T3.1
  What: publicar em produção, configurar backup e cadastrar a barbearia piloto.
  Done when: a barbearia piloto recebe um agendamento real pela página.

- [ ] **T4.2 README do projeto** (S) · depends: T4.1
  What: gerar o README com `/diazero:readme`.
  Done when: o README explica instalação, uso e deploy.

## Backlog (Could and Won't)
- Relatório mensal de faltas
- Várias unidades por conta
- Pagamento online (Won't)
- App nativo (Won't)
