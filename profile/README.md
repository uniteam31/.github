# UNISHARE — Моно‑README для микрофронтов & бэкендов

---

## 📜 Содержание

1. [Живые стенды и сервисы](#живые-стенды-и-сервисы)
2. [Обзор архитектуры](#обзор-архитектуры)
3. [Репозитории фронта](#репозитории-фронта)
4. [Репозитории бэкенда](#репозитории-бэкенда)
5. [Шареные пакеты](#шареные-пакеты)
6. [Git Flow](#git-flow)
7. [CI/CD](#cicd)
8. [Кодстайл и практики](#кодстайл-и-практики)

---

## Живые стенды и сервисы

| Сервис        | URL                                                                                      | Примечание                      |
| ------------- | ---------------------------------------------------------------------------------------- | ------------------------------- |
| DEV стенд     | [https://dev.unishare.example](https://dev.unishare.example)                             | auto‑deploy                     |
| Jenkins CI/CD | *[http://176.114.90.241:8080/](http://176.114.90.241:8080/)*                             | пайплайны для всех репозиториев |
| JIRA          | *[https://uniteam31.atlassian.net/jira](https://uniteam31.atlassian.net/jira/your-work)* | задачи и roadmap                |

---

## Обзор архитектуры

- **Frontend‑shell** (`unishare-frontend`) грузит микрофронты через **Module Federation**.
- **Бандлер / Dev‑server** — Webpack 5 + webpack‑dev‑server.
- **Backend** (`unishare-backend`) — единый **REST‑API** сервис (Node.js + NestJS).
- **Orchestration** (`unishare-orchestration`) деплоит всё через dockerhub.
- **Пакетный менеджер** — **Yarn classic (1.x)**.

---

## Репозитории фронта

**Общий стек микрофронтов:** React 18 · TypeScript · Webpack 5 · Storybook 8 · SCSS · SWR · Zustand

| Repo                                                                                  | Demo                                                     | Additional stack         | Описание                                                             |
| ------------------------------------------------------------------------------------- | -------------------------------------------------------- | ------------------------ | -------------------------------------------------------------------- |
| [`unishare-frontend`](https://github.com/uniteam31/unishare-frontend)                 | [https://dev.unishare.space](https://dev.unishare.space) | —                        | Хост‑приложение (Module Federation host); динамически монтирует MFEs |
| [`unishare-spaces`](https://github.com/uniteam31/unishare-spaces)                     | —                                                        | —                        | Управление «пространствами»                                          |
| [`unishare-disk`](https://github.com/uniteam31/unishare-disk)                         | —                                                        | dnd-kit, Radix UI        | Файловое хранилище                                                   |
| [`unishare-notes`](https://github.com/uniteam31/unishare-notes)                       | —                                                        | Tiptap, React Icons      | Заметки и документы                                                  |
| [`unishare-calendar`](https://github.com/uniteam31/unishare-calendar)                 | —                                                        | FullCalendar, Ant Design | Календарь событий                                                    |
| [`unishare-friends`](https://github.com/uniteam31/unishare-friends)                   | —                                                        | —                        | Социальный граф                                                      |
| [`unishare-account-settings`](https://github.com/uniteam31/unishare-account-settings) | —                                                        | —                        | Настройки аккаунта                                                   |

## Репозитории бэкенда

| Repo                                                                            | Stack                                               | Описание                               |
| ------------------------------------------------------------------------------- | --------------------------------------------------- | -------------------------------------- |
| [`unishare-backend`](https://github.com/uniteam31/unishare-backend)             | Node.js, NestJS, TypeScript, Postgresql, prisma orm | Core **REST API** (auth, users, files) |
| [`unishare-orchestration`](https://github.com/uniteam31/unishare-orchestration) | Docker compose, Shell                               | CI‑helper‑скрипты                      |

---

## Шареные пакеты

| Repo                                                                    | Version | Описание                      |
| ----------------------------------------------------------------------- | ------- | ----------------------------- |
| [`uni-shared-ui`](https://github.com/uniteam31/uni-shared-ui)           | `^0.x`  | Design‑system и UI‑компоненты |
| [`uni-shared-toolkit`](https://github.com/uniteam31/uni-shared-toolkit) | `^0.x`  | Хелперы, утилиты, state‑tools |
| [`uni-shared-types`](https://github.com/uniteam31/uni-shared-types)     | `^0.x`  | Общие TypeScript‑типы         |

---

## Git Flow

- Основные ветки: `dev` → `main`.
- Каждая задача в **JIRA** → ветка `UNISHARE-<ID>`.
- Коммиты: `UNISHARE-42: краткое описание`.
- PR **всегда** в `dev`; CI: lint → тесты → build.
- Мёрж `dev` → автодеплой на DEV‑стенд.

---

## CI/CD

1. **Jenkinsfile** в каждом репозитории.
2. Стейджи: *install* → *lint/test* → *build* → *docker push* → *deploy*.
3. Secrets через Jenkins credentials; `.npmrc` для private registry.

---

## Кодстайл и практики

- **ESLint + Prettier + Stylelint** — настроены в каждом проекте.
- **I/T‑префиксы** в TS (`IUser`, `TUserPayload`).
- Feature‑Sliced Design, React hooks.
- **SWR** для GET, custom hooks для мутаций.
- Короткие функции, говорящие имена, минимум «магии».

---

