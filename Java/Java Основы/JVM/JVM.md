![[Pasted image 20250121205730.png]]

## Что такое виртуальная машина Java (JVM)

Виртуальная машина Java («Java Virtual Machine» — JVM) — это основная часть платформы Java Runtime Environment (JRE), которая интерпретирует байт-код Java для запуска программ.

Как правило, считается, что JVM имеет двойное определение — техническое и неформальное.

_Техническое:_ JVM — это спецификация программы, которая обеспечивает среду выполнения кода Java.

_Неофициальное:_ JVM запускает приложения Java, c помощью настроенных параметров для управления всеми программными ресурсами.

## Что делает виртуальная машина Java

JVM выполняет две основные функции:

- позволяет запускать Java-программы на любом устройстве или в любой операционной системе;
- даёт доступ к управлению памятью программ и её оптимизации.

## Файл .class и байт-код

Когда дело доходит до выполнения программы, главное, что интересует виртуальную машину Java — это определённый формат файла – .class.

Файлы классов содержат наполовину скомпилированный код, называемый байт-кодом, который в свою очередь предоставляет JVM инструкции, таблицу символов и другую вспомогательную информацию.

## Архитектура виртуальной машины Java

Java Virtual Machine состоит из трёх отдельных компонентов:

- загрузчик классов;
- область памяти;
- исполнительный механизм.

![[Pasted image 20250121212340.png]]
1. **Загрузчик классов**

Загрузчики классов отвечают за динамическую загрузку файлов .class в виртуальную машину Java и сохранения байт-кода в области метода JVM, о которой мы поговорим чуть позже.

Загрузчик классов Java бывает трёх типов:

- **BootStrap ClassLoader** (Загрузчик классов начальной загрузки) — это машинный код, который запускает операцию, когда её вызывает JVM. Его задача — загрузить классы из папки rt.jar.
- **Extension ClassLoader** (Загрузчик классов расширений) является дочерним элементом Bootstrap ClassLoader и загружает расширения основных классов Java из каталога jre/lib/ext или любого другого каталога, на который указывает java.ext.dirs.
- **System ClassLoader** (Системный загрузчик классов) загружает классы, найденные в переменной среды CLASSPATH, -classpath или параметре командной строки -cp.

2. **Область памяти**

![[Pasted image 20250121222705.png]]

Область памяти или, как её ещё называют, _область данных времени выполнения_ JVM состоит из 5 частей:

- **Область метода** предназначена для хранения данных файлов .class: например, метаданные, данные полей и методов, а также код метода. Область метода создаётся автоматически при запуске виртуальной машины, и для каждой ВМ существует только одна область метода.
- **Область кучи**. В куче хранятся все объекты и соответствующие им переменные экземпляра. Когда мы создаём новый экземпляр класса, он сразу же загружается в область кучи, которая остается единственной во время выполнения задачи.
- **Область стека**. В неё загружаются все локальные переменные, вызовы методов и частичные результаты.
- **Регистры ПК**. В регистре ПК хранится адреса виртуальных машин Java, выполняющих операцию в данный момент. В Java каждый поток получает свой собственный регистр ПК.
- **Стеки нативных методов**. Нативные методы — это методы, написанные на C или C++. Виртуальная машина JVM хранит стеки, которые поддерживают такие методы, с отдельным стеком собственных методов, выделенным для каждого потока.

3. **Исполнительный механизм**

Этот тип программного обеспечения используется для тестирования оборудования и программного обеспечения. При этом он не сохраняет никакой информации о тестируемом продукте.

Он стоит из:

- интерпретатора;
- JIT-компилятора;
- сборщика мусора.

Перед выполнением программы интерпретатор и компилятор JIT («Just-in-time» — «точно в нужное время») преобразуют байт-код в машинные инструкции. Интерпретатор делает это построчно.

В тот момент, когда в сценарии обнаруживается повторяющийся код, к нему подключается JIT-компилятор для ускорения операции. Затем он компилирует байт-код и заменяет его собственным кодом. Такой процесс повышает производительность всей системы.

Но за что же в таком случае отвечает сборщик мусора? В некоторых других языках программирования (таких как C++) освобождение памяти от объектов без циклических ссылок зависит лишь от самого программиста. Однако в JVM этим занимается сборщик мусора, что оптимизирует использование памяти.

Важно отметить, что сборка мусора выполняется в JVM автоматически через определённые отрезки времени и не требует отдельного внимания специалистов. Конечно, этот процесс можно попробовать принудительно запустить, вызвав System.gc(), но нет никакой гарантии, что это сработает.