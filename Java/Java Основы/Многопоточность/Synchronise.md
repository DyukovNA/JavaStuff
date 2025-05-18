В [многопоточности](https://www.geeksforgeeks.org/multithreading-in-java/) ****синхронизация**** имеет решающее значение для обеспечения безопасной работы нескольких потоков на общих ресурсах. Без ****синхронизации**** может возникнуть несогласованность или повреждение данных , когда несколько потоков одновременно пытаются получить доступ к общим переменным и изменить их. В Java это механизм, который гарантирует, что только один поток может получить доступ к ресурсу в любой момент времени. Этот процесс помогает предотвратить такие проблемы, как несогласованность данных и [состояния гонки](https://www.geeksforgeeks.org/race-condition-vulnerability/) , когда несколько потоков взаимодействуют с общими ресурсами.

Два потока, ****t1**** и ****t2**** , одновременно увеличивают общую переменную счетчика. Методы ****inc()**** и ****get()**** синхронизированы, что означает, что только один поток может выполнять эти методы одновременно, предотвращая условия гонки. Программа гарантирует, что конечное значение счетчика будет согласованным и правильно обновленным обоими потоками.

```java
class Counter {
    private int c = 0; // Shared variable

    // Synchronized method to increment counter
    public synchronized void inc() {
        c++;
    }

    // Synchronized method to get counter value
    public synchronized int get() {
        return c;
    }
}

public class Geeks {
    public static void main(String[] args) {
        Counter cnt = new Counter(); // Shared resource

        // Thread 1 to increment counter
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                cnt.inc();
            }
        });

        // Thread 2 to increment counter
        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                cnt.inc();
            }
        });

        // Start both threads
        t1.start();
        t2.start();

        // Wait for threads to finish
        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Print final counter value
        System.out.println("Counter: " + cnt.get());
    }
}
```

При создании синхронизированного блока кода после оператора `synchronized` идет объект-заглушка: `synchronized(this)`. Причем в качестве объекта может использоваться только объект какого-нибудь класса, но не примитивного типа.

Каждый объект в Java имеет ассоциированный с ним монитор. Монитор представляет своего рода инструмент для управления доступа к объекту. Когда выполнение кода доходит до оператора synchronized, монитор объекта res блокируется, и на время его блокировки монопольный доступ к блоку кода имеет только один поток, который и произвел блокировку. После окончания работы блока кода, монитор объекта res освобождается и становится доступным для других потоков.

После освобождения монитора его захватывает другой поток, а все остальные потоки продолжают ожидать его освобождения.

> `synchronized` methods enable a simple strategy for preventing thread interference and memory consistency errors: if an object is visible to more than one thread, all reads or writes to that object's variables are done through synchronized methods.

_In a very, very small nutshell:_ When you have two threads that are reading and writing to the same 'resource', say a variable named `foo`, you need to ensure that these threads access the variable in an atomic way. Without the `synchronized` keyword, your thread 1 may not see the change thread 2 made to `foo`, or worse, it may only be half changed. This would not be what you logically expect.

All the methods of `Hashtable` are `synchronized`, so only one thread can execute any of them at a time.

When using non-`synchronized` constructs like `HashMap`, you must build thread-safety features in your code to prevent consistency errors.

`Synchronized normal method` equivalent to `Synchronized statement` (use this)

```java
class A {
    public synchronized void methodA() {
        // all function code
    }

    equivalent to

    public void methodA() {
        synchronized(this) {
             // all function code
        }
    } 
}
```

`Synchronized static method` equivalent to `Synchronized statement` (use class)

```java
class A {
    public static synchronized void methodA() {
        // all function code
    }

    equivalent to

    public void methodA() {
        synchronized(A.class) {
             // all function code
        }
    } 
}
```

