# exDOTsmartDesign
exDOT SmartDesign - инструмент типа «Таблица -> Схема» для формализации бизнес-процессов. exDOT SmartDesign (excel - DOT) демонстрирует как можно использовать технологию SmartDesign непосредственно в Excel. Строит схему процесса по табличному описанию через промежуточное преобразование в DOT (graphviz). Фактически это рестайлинг ARIS SmartDesign (похожий инструмент см. jsDOT SmartDesign).
Схемы процессов строятся в процессных нотациях EPC и VAD. В простейшем случае – достаточно нажать кнопку «Схема» и отобразиться тестовый простой пример, далее можно редактировать таблицу связей и получать новую схему, соответствующую описанию процесса в табличном виде.
Статьи: 
# Инструменты
- MS Excel
- graphviz https://graphviz.org/ (требуется локальная установка)
Для работы exDOT SmartDesign в offline должен быть установлен graphviz и добавлен в path (или путь к graphviz явно указать на листе «set» Excel). 
# Сценарии использования
а) Открыть файл exDOT SmartDesign.xlsm и нажать кнопку «Схема» (лист «Процесс»). По умолчанию загружается Пример Простой и отображается его схема. Можно выбрать через выпадающий список тип нотации (три вариации ЕРС и VAD) в верхнем левом углу таблицы.
б) Открыть файл exDOT SmartDesign.xlsm, выбрать Пример Сложн. (сложный) и нажать кнопку «Схема». 
в) Открыть файл exDOT SmartDesign.xlsm и ввести в таблицу собственное описание алгоритма процесса. Для очистки прежнего содержания таблицы можно использовать кнопку «Clear». Можно использовать Режим Простой и Режим Сложный (выпадающий список). В последнем случае добавится поле «Предшествующий», которое нужно заполнить цифрой (набором цифр, через запятую), которая обозначает номер строки с предшествующим workflow – элементом (событие \ функция), см. Пример Сложн.
Для задания ветвления согласно примеру Пример Сложн. необходимо указать двух предшественников «es wAre alles» (через запятую №: 6,9).  
Таблица связей ограничена двадцатью строками. Для увеличения строк для формирования алгоритма достаточно для нужного количества строк выполнить «Формат по образцу» (за образец взять любую строку из первых 20). 
# Описание листов книги (файла) 
На листе «Процесс» (таблица связей) формализуем процесс в табличном виде, например, в ЕРС – используя элементы: событие, функция (операция), входящий документ, исходящий документ, роль (исполнитель операции), ИТ-система (инструмент, используемый в операции). Можно посмотреть демо ролики про ARIS SmartDesign. 
На листе «Справочник» редактируем справочники объектов: типы документов (используются в полях Входящий документ и Исходящий документ таблицы связей), типы ролей (набор исполнителей операций), типы систем (набор инструментов для выполнения операций).
Редактирование по правилам «умных таблиц» Excel (см. нижний синий контур и уголок). Т.е. для добавления значения нужно «потянуть» за уголок и расширить диапазон «умной таблицы» и только потом ввести новое значение. 
Лист «Set» задает пути: файл dot.exe и хранение dot (file.txt) и графического файла со схемой graph1.png, по умолчанию C:\Temp\.
Для формирования начального блока (digraph G { ...) и концевика скрипта DOT используется лист StEnd.
На листе DOTstyle представлены «синтаксические обертки» в EPC \ VAD для каждого объекта процесса: события, операции, роли, системы, документа. Например, обертка (фигурка) в DOT для объекта «операция» для ЕРС выглядит (фигурка - зеленый скругленный прямоугольник):
[shape="box",width=1.5,style="rounded,filled",fillcolor="green",label="
синтаксическая обертка для объекта «операция» для VAD выглядит (зеленоватый кораблик):
[shape="cds",width=1.5,style="filled",fillcolor="lightgreen",label="
exDOT SmartDesign задумывался как «плацдарм» для Semantic SmartDesign, см. https://habr.com/ru/articles/795883/ 

