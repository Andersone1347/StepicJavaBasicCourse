# StepicJavaBasicCourse

## 2  Базовый синтаксис Java

### 2.4 Управляющие конструкции: условные операторы и циклы

Для последней задачи.

**StringBuilder**
Вывести и добавить в StringBuilder.
```
StringBuilder builder = new StringBuilder("Привет");
builder.append(123);
String result = builder.toString();
System.out.println(result);
//Привет123
```
Удалить символ.
```
StringBuilder builder = new StringBuilder("Привет");
builder.deleteCharAt(2);
String result = builder.toString();
System.out.println(result);
//Првет
```
Заменить.
```
StringBuilder builder = new StringBuilder("Привет");
builder.replace(2, 5, "Hello!");
String result = builder.toString();
System.out.println(result);
//ПрHello!т
```
Развернуть строку.
```
String str = "Привет";
StringBuilder builder = new StringBuilder(str);
builder.reverse();
String result = builder.toString();
System.out.println(result);
//тевирП
```

[Больше информации](https://javarush.com/quests/lectures/questsyntaxpro.level09.lecture06)

**append**
Наглядный пример append в StringBuilder.
```
StringBuilder s = new StringBuilder(“I love Java ”);
int i = 14;
//the method appends StringBuilder and integer
s.append(i);
System.out.println(s);
// Мне нравится Java 14
```
[Больше информации](https://codegym.cc/groups/posts/append-method-in-java)
**startsWith()**
Похож на contains
```
import java.io.*;

public class Test {

   public static void main(String args[]){
      String Str = new String("Добро пожаловать на ProgLang.su");

      System.out.print("Возвращаемое значение: " );
      System.out.println(Str.startsWith("Добро пожаловать") );

      System.out.print("Возвращаемое значение: " );
      System.out.println(Str.startsWith("ProgLang") );

      System.out.print("Возвращаемое значение: " );
      System.out.println(Str.startsWith("ProgLang", 20) );
   }
}
Получим следующий результат:

Возвращаемое значение: true
Возвращаемое значение: false
Возвращаемое значение: true
```
[Больше информации](https://proglang.su/java/strings-startswith)

**replaceFirst()**
Заменяет сточку
```
Пример
import java.io.*;

public class Test{
   public static void main(String args[]){
      String Str1 = new String("Добро пожаловать на ProgLang.su");

      System.out.print("Возвращаемое значение: ");
      System.out.println(Str1.replaceFirst("(.*)ProgLang(.*)",
                         "IAMGROOT" ));

      System.out.print("Возвращаемое значение: ");
      System.out.println(Str1.replaceFirst("ProgLang.su", "IAMGROOT"));
      
      String Str2 = new String("Добро пожаловать на ProgLang.su! Добро пожаловать на ProgLang.su!");
      
      System.out.print("Возвращаемое значение: " );
      System.out.println(Str2.replaceFirst("Добро пожаловать на ProgLang.su!", "IAMGROOT!"));
   }
}
Получим следующий результат:

Возвращаемое значение: IAMGROOT
Возвращаемое значение: Добро пожаловать на IAMGROOT
Возвращаемое значение: IAMGROOT! Добро пожаловать на ProgLang.su!
```
[Больше информации](https://proglang.su/java/strings-replacefirst)

## 3  Объекты, классы и пакеты в Java
### 3.3 Объявление класса
![alt](/img/%D1%82%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%B0%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F.jpg)