# Публикация VK Base

VK Base — отдельный статический проект. Код основного iiai.pro не используется и не изменяется.

## 1. GitHub Actions secrets

В репозитории `TopcuoH/vkbase` добавьте:

- `VKBASE_SSH_HOST` — IP/hostname сервера;
- `VKBASE_SSH_USER` — SSH-пользователь;
- `VKBASE_SSH_KEY` — приватный SSH-ключ пользователя для деплоя.

У пользователя должны быть права записи только в `/srv/vkbase/current/`.

## 2. Nginx

В конфигурации существующего домена iiai.pro добавляется только route из `nginx-vkbase.conf`.

После изменения:

```bash
nginx -t
systemctl reload nginx
```

Основное приложение iiai.pro не перезаписывается и не смешивается с VK Base.

## 3. Обновления

Каждый push в `main` автоматически синхронизирует статические файлы в `/srv/vkbase/current/`.

Целевой адрес:

`https://iiai.pro/vkbase/`
