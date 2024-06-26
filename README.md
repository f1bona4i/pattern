# Шаблон для LaTeX

Подойдет для простеньких курсовых, обзора литературы и т.п. и т.д.
Для публикации в журналах, для соискания научной степени, даже для дипломной работы, скорее всего не подойдёт.

## Быстрый старт

### Использование Overleaf

1. Скачайте архив с проектом
2. Откройте Overleaf
3. Нажмите на **New Project**, выберите **Upload Project**
4. Загрузите архив с шаблоном
5. Выберите необходимый компилятор (Menu \ Settings \ Compiler \ (pdfLaTex, XeLaTeX, LuaLaTex))
6. Можете начинать творить

### Использование offline сред

1. Скачайте архив с проектом
2. Разархивируйте в какую-либо папку
3. Откройте папку как проект через вашу среду разработки
4. Выберите необходимый компилятор (pdfLaTex,XeLaTeX, LuaLaTex)
5. Можете начинать творить

## Параметры и пакеты

Основные настройки пакетов в файле "packeges.tex", там же настройки biblatex.
Используются пакеты:

- fontenc[T2A], inputenc[utf8x], babel — Поддержка русского и английского языков, кодировок и шрифтов
- indentfirst, setspace — Форматирование текста
- amsmath, amssymb, gensymb, amsthm, mathtext, amsmath — Математические символы и уравнения
- graphicx, svg, pst-all, pstricks-add, chngcntr, caption, xcolor — Графика и рисунки
- hyperref — Гиперссылки и навигация
- chngcntr — Управление нумерацией (подробнее в "packeges.tex")
- biblatex — Цитирование и списки литературы
- listings — Листинг кода

## Формат документа

Параметры старались подбираться максимально приближенные к российским гостам.

- Шрифт стандартный (см. ниже для Times New Roman)
- Размер шрифта 14pt
- Лист А4
- Поля: слева 3см, справа 1.5см, сверху 2см, снизу 2см
- Междустрочный интервал 1.5
- Отступ для абзаца 1.25см
- Шрифт для url-ссылок такой же как у основного текста
- Перенос текста при переполнении 25pt

## Цитирование

Для цитирования используется пакет biblatex, позволяющий в автоматическом режиме делать список литературы.

В шаблоне используется российский гост для оформления цитирования и списка литературы.

Для настройки сортировки зайдите в "packeges.tex" и удалите комментарий для нужного формата сортировки, остальное закомментируйте или удалите.

Для настройки отображения списка литературы перейдите в файл "bibz.tex":

- \nocite{\*} — отвечает за отображение **ВСЕХ** статей из списка литературы. Если вам нужно отображать только то, что использовалось в работе, удалите эту строчку.
- heading=bibintoc — добавляет список литературы в оглавление. Если вам не нужен список литературы в оглавлении, то удалите этот параметр.
- title={ИСТОЧНИКИ} — отвечает за то, как будет отображаться название списка литературы. Если вам нужно изменить название, то меняйте "ИСТОЧНИКИ" на нужное Вам.

## Листинг кода (В поиске стиля)

Для листинга кода используется пакет listings.
Стиль листинга можно настроить в файле "listing.tex".

Для листинга кода можно использовать два метода.

- Вставка кода из файла.
- Вставка кода в tex документ.

Больше информации в FAQ.

## Макросы и переопределения

Основные переопределения и макросы находятся в файле "macros.tex"

Сразу переопределён стиль вложенного нумерованного списка.

## Оглавление

Классическое оглавление. Включает в себя все секции, подсекции, подподсекции, список литературы.
Настройки в файле "toc.tex"

## Титульный лист

Титульный лист не можете заменить на свой, либо отредактировать имеющийся. Все настройки титульного находятся в файле "title.tex".

По умолчанию используется логотип учебного заведения. При желании можно заменить на свой, либо удалить, но имейте ввиду, что тогда придется править отступы между блоками.

## Main и контент

В шаблоне весь контент пишется в файле "content.tex".

В "main.tex" содержится точка входа (в LaTeX это строчка с \documentclass). Все настройки из файлов настроек подключаются, добавляется титульный лист, оглавление, переопределяются макросы и новые команды, добавляется контент и формируется список литературы.

Крайне **НЕ** рекомендуется как-то менять "main.tex"

## FAQ

### Как настроить сортировку для biblatex?

Зайдите в "packeges.tex" и удалите комментарий для нужного формата сортировки, остальное закомментируйте или удалите.

### Я хочу использовать Times New Roman

Зайдите в "format.tex" и удалите комментарий для помеченных строк.

**Для использования Times New Roman нужно использовать компилятор "LuaLaTex" или "XeLaTeX". При использовании "pdfLaTeX" ничего работать не будет.**
 
### Откуда брать правильные ссылки на статьи?

Заходите на google scholar, ищите статью для цитаты (удобнее всего использовать номер DOI, но гугл умеет хорошо искать и по другим параметрам), жмите на "цитировать", выбирайте biblatex и вставляйте код в файл "bibsource.bib". Сослаться на статью в тексте можно используя команду \cite{name}.

### Как вставлять код в текст?

Для того, чтобы вставить код в текст, добавляем его в папку code и пишем

```
\lstinputlisting[language=Python]{code/code.py}
```

Либо можно использовать вставку прямо в tex документ.

```
\begin{lstlisting}[label=some-code,caption=Some Code,language=C]
    *code*
\end{lstlisting}
```

### Как добавлять свои команды?

Для этого используйте \newcommand{\command}[param]{command}. Пример можете посмотреть в "macros.tex"
