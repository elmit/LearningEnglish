LearningEnglish
===============
Работает приложение очень просто - вы создаете словарь, оно "прогоняет" вас по этому словарю, поправляя при необходимости. При каждом запуске нужно ответить правильно определенное кол-во раз, после чего программа завершиться. Если вы ответили неверно, то слово будет повторяться снова и снова до тех пор, пока не будет введн верный ответ, причем повторные ответы правильные или нет - на статистику не влияют.
Для контроля процесса изучения в правом верхнем углу есть кнопка показывающая текущий прогресс.

## Настройки
Настроить путь к словарю, к файлу для сохранения статистики, периодичность повторения уроков, кол-во правильных ответов, которое будет требовать программа - можно в файле config.json. Так же там можно настроить кол-во изучаемых одновременно слов и параметры, по которым можно считать слово изученным. Пути к словарю или файлу со статистикой, нужно указывать либо полный, либо относительно файла main.py.

## Словарь
В словаре допускается указывать несколько вариантов перевода через запятую, программа засчитает любой из этих ответов за правильный. Так же не играет роли регистр введенного слова и пробелы в конце или в начале. Если вы по ошибке добавите в словарь несколько одинаковых английских слов, при загрузке переводы дубликатов будут объединены.

Некоторые разные английские слова переводятся на русский одинаково н-р: team и command переводятся как команда, поэтому когда попадается упражнение по переводу слова "команда" на английский, не понятно что вводить в ответ. На этот случай, в словаре можно использовать уточнения в круглых скобках:
["team", "ti:m", "команда(группа)"],
["command", "kə'mɑ:nd", "команда(приказ)"]
тогда скрипт будет явно просить перевести слово "команда(группа)" или "команда(приказ)", при переводе в обратную сторону слов team или command уточнение писать не нужно, требуется ответить только "команда".

При переводе на русский, зачастую окончание слова (или другая часть) не важна например angry можно перевести как сердитый, сердит, сердита и т.п. Что бы избежать путаницы, в переводе можно поменить необязательную часть слова квадратными скобками н-р:
["angry", "'æŋgri", "сердит[ый]"]
Теперь при везде в интерфейсе перевод будет отображаться как "сердитый", но в качестве ответа на слово "angry", допускается вводить сердитый, сердит, сердита и т.п., главное что бы оно начиналось с "сердит". Скобок может быть сколько угодно, в любой части слова

Пример словаря находится в файле - dict.json.

## Выбор слов для изучения
Случайным образом из словаря выбирается 50 (настраивается) неизученных слов + все изученные. Каждому из слов проставляется рейтинг, зависящий от того, насколько давно это слово повторялось, какой процент правильных ответов по этому слову, правильно ли вы в последний раз его перевели, в итоге чем хуже вы слово знаете тем выше у него проставляется рейтинг. Из полученного списка слов случайным образом выбираются слова для урока, причем, чем выше рейтинг, тем больше вероятность, что именно оно будет вам предложено для перевода.

## Установка
Скрипт написан на python 2.6, поэтому требуется его установить, вполне вероятно что он будет работать и на других версиях python 2.x.
Запустить скрипт можно вот такой командой: «%path_to_Python26%\pythonw.exe %path_to_main.py%\main.py».
Если скрипт используется одновременно на разных компьютерах, то его можно переместить в папку dropbox'а или аналогичного сервиса (в принципе достаточно выложить туда только словарь и файл со статистикой настроив соответственно пути в конфиге). Скрипт достаточно интеллектуален, что бы не затирать результаты уроков записанных другой копией.