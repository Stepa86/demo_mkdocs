# Главная

Демонстрация работы автогенерации сайта на [github-pages](https://pages.github.com/)/[gitlab.pages](https://docs.gitlab.com/ee/user/project/pages/) с использованием [mkdocs](https://www.mkdocs.org/).

## Что же это?

Пишите страницы в [markdown](https://ru.wikipedia.org/wiki/Markdown), а генератор статичного сайта [mkdocs](https://www.mkdocs.org/) с темой [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) соберут нестыдный статичный сайт с оформлением, навигацией, поиском, содержанием и тп. А если использовать [github-pages](https://pages.github.com/) или [gitlab.pages](https://docs.gitlab.com/ee/user/project/pages/), то этот сайт автоматически соберется, опубликуется и будет доступен с учетом видимости проекта.

## Как включить пайплайн по генерации сайта на github-pages

1. Готовый файл пайплайна уже есть в репозитории: [.github\workflows\gh-pages.yml](https://github.com/Stepa86/demo_mkdocs/blob/master/.github/workflows/gh-pages.yml)

2. В настройках репо нужно включить использование Actions. https://github.com/<путь к репо>/settings/actions . Для этого репо путь такой, но у вас нет прав на настройки: https://github.com/Stepa86/demo_mkdocs/settings/actions

   ![image-20210102180048869](index.assets/image-20210102180048869.png)

3. После пуша в мастер (если вы не меняли триггер для запуска пайплайна) запустится сборка и через некоторое время будет опубликован статический сайт. Адрес сайта можно посмотреть в настройках https://github.com/<путь к репо>/settings.

   ![image-20210102175958453](index.assets/image-20210102175958453.png)

## Как включить пайплайн по генерации сайта на gitlab.pages

## Полезное ПО


## Примеры статей

- [Добавление новой статьи](checklists/New_page.md)

## Прочее

[Все статьи](SUMMARY.md)
