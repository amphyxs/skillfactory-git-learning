# Документация по git

## Начало

Репозиторий располагается на GitHub:
https://github.com/amphyxs/skillfactory-git-learning

Для развёртывания репозитория у себя нужно:

1. Сообщить @amphyxs свой email для получения приглашения в коллабораторы репо
2. Выполнить:

```sh
git clone https://github.com/amphyxs/skillfactory-git-learning.git
```

3. Перейти в директорию проекта и в файле git-config заменить имя, фамилию, email на свой, затем исполнить:

```sh
mv git-config .git/config
```

## Внесение своих изменений

Нужно создать ветку под задачу (см. Правила, чтобы понять, как именовать):

```sh
git checkout master
git pull
git branch 1101-my-branch
```

По мере внесения изменений создавать коммиты:

```sh
git add .
git commit -m "[1101] Add new feature for page navigation"
```

## Правила

Ветки именуются так: `<номер-задачи-в-Jira>-<имя-ветки>`
Пример: `1415-fix-critical-error-on-login-page`

Рекомендуется добавлять сообщения к коммитам в следующем формате: `[<номер-задачи-в-Jira>]<описание-коммита-на-английском-начиная-глаголом-в-инфинитиве>`
Пример (если у нас ветка `1415-fix-critical-error-on-login-page`): `[1415] Fix bad database query`

## Настройка

Если у вас VSCode, то он сам обнаружит репозиторий и сконфигурирует его.

## Слияние веток

Когда готовы открыть пулл-реквест:

```sh
git push
```

Также нужно залить ваши изменения на ветку теста:
```sh
git checkout testing
git pull
git merge origin/1101-my-branch
git push origin testing
```

GitHub предложит открыть pull-request: открываем, именуем как ветку, но без тире (1101-my-branch -> [1101] My branch)
Дальше запустится CI: линт, тесты, деплой.

Если всё успешно пройдено, запрашивайте ревью у вашего лида.
После того, как он апрувнет PR, он сам вольёт его в `master`.
В `master` не пушим, делаем мердж через PR на GitHub.
