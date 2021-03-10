# UNIFLOC VBA #

Анализ работы скважины и скважинного оборудования 
с использованием VBA макросов Excel.

### Описание ###

* Инженерные расчеты по добыче Унифлок VBA

* Версия 7.26

Расчетные модули разработаны для обучения студентов и специалистов методам проведения инженерных расчетов добывающих скважин. Рекомендуется применение для учебных целей. Авторы стараются избегать ошибок в расчетных модулях, но не гарантируют их отсутствия. 


Возможности на текущий момент
- Расчет физико-химических свойств пластовых флюидов по двум наборам корреляций
- Расчет многофазного потока в трубах и скважине по нескольких корреляциям (Беггс Брилл, Ансари, Унифицированная TUFFP и некоторые другие)
- Расчет многофазного потока в штуцере. Корреляция Перкинса.
- Расчет характеристик УЭЦН и база характеристик УЭЦН для некоторых типов насосов
- Расчет распределения давления в фонтанирующей скважине
- Расчет распределения давления в скважине с УЭЦН
- Расчет распределения давления в скважине с газлифтом

Изменения в версии 7.26
- промежуточная версия с большими изменениями в аргументах функций и способах вывода результата
  часть функциональности временно вырезана, если необходима используйте версию 7.25
- широко используются json строки для задания параметров и вывода результатов. В перспективе должно 
  повысить удобство использования и удобства переноса на другие платформы
- изменена модель задания потока флюидов - появился термин feed (это влечет за собой значительную перестройку всех зависимых функций)


Изменения в версии 7.25 (используйте эту версию если нужна стабильная функциональность на текущий момент)
- изменился формат базы ЭЦН
- добавлено активное использование json строк при работе с пользовательскими функциями для ввода и вывода
- улучшена модель ПЭД и модель УЭЦН с учетом ПЭД и газосепаратора
- разные мелкие изменения для повышения удобства работы 
- поправлены баги с расчетом горизонтальной скважины, выводом сжимаемости нефти и расчетом вязкости смеси

Изменения в версии 7.24
- добавлены функции для расчета гидратов (от Горидько К)
- исправления в пользовательских функциях расчета ЭЦН. Теперь выводится больше информации о расчете. Работает калибровка по одному параметру. Поправлена модель задания поправки на газ.

Изменения в версии 7.23
- проверена и восстановлена работа python API

Изменения в версии 7.22
- Исправление ошибок и рефакторинг кода PVT и расчета корреляций
- Приведение в порядок упражнений 

Изменения в версии 7.21
- Появилась мелкое обновление с номером версии 7.21.1. Исправлена ошибка в функции MF_p_pipe_atma - теперь она правильно понимает отрицательные углы.
- В попытке исправить баги и сделать лучше изменены аргументы функций расчета трубы. Подробности будут в сообщениях на unifloc.ru
- Добавлен ряд пользовательских PVT функций. В частности для расчета теплоемкостей и сжимаемостей флюидов.
- Добавлен пример расчета z фактора 
- Обновлены примеры расчета трубы 
- Обновлен мануал в части описания идеологии расчета трубы и трубопровода по новому

Изменения в версии 7.20
- исправлена ошибка при загрузке базы ЭЦН. При скачивании с гитхаба в базе насосов заменялся символ переноса каретки, из за чего считывание проходило некорректно. Исправлено и немного оптимизировано
- добавлены варианты расчета калибровок для модели трубы - подстройка по дебиту жидкости и свободного газа
- добавлены варианты расчета калибровок для модели штуцера аналогично трубе 

Изменения в версии 7.19
- сделан скрип автоматизированной проверки заданий/упражнений для дистанционных курсов. Если скачать сразу много заданий можно проверить их корректность по ключевым файлам.
- подготовлен ряд заданий для проверки с использованием скрипта
- исправлены мелких ошибки (инициализация перемернных, отладка сообщений в логе)

Изменения в версии 7.18
- исправлен и доработан расчет ЭЦН. обновлен пример расчета ЭЦН
- новый вариант работы с базой ЭЦН - база читается из текстового файла

Изменения в версии 7.17
- изменения в наборе примеров и упражнений
- исправлены некоторые мелкие ошибки

Изменения в версии 7.16
- Продолжение доработки документации - добавлены некоторые картинки по трубопроводам, одновлена диаграмма классов
- Вызов расчета трубы и трубопровода унифицирован - и там и там вывод одинаковый
- Исправлены мелкие ошибки при расчете PVT - при некоторых условиях неправильно инициалировались газовый фактор и газосодержание
- Проведен рефакторинг класса CESPpump - убран лишний код (строк меньше стало в два раза). Изменена схема расчета характеристики ЭЦН. Теперь она всегда интерполируется по заданным в базе точкам. При этом в коде больше не используются функции Application (должно позволить проще портировать код). 
- Для ЭЦН добавлена фича, что при дебите больше максимального напор не обнуляется, а становится отрицательным. Для контроля введены два контрольных параметра turb_head_factor, turb_rate_factor
- База насосов вынесена из надстройки в отдельный файл ESP_db.xlsx - для корректной работы файл должен быть рядом с надстройкой
- Исправлен расчет скважины по кнопке в рабочей книге в папке apps 
- Вроде все примеры работают но версия промежуточная - будут еще доработки в ближайшее время.


Изменения в версии 7.15
- Документация актуализирована с текущим состоянием кода 
- Исправлена ошибка при расчете функций скважины 
- Мелкие исправления ошибок и неточностей в наименовании аргументов. Должно стать немного логичнее и понятнее

Изменения в версии 7.14
- Доработка документации - описание разделено на несколько документов
- Исправление ошибок

Изменения в версии 7.13
- Доработка и исправлении версии 7.12 
- Изменения для повышения удобства использования расчетных функций при написании макросов (не из интерфейса Excel)

Изменения в версии 7.12
- Изменены интерфейсы для пользовательских функций расчета скважины с префиксом well_
- Добавлен расчет трубопровода - отличается от трубы возможностью задания траектории и изменения диаметров по длине
- Возможность учета инклинометрии в скважине 
- Расчет трубопровода и скважины возвращает в Excel расширенный набор информации о расчете
- Добавлены упражнения для новых функций
- версия 7.12 промежуточная - после больших обновлении в расчете трубы и скважины возможны баги. Следующие версии будут направлены на стабилизацию кода.

Изменения в версии 7.11
- Добавлен автоматически генерируемый программный интерфейс API для доступа к пользовательским функциям unifloc VBA через python
- Добавлены функции расчета неустановившегося режима работы скважины после запуска с постоянным дебитом
- Описание разделено на две части - руководство пользователя и сборник упражнений

Изменения в версии 7.10
- При запуске надстройки создается закладка с кнопками на панели управления Excel. Там есть кнопки для проверки версии и исправления ссылок на надстройку при переносе ее между компами.
- Мелкие исправления в названиях функций

Изменения в версии 7.9
- Добавлены функции для расчета газлифтных клапанов
- Добавлен режим расчета распределения давления газа в трубе (без трения)
- Добавлены функции расчета параметров газлифтной скважины (расчет снизу вверх и сверху вниз)

Изменения в версии 7.8.
- Добавлены функции для работы с кривыми в интерфейсе Excel (префикс "crv_")

Изменения в версии 7.7.
- Упорядочены упражнения по использованию расчетных функций
- Изменены названия ряда пользовательских функций для удобства использования
- Функции для расчета скважин (фонтан, ЭЦН, газлифт)
- Расчет асинхронного двигателя ПЭД
- Оценка коэффициента сепарации газосепаратора 
- Исправление мелких ошибок
- Доработано описание - добавлен раздел с автоматически генерируемыми описаниями функций. Компиляция документации в LuaTex

Изменения в версии 7.6
- Добавлен учет плотности газа в затрубном пространстве при расчете скважины с УЭЦН
- Обновлена схема работы со скважинами и расчета узлового анализа. Введен интерфейсный класс IWell скважины обеспечивающий одинаковое поведение всех типов скважин и типовые расчеты узлового анализа
- Сделан единий механизм работы с расчетными кривыми для всех базовых классов. Механизм реализуется классом CCurves
- Переработаны методы инициализации скважин для устранения неоднозначностей. Отдельно задается конструкция, отдельно задается распределение температуры и метод расчета температуры скважины
- В связи с переработками поменялись названия ряда методов классов скважины, поэтому изменен номер версии.

на текущий момент версия 7.6 еще в доработке. 

Изменения в версии 7.5
- Обновлен класс CWell обеспечивающий расчет по скважине с УЭЦН. 
- Добавлен класс описывающий упрощенную систему УЭЦН CESPSystemSimple. Класс обеспечивает расчет сепарации и электрических параметров по работе УЭЦН. Встраивается в CWell и обеспечивает учет работы УЭЦН в скважине. Текущие ограничения - один тип насоса (нет конусной сборки, единая кабельная линия, сопротивление кабеля не меняется по глубине с температурой, двигатель с постоянным КПД и постоянными параметрами электрическими)
- Вернулся расчет барботажа (потока газа в неподвижной жидкости) в блок многофазных расчетов и блок скважины. Сейчас барботаж считается по корреляции Ансари при очень маленьком дебите жидкости
- Добавлены интерфейсные функции Excel для расчета скважины.
- Изменена схема именования надстройки - теперь содержит только главный номер версии. Для того чтобы проще было обновлять расчетные модули на компе в ходе разработки. 


Изменения в версии 7.3
- Дополнена модель ПЭД
- Ускорены расчеты по скважине
- Изменился вызов некоторых функций Excel 
- Систематизирован расчет скважины 


### Контакты ###

* Хабибуллин Ринат
* khabibullin.ra@gubkin.ru

