# AgendaFácil

## What this is
Agendamento online para barbearias pequenas, sem app para o cliente instalar.
Versão 1: página pública de agendamento e painel do dono.

## Stack
- Laravel + Livewire
- MySQL
- GitHub Actions para CI

## Commands
- Instalar: `composer install && npm install`
- Rodar: `php artisan serve`
- Testar: `php artisan test`
- Lint: `./vendor/bin/pint --test`
- Build: `npm run build`

## Structure
- `app/Models/`: Barbershop, Professional, Service, Appointment
- `app/Livewire/Public/`: página pública de agendamento
- `app/Livewire/Admin/`: painel do dono
- `app/Services/`: regras de negócio, como o `SlotCalculator`
- `database/migrations/`: esquema do banco
- `tests/`: Unit para regras, Feature para fluxos

## Conventions
- Regras de horário ficam em `app/Services`, nunca dentro de componentes Livewire.
- Valores em centavos; datas em UTC no banco.
- Follow ARCHITECTURE.md. Ask before changing the stack or the data model.

## How to work here
1. Read TASKS.md and take the first unchecked task whose dependencies are done.
2. One task at a time, with small diffs.
3. Run tests and lint before marking a task done. Mark it `[x]` and add a one-line note.
4. If the scope changes, stop and use /diazero:refine instead of editing the plan silently.

## Definition of done
Testes e lint passam, o "done when" da tarefa foi verificado e a tarefa foi marcada em TASKS.md.

## Do not
- Não adicionar pagamento online na versão 1.
- Não criar conta para o cliente final.
- Não coletar outros dados pessoais além de nome e telefone.
