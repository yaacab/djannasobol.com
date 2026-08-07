# Как править сайт из ChatGPT (iPhone) и сразу видеть на djannasobol.com

## Как это работает

1. ChatGPT меняет файлы в репозитории `yaacab/djannasobol.com` (обычно `index.html`).
2. Push в ветку `main` запускает GitHub Action **Deploy site**.
3. Action заливает `index.html` на сервер → через ~1 минуту обновление на https://djannasobol.com

Без secrets для деплоя правки останутся только на GitHub.

## Секреты (один раз в GitHub)

Repo → **Settings** → **Secrets and variables** → **Actions** → New repository secret:

| Secret | Пример |
|--------|--------|
| `DEPLOY_HOST` | `193.29.224.1` |
| `DEPLOY_USER` | `root` |
| `DEPLOY_SSH_KEY` | приватный SSH-ключ целиком (`-----BEGIN … KEY-----` …) |
| `DEPLOY_PATH` | `/var/www/djannasobol/index.html` (опционально) |
| `DEPLOY_PORT` | `22` (опционально) |

Ключ должен уметь заходить на этот хост и писать в каталог сайта. Не коммитьте ключ в репозиторий.

## Текст для ChatGPT (скопировать)

```
Репозиторий: yaacab/djannasobol.com
Сайт в проде: https://djannasobol.com

Правила:
1) Меняй только файлы этого репозитория (главное — index.html). Не трогай другие репозитории и не проси VPN/секреты/.env.
2) После правок обязательно закоммить и запушь в ветку main.
3) Дождись успешного GitHub Action "Deploy site" (или скажи мне проверить Actions).
4) Итог для меня: что изменил + что открыть на сайте (Ctrl+F5).

Задача сейчас:
<опиши правку своими словами>
```

## Проверка

- GitHub → вкладка **Actions** → workflow **Deploy site** зелёный.
- На телефоне открой https://djannasobol.com и обнови страницу.
