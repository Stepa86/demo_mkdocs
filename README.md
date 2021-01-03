# Главная

Демонстрация работы автогенерации сайта на [github-pages](https://pages.github.com/)/[gitlab.pages](https://docs.gitlab.com/ee/user/project/pages/) с использованием [mkdocs](https://www.mkdocs.org/).

Лучше читать эту страницу на [https://stepa86.gitlab.io/demo_mkdocs/](https://stepa86.gitlab.io/demo_mkdocs/)

## Что же это?

Пишите страницы в [markdown](https://ru.wikipedia.org/wiki/Markdown), а генератор статичного сайта [mkdocs](https://www.mkdocs.org/) с темой [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) соберут нестыдный статичный сайт с оформлением, навигацией, поиском, содержанием и тп. А если использовать [github-pages](https://pages.github.com/) или [gitlab.pages](https://docs.gitlab.com/ee/user/project/pages/), то этот сайт автоматически соберется, опубликуется и будет доступен с учетом видимости проекта.

## GitHub Pages

Смотрите пример репозитория на GitHub [https://github.com/Stepa86/demo_mkdocs/](https://github.com/Stepa86/demo_mkdocs/) и пример сайта [https://stepa86.github.io/demo_mkdocs/](https://stepa86.github.io/demo_mkdocs/)

1. Готовый файл пайплайна уже есть в репозитории: [.github\workflows\gh-pages.yml](https://github.com/Stepa86/demo_mkdocs/blob/master/.github/workflows/gh-pages.yml)

2. В настройках репо нужно включить использование Actions. `https://github.com/<username>/<repository>/settings/actions` . Для этого репо путь такой, но у вас нет прав на настройки: https://github.com/Stepa86/demo_mkdocs/settings/actions

    [![Setting-GA][1]][1]

3. После пуша в мастер (если вы не меняли триггер для запуска пайплайна) запустится сборка и через некоторое время будет опубликован статический сайт `<username>.github.io/<repository>`. Адрес сайта можно посмотреть в настройках `https://github.com/<username>/<repository>/settings`.

    [![Setting-GP][2]][2]

Так же смотрите инструкцию на странице [mkdocs-material](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#github-pages)

  [1]: docs/index.assets/Setting-GA.png
  [2]: docs/index.assets/Setting-GP.png

## GitLab Pages

Смотрите пример репозитория на GitLab [https://gitlab.com/Stepa86/demo_mkdocs](https://gitlab.com/Stepa86/demo_mkdocs) и пример сайта [https://stepa86.gitlab.io/demo_mkdocs/](https://stepa86.gitlab.io/demo_mkdocs/)

1. Готовый файл пайплайна уже есть в репозитории: [.gitlab-ci.yml](https://gitlab.com/Stepa86/demo_mkdocs/-/blob/master/.gitlab-ci.yml)
2. После пуша в мастер запустится сборка и публикация. Сайт будет опубликован по адресу `<username>.gitlab.io/<repository>`
3. При мерж-реквестах будет выполнятся тестирование - будут проверены ссылки на их существование и корректность настроек

Так же смотрите инструкцию на странице [mkdocs-material](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#gitlab-pages)

## Локальный веб-сервер

Должен быть установлен python.

### Установка python

[Скачиваем](https://www.python.org/) питон. Запускаем выборочную установку.

[![install-python1][3]][3]

Снимаем все галочки, кроме pip.

[![install-python2][4]][4]

Снимаем все, кроме добавления в переменные окружения.

[![install-python3][5]][5]

Можно тыкнуть в отключение лимитов в длине пути, но это не обязательно (но это не точно).

  [3]: docs/index.assets/install-python1.png
  [4]: docs/index.assets/install-python2.png
  [5]: docs/index.assets/install-python3.png

### Установка/обновление библиотек

Запустить в корне репозитория `pip_Install_update.bat` или в командной строке выполнить следующий код:

```cmd
pip install --upgrade mkdocs mkdocs-material pygments-bsl pymdown-extensions mkdocs-minify-plugin mkdocs-awesome-pages-plugin mkdocs-git-revision-date-localized-plugin
```

[![pip_Install_update][6]][6]

В конце должна появится надпись, что нас достиг саксесс.

  [6]: docs/index.assets/pip_Install_update.gif

### Запуск сервиса локально

В корне репозитория запускаем `mkdocs_serve.bat` или в командной строке, находясь в корне репозитория:

```cmd
mkdocs serve
```

[![mkdocs_serve][7]][7]

  [7]: docs/index.assets/mkdocs_serve.gif

На первое предупреждение не пугаемся. Через некоторое время будет выведено сообщение, что сервер поднят по адресу [http://127.0.0.1:8000/](http://127.0.0.1:8000/) и включено отслеживание изменений.

Отслеживание изменений означает, что после каждого сохранения файла в репозитории - статьи, вспомогательных файлов или настроечных - сайт будет сам пересобираться и выводить уже обновленную статью.

Через поднятый локальный сервер удобно смотреть на верстку сайта и контролировать ошибки в настройках, потерянные ссылки итп.

Когда сервер больше не нужен - достаточно закрыть окно комадной панели.

### Не страшное предупреждение has no git logs, using current timestamp

Когда создана новая статья, но еще не закоммичена, то сервер ругается вот так:
[![image-20200610201757936][8]][8]
На него можно не обращать внимание или просто закоммитить изменения и предупреждение уйдет.

### Предупреждение о битой ссылке

Такое предупреждение означает, что в файле `knowledge\Posts\New_page_checklist.md` есть ссылка на файл `knowledge\Posts\test.md`, но самого этого файла не существует. Это битая ссылка и гитлаб не даст влить такую статью. Убедитесь, что регистр букв совпадает и слеши правильные.
[![image-20200610202108342][9]][9]

### Ошибка в файле .pages

Если в файле `.pages` ошибка, то выскочет такая страшная штука, где указано, что в файле `E:\GIT_Repo\Konstanta\wiki\docs\knowledge\Posts\.pages` неправильно указан порядок, т.к. файл `New_post1.md` не найден.
[![image-20200610202418995][10]][10]

  [8]: docs/index.assets/image-20200610201757936.png
  [9]: docs/index.assets/image-20200610202108342.png
  [10]: docs/index.assets/image-20200610202418995.png

## Полезное ПО

## Примеры

- [Добавление новой статьи](https://stepa86.gitlab.io/demo_mkdocs/checklists/New_page.md)
- Список сайтов на [mkdocs-material](https://github.com/squidfunk/mkdocs-material#users)
- [BSL Language Server](https://1c-syntax.github.io/bsl-language-server/)
- [About-tests-in-1C](https://stepa86.github.io/About-tests-in-1C/)

## Известные проблемы

### Оглавление не отображается

Чтобы оглавление отображалось нужно:

1. Оно не должно быть отключено через метаданные или настойки
2. Должна быть правильная структура файла. Должен быть заголовок `# Заголовок страницы` и `## Заголовки разделов первого уровня`. Именно по заголовкам раздела строится оглавление.
3. Если включена опция отображения оглавления встроенная в навигацию (`toc.integrate`), то для вывода оглавления страница должна входить в навигацию - то есть слева должна отображаться иерархия страниц

### Картинки в gh-pages не отображаются, а при `mkdocs serve` и в других местах все нормально

Эксперементальным путем выяснил, что дело в LFS. Если картинки не включать в LFS, то они начинают отображаться.

## Использовано:

https://www.mkdocs.org/

https://github.com/squidfunk/mkdocs-material

https://material.io/resources/icons/
