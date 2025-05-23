Ещё в 1960-е годы у инженеров появилась идея: писать программы не для конкретного железа, а для абстрактного «исполнителя». Программы на Java как раз пишутся для такого исполнителя — виртуальной машины, или Java Virtual Machine (JVM). Java-разработчик не задумывается, на какой платформе будет запускаться его код. В то же время виртуальная машина не знает, что исполняет инструкции на Java, ведь она принимает и исполняет байт-код.

Кроссплатформенность в Java обеспечивается явным разделением уровней языка и реализации.

**Языковой уровень.** Разработчики пишут код на языке Java. После этого специальным инструментом, который называется javac, исходный код компилируется в байт-код Java. При этом происходит проверка синтаксиса, и в случае его нарушения разработчик получает сообщение об ошибке от javac.

Что здесь важно:

- На этом этапе нет ничего платформенно-специфичного, весь код на языке Java (как и байт-код Java) универсален.
- Байт-код Java — это язык, предназначенный не для людей, а для машин. Обычному разработчику его читать не нужно.

**Уровень реализации.** Полученный байт-код Java передаётся на вход виртуальной машины Java. Со всеми особенностями конкретной операционной системы или архитектуры процессора тоже разбирается JVM, без влияния на исходный код на языке Java.

Язык Java и сама JVM разрабатываются параллельно, при этом новые фичи языка зачастую требуют поддержки внутри JVM. С другой стороны, различные реализации JVM развиваются и сами по себе, например в них появляются новые, более эффективные алгоритмы сборки мусора или оптимизации кода.

**Java Development Kit** _(_[_JDK_](https://skillbox.ru/media/code/chto_takoe_java_obyasnyaem_dlya_novichkov/?utm_source=media&utm_medium=link&utm_campaign=all_all_media_links_links_articles_all_all_skillbox)_)_ — это комплект инструментов для разработки приложений на Java. В него входят несколько компонентов, которые позволяют разрабатывать и запускать приложения:

- **Javас.** Это компилятор, который преобразует исходники Java в class-файлы или формат jar.
- **JVM.** Виртуальная машина, которая исполняет байт-код.
- **Стандартная библиотека.** Набор модулей, классов, объектов и функций, которые доступны в языке.
- **Документация.** В ней содержится справочная информация об инструментах данной версии JDK.

Вы не можете явно освободить память из под объекта, когда он вам уже не нужен. Этим занимается специальный компонент JVM — Garbage Collector. Но вот как именно он работает, в спецификации не сказано.

[OpenJDK](https://openjdk.java.net/) — полностью открытой реализации JDK. Через какое-то время Sun была поглощена корпорацией Oracle, но при этом проект OpenJDK никуда не делся и до сих пор остаётся главной open-source-площадкой для разработки Java и JVM. OpenJDK — это эталонная реализация, на которую ориентируются разработчики других виртуальных машин.