# StepicJavaBasicCourse

## 2  Базовый синтаксис Java

### 2.1 Примитивные типы

#### Задача
Реализуйте метод, возвращающий true, если среди четырех его аргументов ровно два истинны (любые). Во всех остальных случаях метод должен возвращать false.

Воспользуйтесь шаблоном кода, который предлагает система. Ввод-вывод будет сделан за вас. Вам надо только проанализировать переданные в метод booleanExpression значения (a, b, c, d) и вернуть результат. Попробуйте составить формулу с использованием булевых операторов. Если не получается, вернитесь к этому заданию после просмотра степов про условные операторы и циклы.

При записи сложных выражений рекомендуется использовать скобки, чтобы не запутаться в порядке применения операторов.

В качестве примера уже указано заведомо некорректное решение задачи. Исправьте его.

Совет тем, у кого не проходит какой-то из тестов. В данной задаче возможно всего 16 комбинаций значений входных параметров. Их можно выписать на бумажку, посчитать для них правильные ответы и сравнить с тем, что выдает ваше решение. Попробуйте самостоятельно проделать это, найти ошибку и исправить решение.
Sample Input 1:

false false false false
Sample Output 1:

false
Sample Input 2:

true true true true
Sample Output 2:

false
Sample Input 3:

false false true true
Sample Output 3:

true
#### Решение
Сравниваем все возможные варианты.
```
public static boolean booleanExpression(boolean a, boolean b, boolean c, boolean d) {
    return (a & b & !c & !d) | (a & !b & c & !d) | (a & !b & !c & d) | (!a & b & c & !d) | (!a & b & !c & d) | (!a & !b & c & d);
}
```
Альтернативные решения:
```
public static boolean booleanExpression(boolean a, boolean b, boolean c, boolean d) {
    return ((a != b) && (c != d)) || ((a != c) && (b != d));
}
```
#### Задача
В Григорианском календаре год является високосным в двух случаях: либо он кратен 4, но при этом не кратен 100, либо кратен 400.

Реализуйте метод, вычисляющий количество високосных лет с начала нашей эры (первого года) до заданного года включительно. На самом деле Григорианский календарь был введен значительно позже, но здесь для упрощения мы распространяем его действие на всю нашу эру.

Ввод-вывод обеспечивает проверяющая система. Вам надо только проанализировать переданное в метод значение и вернуть результат. В программу всегда подается положительный номер года. Предполагается решение без циклов. Вам надо придумать и записать несложную формулу, использующую только арифметические операторы.

В качестве примера написано заведомо неправильное выражение. Исправьте его.
Sample Input 1:

1
Sample Output 1:

0
Sample Input 2:

4
Sample Output 2:

1
Sample Input 3:

100
Sample Output 3:

24
#### Решение
по формуле
```
   public static int leapYearCount(int year) {
         return ((year / 4) - (year / 100) + (year / 400));
     }
 
```
Альтернативные решения:
```
import java.util.Scanner;

public class Stepik_218 {
    public static void main(String[] args){
        System.out.println("Сколько високостных лет от 0 до указанного года?");
        System.out.println("------------------------------------------------");
        Scanner in = new Scanner(System.in);
        int year;
        while(true){
            System.out.print("Year? [0 - exit]: ");
            year = in.nextInt();
            if (year > 0) {
                System.out.printf("Reply: %d.\n", leapYearCount(year));
            } else {
                break;
            }
        }
    }
    public static int leapYearCount(int year) {
        return year / 4 - year / 100 + year / 400;
    }
}
```
#### Задача
Реализуйте метод, возвращающий ответ на вопрос: правда ли, что a + b = c?
Допустимая погрешность – 0.0001 (1E-4)

Можно использовать класс Math и его методы. Класс Math доступен всегда, импортировать его не надо.

В качестве примера написано заведомо неправильное выражение. Исправьте его.
Sample Input:

0.1 0.2 0.3
Sample Output:

true
#### Решение
по формуле
```
public static boolean doubleExpression(double a, double b, double c) {
    return Math.abs((a+b)-c)<1e-4;
}
```
Альтернативные решения:
```
 public static boolean doubleExpression(double a, double b, double c) {
        return Math.abs((a + b) - c) < 0.0001;
    }
```
#### Задача
Какой тип имеет литерал 0x0bp3?

Введите имя соответствующего примитивного типа. Напоминаем, что Java чувствительна к регистру символов.
#### Решение
double
```
class MyProgram {
    public static void main(String[] args) {

        Object o = 0x0bp3;
        System.out.println(o.getClass());
    }
}
//class java.lang.Double
```
#### Задача
Укажите размер целочисленного типа int в Java.

Известно только, что sizeof(short) <= sizeof(int) <= sizeof(long). Конкретный размер зависит от платформы.

32 бита

16 бит

Размер динамически изменяется, чтобы вместить любое нужное пользователю целое число.
#### Решение
![alt](/img/int.jpg)
```
32
```
#### Задача
Реализуйте метод flipBit, изменяющий значение одного бита заданного целого числа на противоположное. Данная задача актуальна, например, при работе с битовыми полями.

Договоримся, что биты нумеруются от младшего (индекс 1) к старшему (индекс 32).

Воспользуйтесь предоставленным шаблоном. Декларацию класса, метод main и обработку ввода-вывода добавит проверяющая система.

Sample Input:

0 1
Sample Output:
1
#### Решение
[Инверсия бита в числе](https://www.youtube.com/watch?v=YGFQOUYJbUs) 
Алгоритм:
1. Берем число 1, оно у нас в двоичной СС представляется как 00000001.
2. Затем побитово сдвигаем его на bitIndex-1. Почему -1? Потому что "умные" составители задачи написали нам условие "Договоримся, что биты нумеруются от младшего (индекс 1) к старшему (индекс 32)." Т.е. получается 1<<(bitIndex-1)
3. Выполняем операцию "логическое исключающее или" c value и побитово сдвинутой единицей (см шаг 2): value^(1<<(bitIndex-1)). Собственно это и запихиваем в return.

Пример:
Дано число 13. Изменить 2й бит на противоположный.
Число 13 в 2й СС = 1101. 2й бит у нас 0, т.е. его меняем на 1 и получаем результат 1111 (2я СС) = 15 (10я СС).
Что происходит в программе:
1 << 2-1, получается 0001 превратилось в 0010
Выполяняем 3й шаг: 1101 ^ 0010 = 1111 (2я СС) = 15 (10я СС).

В принципе задача не сложная просто надо еще раз пересмотреть/перечитать что такое побитовый сдвиг и операция ^.

Итоговый код:
```
public static int flipBit(int value, int bitIndex) {
    return value^(1<<(bitIndex-1));
}
```
Альтернативные решения:
```
/**
 * Flips one bit of the given <code>value</code>.
 *
 * @param value     any number
 * @param bitIndex  index of the bit to flip, 1 <= bitIndex <= 32
 * @return new value with one bit flipped
 */
public static int flipBit(int value, int bitIndex) {
    return value^((int) Math.pow(2, (bitIndex-1))); // put your implementation here
}
```
##### 2.2 Преобразование типов
#### Задача
Реализуйте метод, который возвращает букву, стоящую в таблице UNICODE после символа "\" (обратный слэш) на расстоянии a.

В качестве примера написано заведомо неправильное выражение. Исправьте его.

Sample Input 1:

32
Sample Output 1:

|
Sample Input 2:

29
Sample Output 2:

y
#### Решение
```
   public static char charExpression(int a) {
        return (char) ('\\' + a);
    }

```
Альтернативные решения:
[таблица символов Юникода](https://en.wikipedia.org/wiki/List_of_Unicode_characters) 92 это \\.
```
class MyProgram {
    public static void main(String[] args) {
        int a = 92;
        System.out.println((char)a);
    }
}
```

#### Задача
Укажите преобразования типов, которые компилятор делает автоматически. Другими словами, для каких преобразований не требуется явно писать в программе оператор приведения типа?

long -> float

int -> long

String -> int

byte -> char

char -> int

int -> boolean

float -> long

char -> Character
#### Решение
![alt](/img/izm.png)
```
long to float

char to int

char to Character

int to long
```

#### Задача
Реализуйте метод, проверяющий, является ли заданное число по абсолютной величине степенью двойки.

Решать можно разными способами:

воспользовавшись одним удобным статическим методом из класса java.lang.Integer;
применив пару трюков из двоичной арифметики;
написав решение "в лоб" с циклом и условными операторами (можете вернуться к этой задаче после просмотра соответствующих уроков).
Воспользуйтесь предоставленным шаблоном. Декларацию класса, метод main и обработку ввода-вывода добавит проверяющая система.

Sample Input 1:

0
Sample Output 1:

false
Sample Input 2:

1
Sample Output 2:

true
Sample Input 3:

-2
Sample Output 3:

true
#### Решение
```
public static boolean isPowerOfTwo(int value) {
    return Integer.bitCount(Math.abs(value)) == 1; // you implementation here
}
```
Альтернативные решения:
Для понимания в ide (https://www.youtube.com/watch?v=zXQuqY3WQtM).
```
import java.util.Scanner;

class MyProgram {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int x = Math.abs(sc.nextInt());
        boolean a = true;
        if (Integer.bitCount(x)==1){
            System.out.println(a);
        } else {
            a = false;
            System.out.println(a);
        }
    }
}
```
---
### 2.3 Массивы и строки
#### Задача
Реализуйте метод, проверяющий, является ли заданная строка палиндромом. Палиндромом называется строка, которая читается одинаково слева направо и справа налево (в том числе пустая). При определении "палиндромности" строки должны учитываться только буквы и цифры. А пробелы, знаки препинания, а также регистр символов должны игнорироваться. Гарантируется, что в метод попадают только строки, состоящие из символов ASCII (цифры, латинские буквы, знаки препинания). Т.е. русских, китайских и прочих экзотических символов в строке не будет.

Воспользуйтесь предоставленным шаблоном. Декларацию класса, метод main и обработку ввода-вывода добавит проверяющая система.

Подсказки (не читайте, если хотите решить сами):

для удаления из строки всех символов, не являющихся буквами и цифрами, можно воспользоваться регулярным выражением "[^a-zA-Z0-9]"; найдите в классе String метод, выполняющий замену по регулярному выражению;
для перестановки символов строки в обратном порядке можно воспользоваться методом reverse(), который находится в классе StringBuilder;
в классе String есть методы для преобразования всей строки в верхний и нижний регистр.
Sample Input:

Madam, I'm Adam!
Sample Output:

true
#### Решение
```
   public static boolean isPalindrome(String text) {
        String text1 =text.replaceAll("[^a-zA-Z0-9]","").toLowerCase();
        String text2 = new StringBuilder(text1).reverse().toString();
        return text1.equals(text2); 
    }
```
Альтернативные решения:
в ide
```
class Hello{
    public static void main(String[] args) {
        String text = "Madam, I'm Adam!";
        String text1 =text.replaceAll("[^a-zA-Z0-9]","").toLowerCase();
        String text2 = new StringBuilder(text1).reverse().toString();
        boolean a = text1.equals(text2);

        System.out.println(a);

    }
}
```
---
### 2.4 Управляющие конструкции: условные операторы и циклы
#### Задача
Реализуйте метод, вычисляющий факториал заданного натурального числа.

Факториал 
N вычисляется как 1 2...
1⋅2⋅...⋅N.
Поскольку это очень быстро растущая функция, то даже для небольших 
N вместимости типов int и long очень скоро не хватит. Поэтому будем использовать BigInteger.

Воспользуйтесь предоставленным шаблоном. Декларацию класса, метод main и обработку ввода-вывода добавит проверяющая система.
#### Решение
```
/**
 * Calculates factorial of given <code>value</code>.
 *
 * @param value positive number
 * @return factorial of <code>value</code>
 */
public static BigInteger factorial(int value) {
  BigInteger result = BigInteger.ONE;
  for (int i = 1; i <= value; i++)
     result = result.multiply(BigInteger.valueOf(i));
  return result;

}
```
#### Задача
Реализуйте метод, сливающий два отсортированных по неубыванию массива чисел в один отсортированный в том же порядке массив. Массивы могут быть любой длины, в том числе нулевой.

Предполагается, что вы реализуете алгоритм слияния, имеющий линейную сложность: он будет идти по двум исходным массивам и сразу формировать отсортированный результирующий массив. Так, чтобы сортировка полученного массива при помощи Arrays.sort() уже не требовалась. К сожалению, автоматически это не проверить, так что это остается на вашей совести :)

Воспользуйтесь предоставленным шаблоном. Декларацию класса, метод main и обработку ввода-вывода добавит проверяющая система.

Пример

Если на вход подаются массивы {0, 2, 2} и {1, 3}, то на выходе должен получиться массив {0, 1, 2, 2, 3}
#### Решение
[Слияние массивов](https://habr.com/ru/articles/281675/)
```
/**
 * Merges two given sorted arrays into one
 *
 * @param a1 first sorted array
 * @param a2 second sorted array
 * @return new array containing all elements from a1 and a2, sorted
 */
public static int[] mergeArrays(int[] a1, int[] a2) {
            int[] a3 = new int[a1.length + a2.length];

        int i=0, j=0;
        for (int k=0; k<a3.length; k++) {

            if (i > a1.length-1) {
                int a = a2[j];
                a3[k] = a;
                j++;
            }
            else if (j > a2.length-1) {
                int a = a1[i];
                a3[k] = a;
                i++;
            }
            else if (a1[i] < a2[j]) {
                int a = a1[i];
                a3[k] = a;
                i++;
            }
            else {
                int b = a2[j];
                a3[k] = b;
                j++;
            }
        }
        Arrays.toString(a3);
        return a3;
}
```
Альтернативные решения:
Решение через ide
```
import java.util.Arrays;

class Hello{
    public static void main(String[] args) {
    int[] a1 = new int[] {21,2,6,4,9};
    int[] a2 = new int[] {1,2,3,8,9,7};
        int[] a3 = new int[a1.length + a2.length];

        int i=0, j=0;
        for (int k=0; k<a3.length; k++) {

            if (i > a1.length-1) {
                int a = a2[j];
                a3[k] = a;
                j++;
            }
            else if (j > a2.length-1) {
                int a = a1[i];
                a3[k] = a;
                i++;
            }
            else if (a1[i] < a2[j]) {
                int a = a1[i];
                a3[k] = a;
                i++;
            }
            else {
                int b = a2[j];
                a3[k] = b;
                j++;
            }
        }
        Arrays.sort(a3);
        System.out.println(Arrays.toString(a3));
    }}

```
#### Задача
Вам дан список ролей и сценарий пьесы в виде массива строчек.

Каждая строчка сценария пьесы дана в следующем виде:
Роль: текст

Текст может содержать любые символы.

Напишите метод, который будет группировать строчки по ролям, пронумеровывать их и возвращать результат в виде готового текста (см. пример). Каждая группа распечатывается в следующем виде:

Роль:
i) текст
j) текст2
...
==перевод строки==

i и j -- номера строк в сценарии. Индексация строчек начинается с единицы, выводить группы следует в соответствии с порядком ролей. Переводы строк между группами обязательны, переводы строк в конце текста не учитываются.

Заметим, что вам предстоит обработка огромной пьесы в 50 000 строк для 10 ролей – соответственно, неправильная сборка результирующей строчки может выйти за ограничение по времени.

Обратите внимание еще на несколько нюансов:

имя персонажа может встречаться в строке более одного раза, в том числе с двоеточием;
название одной роли может быть префиксом названия другой роли (например, "Лука" и "Лука Лукич");
роль, у которой нет реплик, тоже должна присутствовать в выходном файле;
в качестве перевода строки надо использовать символ '\n' (перевод строки в стиле UNIX);
будьте внимательны, не добавляйте лишних пробелов в конце строк.
Sample Input:

roles:
Городничий
Аммос Федорович
Артемий Филиппович
Лука Лукич
textLines:
Городничий: Я пригласил вас, господа, с тем, чтобы сообщить вам пренеприятное известие: к нам едет ревизор.
Аммос Федорович: Как ревизор?
Артемий Филиппович: Как ревизор?
Городничий: Ревизор из Петербурга, инкогнито. И еще с секретным предписаньем.
Аммос Федорович: Вот те на!
Артемий Филиппович: Вот не было заботы, так подай!
Лука Лукич: Господи боже! еще и с секретным предписаньем!
Sample Output:

Городничий:
1) Я пригласил вас, господа, с тем, чтобы сообщить вам пренеприятное известие: к нам едет ревизор.
4) Ревизор из Петербурга, инкогнито. И еще с секретным предписаньем.

Аммос Федорович:
2) Как ревизор?
5) Вот те на!

Артемий Филиппович:
3) Как ревизор?
6) Вот не было заботы, так подай!

Лука Лукич:
7) Господи боже! еще и с секретным предписаньем!
#### Решение
```
private String printTextPerRole(String[] roles, String[] textLines) {
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < roles.length; i++){
            String name = roles[i];
            result.append(name).append(":").append("\n");
            for (int j = 0; j < textLines.length; j++){
                if (textLines[j].startsWith(name + ":")){
                    result.append(j + 1).append(") ").append(textLines[j].replaceFirst(name + ": ", "")).append("\n");
                }
            }
            result.append("\n");
        }
        return result.toString();
    }
```
Альтернативные решения:
В ide сделал.
```
import java.util.Arrays;

class Main{
    public static void main(String[] args) {
        String [] roles= {
                "Городничий","Аммос Федорович",
                "Артемий Филиппович",
                "Лука Лукич"};
        String [] textLines={"Городничий: Я пригласил вас, господа, с тем, чтобы сообщить вам пренеприятное известие: к нам едет ревизор.",
                "Аммос Федорович: Как ревизор?",
                "Артемий Филиппович: Как ревизор?",
                "Городничий: Ревизор из Петербурга, инкогнито. И еще с секретным предписаньем.",
                "Аммос Федорович: Вот те на!",
                "Артемий Филиппович: Вот не было заботы, так подай!",
                "Лука Лукич: Господи боже! еще и с секретным предписаньем!"};
        StringBuilder result = new StringBuilder();
        for (int i = 0; i <roles.length ; i++) {
            String name = roles[i];
            result.append(name).append(":").append("\n");
            for (int j=0;j<textLines.length;j++){
                if(textLines[j].startsWith(name + ":")){
                    result.append(j+1).append(") ").append(textLines[j].replaceFirst(name+": ", "")).append("\n");
                }
            }
            System.out.println();
        }
        System.out.println(result);
    }}

```
#### Задача
На игровом поле находится робот. Позиция робота на поле описывается двумя целочисленным координатами: X и Y. Ось X смотрит слева направо, ось Y — снизу вверх. (Помните, как рисовали графики функций в школе?)

В начальный момент робот находится в некоторой позиции на поле. Также известно, куда робот смотрит: вверх, вниз, направо или налево. Ваша задача — привести робота в заданную точку игрового поля.

Робот описывается классом Robot. Вы можете пользоваться следующими его методами (реализация вам неизвестна):
```
public class Robot {

    public Direction getDirection() {
        // текущее направление взгляда
    }

    public int getX() {
        // текущая координата X
    }

    public int getY() {
        // текущая координата Y
    }

    public void turnLeft() {
        // повернуться на 90 градусов против часовой стрелки
    }

    public void turnRight() {
        // повернуться на 90 градусов по часовой стрелке
    }

    public void stepForward() {
        // шаг в направлении взгляда
        // за один шаг робот изменяет одну свою координату на единицу
    }
}
```
Direction, направление взгляда робота,  — это перечисление:
```
public enum Direction {
    UP,
    DOWN,
    LEFT,
    RIGHT
}
```

Как это  выглядит:

![alt](/img/robot.png)


Пример

В метод передано: toX == 3, toY == 0; начальное состояние робота такое: robot.getX() == 0, robot.getY() == 0, robot.getDirection() == Direction.UP

Чтобы привести робота в указанную точку (3, 0), метод должен вызвать у робота следующие методы:
```
robot.turnRight();
robot.stepForward();
robot.stepForward();
robot.stepForward();
```

P.S. Если вам понравилось это задание, то вам может прийтись по душе игра Robocode, в которой надо написать алгоритм управления танком. Алгоритмы, написанные разными людьми, соревнуются между собой.
#### Решение
Плохо понял задачу, решение из коментов.
```
 public static void moveRobot(Robot robot, int toX, int toY) {
        if (toX < robot.getX()) {
            turnToDirection(robot, Direction.LEFT);
        } else if (toX > robot.getX()) {
            turnToDirection(robot, Direction.RIGHT);
        }
        robotWalks(robot, 'x', toX);
        if (toY < robot.getY()) {
            turnToDirection(robot, Direction.DOWN);
        } else if (toY > robot.getY()) {
            turnToDirection(robot, Direction.UP);
        }
        robotWalks(robot, 'y', toY);
    }

    public static void turnToDirection(Robot robot, Direction dir) {
        while (robot.getDirection() != dir) {
            robot.turnRight();
        }
    }

    public static void robotWalks(Robot robot, char coordinate, int destination) {
        final char x = 'x';
        final char y = 'y';
        if (coordinate == x) {
            while (robot.getX() != destination) {
                robot.stepForward();
            }
        } else if (coordinate == y) {
            while (robot.getY() != destination) {
                robot.stepForward();
            }
        } else {
            throw new IllegalArgumentException("wrong coordinate name (must be x or y)");
        }
    }
```
Альтернативные решения:

```

```

#### Задача
Дан класс ComplexNumber. Переопределите в нем методы equals() и hashCode() так, чтобы equals() сравнивал экземпляры ComplexNumber по содержимому полей re и im, а hashCode() был бы согласованным с реализацией equals().

Реализация hashCode(), возвращающая константу или не учитывающая дробную часть re и im, засчитана не будет

Пример

ComplexNumber a = new ComplexNumber(1, 1);
ComplexNumber b = new ComplexNumber(1, 1);
// a.equals(b) must return true
// a.hashCode() must be equal to b.hashCode()

Подсказка 1. Поищите в классе java.lang.Double статический метод, который поможет в решении задачи.
Подсказка 2. Если задача никак не решается, можно позвать на помощь среду разработки, которая умеет сама генерировать equals() и hashCode(). Если вы воспользовались помощью IDE, то разберитесь, что было сгенерировано и почему оно выглядит именно так. Когда вас на собеседовании попросят на бумажке реализовать equals() и hashCode() для какого-нибудь простого класса, то среда разработки помочь не сможет.
#### Решение
С коментов.
```
public final class ComplexNumber {
    private final double re;
    private final double im;

    public ComplexNumber(double re, double im) {
        this.re = re;
        this.im = im;
    }
    public double getRe() {
        return re;
    }
    public double getIm() {
        return im;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null || obj.getClass() != this.getClass())
            return false;
        if (obj.getClass() == this.getClass()) {
            ComplexNumber other = (ComplexNumber) obj;
            if (other.re == this.re && other.im == this.im)
                return true;
        }
        return false;
    }
    @Override
    public int hashCode() {
        final int prime = 505;
        int reint = Double.hashCode(re);
        int imint =Double.hashCode(im);
        int result = 1;
        result = prime * result + reint;
        result = prime * result + imint;
        return result;
    }

}
```


#### Задача
Реализуйте метод, выполняющий численное интегрирование заданной функции на заданном интервале по формуле левых прямоугольников.

Функция задана объектом, реализующим интерфейс java.util.function.DoubleUnaryOperator. Его метод applyAsDouble() принимает значение аргумента и возвращает значение функции в заданной точке.

Интервал интегрирования задается его конечными точками 
a и b, причем a<=b. Для получения достаточно точного результата используйте шаг сетки не больше 10(−6).

Пример. Вызов

integrate(x -> 1, 0, 10)
должен возвращать значение 10.

P.S. Если задача слишком легкая, то дополнительно можете реализовать динамический выбор шага сетки по следующему алгоритму:

Вычислить приближенное значение интеграла функции при начальном значении шага сетки (например, 1).
Вычислить приближенное значение интеграла функции при более мелком шаге сетки (например, уменьшить шаг сетки в два раза).
Если разность двух последовательных приближений интеграла функции достаточно мала, то завершаем алгоритм и возвращаем текущее приближение в качестве результата.
Иначе возвращаемся к шагу 2.
#### Решение

```
public static double integrate(DoubleUnaryOperator f, double a, double b) {
    double n = 10000000;
    double h = Math.abs(b - a) / n;
    double result = 0;
    //f = (s) -> Math.sin(s);

    for(int i = 0; i < n; i++) {
        result +=  f.applyAsDouble(a + h * i);
    }

    return result *= h;
}
```

#### Задача
Напишите класс AsciiCharSequence, реализующий компактное хранение последовательности ASCII-символов (их коды влезают в один байт) в массиве байт. По сравнению с классом String, хранящим каждый символ как char, AsciiCharSequence будет занимать в два раза меньше памяти.

Класс AsciiCharSequence должен:

реализовывать интерфейс java.lang.CharSequence;
иметь конструктор, принимающий массив байт;
определять методы length(), charAt(), subSequence() и toString()
Сигнатуры методов и ожидания по их поведению смотрите в описании интерфейса java.lang.CharSequence (JavaDoc или исходники).

В данном задании методам charAt() и subSequence() всегда будут подаваться корректные входные параметры, поэтому их проверкой и обработкой ошибок заниматься не нужно. Тем более мы еще не проходили исключения.

P.S. В Java 9 ожидается подобная оптимизация в самом классе String: http://openjdk.java.net/jeps/254
#### Решение

```
public class AsciiCharSequence implements CharSequence {
    private byte[] data;

    public AsciiCharSequence(byte[] data) {
        this.data = data;
    }

    @Override
    public int length() {
        return data.length;
    }

    @Override
    public char charAt(int index) {
        return (char) (data[index] & 0xff);
    }

    @Override
    public CharSequence subSequence(int start, int end) {
        int length = end - start;
        byte[] bytes = new byte[length];
        for (int i = 0, j = start; i < length; i++, j++) {
            bytes[i] = data[j];
        }
        return new AsciiCharSequence(bytes);
    }

    @Override
    public String toString() {
        return new String(data);
    }
}

```

#### Задача
Пришло время попробовать реализовать иерархию классов определенного вида и решить конкретную задачу.

Представим, вы делаете систему фильтрации комментариев на каком-то веб-портале, будь то новости, видео-хостинг, а может даже для системы онлайн-обучения :)

Вы хотите фильтровать комментарии по разным критериям, уметь легко добавлять новые фильтры и модифицировать старые.

Допустим, мы будем фильтровать спам, комментарии с негативным содержанием и слишком длинные комментарии.
Спам будем фильтровать по наличию указанных ключевых слов в тексте.
Негативное содержание будем определять по наличию одного из трех смайликов – :( =( :|
Слишком длинные комментарии будем определять исходя из данного числа – максимальной длины комментария.

Вы решили абстрагировать фильтр в виде следующего интерфейса:
interface TextAnalyzer {
    Label processText(String text);
}
Label – тип-перечисление, которые содержит метки, которыми будем помечать текст:
enum Label {
    SPAM, NEGATIVE_TEXT, TOO_LONG, OK
}
Дальше, вам необходимо реализовать три класса, которые реализуют данный интерфейс: SpamAnalyzer, NegativeTextAnalyzer и TooLongTextAnalyzer.
SpamAnalyzer должен конструироваться от массива строк с ключевыми словами. Объект этого класса должен сохранять в своем состоянии этот массив строк в приватном поле keywords.
NegativeTextAnalyzer должен конструироваться конструктором по-умолчанию.
TooLongTextAnalyzer должен конструироваться от int'а с максимальной допустимой длиной комментария. Объект этого класса должен сохранять в своем состоянии это число в приватном поле maxLength.
Наверняка вы уже заметили, что SpamAnalyzer и NegativeTextAnalyzer во многом похожи – они оба проверяют текст на наличие каких-либо ключевых слов (в случае спама мы получаем их из конструктора, в случае негативного текста мы заранее знаем набор грустных смайликов) и в случае нахождения одного из ключевых слов возвращают  Label (SPAM и NEGATIVE_TEXT соответственно), а если ничего не нашлось – возвращают OK.
Давайте эту логику абстрагируем в абстрактный класс KeywordAnalyzer следующим образом:
Выделим два абстрактных метода getKeywords и getLabel, один из которых будет возвращать набор ключевых слов, а второй метку, которой необходимо пометить положительные срабатывания. Нам незачем показывать эти методы потребителям классов, поэтому оставим доступ к ним только для наследников.
Реализуем processText таким образом, чтобы он зависел только от getKeywords и getLabel.
Сделаем SpamAnalyzer и NegativeTextAnalyzer наследниками KeywordAnalyzer и реализуем абстрактные методы.

Последний штрих – написать метод checkLabels, который будет возвращать метку для комментария по набору анализаторов текста. checkLabels должен возвращать первую не-OK метку в порядке данного набора анализаторов, и OK, если все анализаторы вернули OK.
Используйте, пожалуйста, модификатор доступа по-умолчанию для всех классов.
В итоге, реализуйте классы KeywordAnalyzer, SpamAnalyzer, NegativeTextAnalyzer и TooLongTextAnalyzer и метод checkLabels. TextAnalyzer и Label уже подключены, лишние импорты вам не потребуются.
#### Решение
```
abstract class KeywordAnalyzer implements TextAnalyzer {


  abstract protected String[] getKeywords();

  abstract protected Label getLabel();

  @Override
  public Label processText(String text) {
    for (String keyword : getKeywords()) {
      if (text.contains(keyword))
        return getLabel();
    }
    return Label.OK;
  }
}

class SpamAnalyzer extends KeywordAnalyzer {
  private String[] keywords;
  private Label label;
  public SpamAnalyzer(String[] keywords) {
    this.keywords = keywords.clone();
    label = Label.SPAM;
  }

  @Override
  protected String[] getKeywords() {
    return keywords;
  }

  @Override
  protected Label getLabel() {
    return label;
  }
}

class NegativeTextAnalyzer extends KeywordAnalyzer {
  private String[] keywords;
  private Label label;
  public NegativeTextAnalyzer() {
    this.keywords = new String[3];
    this.keywords[0] = ":(";
    this.keywords[1] = "=(";
    this.keywords[2] = ":|";
    label = Label.NEGATIVE_TEXT;
  }

  @Override
  protected String[] getKeywords() {
    return keywords;
  }

  @Override
  protected Label getLabel() {
    return label;
  }

}

class TooLongTextAnalyzer implements TextAnalyzer {
  private int maxLength;

  public TooLongTextAnalyzer(int maxLength) {
    this.maxLength = maxLength;
  }

  @Override
  public Label processText(String text) {
    if (text.length() > maxLength)
      return Label.TOO_LONG;
    return Label.OK;
  }

}

public Label checkLabels(TextAnalyzer[] analyzers, String text) {
   for(TextAnalyzer analyzer: analyzers) {
        if(analyzer.processText(text) != Label.OK) return analyzer.processText(text);
   }
    return Label.OK;
}
```
Альтернативные решения:

```

```

#### Задача
#### Решение

```

```
Альтернативные решения:

```

```

#### Задача
#### Решение

```

```
Альтернативные решения:

```

```

#### Задача
#### Решение

```

```
Альтернативные решения:

```

```