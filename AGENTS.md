# AGENTS.md

## Project

MiniBook is a Laravel 12 web app for booking minisoccer fields at Minisoccer Ngabang (Kalimantan Barat). The repo is still a fresh Laravel skeleton: no booking-domain code, auth scaffolding, or UI beyond the default welcome page. Build the domain from the docs; don't assume an existing implementation.

## Sources of truth

Read these before implementing anything:

- `agent/prd.md` — product requirements, roles, business rules, and data model (Indonesian).
- `agent/design.md` — UI/UX spec; mandates **Bootstrap 5**, Indonesian copy, and the design tokens/components in §2 and §6.
- `agent/task-instruction.md` — workflow and task checklist rules.

The docs are in `agent/`, not `.agents/` (despite `agent/readme.md`). Root `README.md` is the default Laravel readme.

## Commands

```bash
composer install
npm install
php artisan migrate --seed
php artisan serve        # plus `npm run dev` in a second terminal
php artisan test
php artisan test --filter=ExampleTest
vendor/bin/pint <path>   # format only changed files
```

- Start MySQL first. `.env` uses MySQL at `127.0.0.1:3306`, database `futsal-booking`, user `root`. `.env.example` defaults to SQLite, and `database/database.sqlite` is empty/unused; create the MySQL database before migrating.
- `composer dev` is defined but **fails on this Windows setup**: it runs `php artisan pail`, which requires the `pcntl` extension (not available). Run `php artisan serve` + `npm run dev` separately; add `php artisan queue:listen` if queue jobs are used.
- `phpunit.xml` does not override the DB, so `php artisan test` uses the `.env` MySQL database `futsal-booking`. The commented SQLite `:memory:` block won't work here because `pdo_sqlite` is not enabled. Before adding `RefreshDatabase`/DB tests, point `DB_DATABASE` at a separate MySQL test database (or enable `pdo_sqlite`); otherwise tests will wipe dev data.
- `vendor/bin/pint --test` currently fails on untouched Laravel files (`app/Models/User.php`, `bootstrap/providers.php`, `config/auth.php`, `database/factories/UserFactory.php`). Don't mass-format; format only files you change.
- No CI, JS lint, or typecheck scripts are configured. `php artisan test` and Pint are the available checks.

## UI and product constraints

- Follow `agent/design.md` over the scaffold: it requires **Bootstrap 5 + Blade**, but the repo currently ships **Tailwind 4** (`resources/css/app.css`, `vite.config.js`) and no Bootstrap. Add Bootstrap 5 rather than building the UI with Tailwind.
- UI copy is **Bahasa Indonesia**. Use the MiniBook palette, status labels, and layout patterns from `design.md`.
- Current config is still Laravel defaults (`APP_NAME=Laravel`, locale `en`, timezone `UTC`), while the product is MiniBook in WIB (UTC+7). Align branding, locale, and timezone before implementing schedule/booking logic.

## Open decisions

`agent/prd.md` §16 and `agent/design.md` §10 list unresolved requirements. Do not silently hard-code choices for:

- 50% down payment vs full payment;
- booking status names/transitions and the rejection flow;
- whether customers need accounts/login;
- tariff time ranges (18:00–22:00 vs 18:00–23:00) and the student discount;
- email confirmation and digital-ticket fields.

Keep rates, slots, and bank account details configurable and flag decisions instead of inventing final values.

## Task tracking

`agent/task-instruction.md` requires updating `.agents/tasklist.md` after each task: mark `[x] ✅`, update overall progress %, and note files changed. That file/folder does not exist yet; create it when starting work.
