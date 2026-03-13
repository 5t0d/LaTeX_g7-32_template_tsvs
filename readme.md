# Оригинальный шаблон
Копия русскоязычного шаблона для рефератов по ГОСТ 7.32-2017 "Отчет о научно-исследовательской работе". Оригинал не был найден на github, только в Overleaf ([оригинальный шаблон ИТМО](https://ru.overleaf.com/latex/templates/essay-template-itmo-rus/qfhzpzxstvvw) ).

> Шаблон составлен для компилятора XeLaTeX, некоторые возможности которого (в частности, нативная поддержка Unicode) отсутствуют на более старом компиляторе pdfLaTeX. Поэтому, если вы компилируете при помощи pdfLaTeX, и у вас ничего не работает - не удивляйтесь. Все или почти все современные дистрибутивы LaTeX уже содержат внутри себя XeLaTeX, просто выберите его в настройках.

> Библиография собирается при помощи движка biber. Если компилятор выдает ошибку, либо же ссылки и/или список литературы выглядят не так, как должны - проверьте в настройках, нужный ли движок у вас подключен. В Overleaf специально выбирать ничего не надо, все работает по умолчанию. В некоторых сборках движок для библиографии надо выбирать вручную в настройках (например, в TeXstudio по умолчанию стоит bibTeX).

# Использование LaTeX в редакторе VSCode

<img src="https://github.com/user-attachments/assets/a0d59ae8-b444-4cd4-a48f-9215845b5b93" width="800" />

Для такого результата необходимо установить:


1. `VSCode`. Потребуется `x64` версия;
2. Необходимые пакеты (`TexLive`);
3. Поддержка XeLaTeX в VSCode;
4. Расширения для VSCode: LaTeX Workshop, LaTeX Utilities.

## Установка (Ubuntu 24)
### 1. VSCode
[VSCode](https://code.visualstudio.com/). Ничего сверхъестественного, скачиваем, устанавливаем. 

### 2. Установка зависимостей
```bash
sudo apt install texlive-science texlive-latex-extra texlive-extra-utils latexmk texlive-publishers texlive-science texlive-bibtex-extra texlive-full
```

### 5. VSCode Extensions: LaTeX Workshop, LaTeX Utilities

Устанавливаем расширения VSCode:

<img src="https://github.com/user-attachments/assets/ca51d44b-c6ec-4cf2-af4d-df32cfb64a2f" width="400" />


### 6. Поддержка xelatex
В проектах [Overleaf](https://ru.overleaf.com/project) используется верстка `xelatex`, добавим поддержку в VSCode: `CTRL`+`Shift`+`P`, далее ищем `Preferences: Open User Settings (JSON)` в открывшемся файле добавляем строки:
```sh
"latex-workshop.latex.tools": [{
        "name": "latexmk",
        "command": "latexmk",
        "args": [
            "-xelatex",
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
        ]
    }],
```

## Компиляция, получение PDF
1. После установки и настройки VSCode скачиваем репозиторий (можно просто `ZIP-архив`):
```sh
git clone https://github.com/sibsutisTelecomDep/essay_g7-32_template_tsvs_dep.git
```
2. Открываем папку в VSCode.
3. Компиляция (обратите внимание на `или`, компилируем только по одному из пунктов):
    1. Редактируем файл `0_main.tex` и сохраняем (компиляция начнется автоматически) **или**
    2. Выполняем команду в терминале: `xelatex -halt-on-error  -enable-installer ./0_main.tex` **или** 
    3. Переходим в расширение TeX, выполняем команду `Build`, получаем в корневой папке `.pdf-файл` 

<img src="https://github.com/user-attachments/assets/4ac12dd7-0da0-4f4b-8ea4-01b1b3b7bac8" width="700" /> 
