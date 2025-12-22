# Полная лекция по Dart и типам данных

## Часть 1: Введение в Dart

### 1.1 История и контекст языка

Dart — это современный, статически типизированный язык программирования, разработанный компанией Google в 2011 году. Первоначально язык был задуман как замена JavaScript для веб-разработки, однако с течением времени область его применения значительно расширилась.

Поворотный момент в истории Dart наступил в 2017 году, когда Google представила фреймворк **Flutter**. Flutter — это UI-фреймворк для создания кроссплатформенных приложений на мобильных платформах, веб и десктопе. Именно благодаря Flutter язык Dart получил широкое признание и стал одним из самых быстрорастущих языков программирования.

Сегодня Dart используется:
- в мобильной разработке (через Flutter) — приложения Google Ads, Google Pay, Alibaba, BMW и многие другие
- в веб-разработке (компиляция в JavaScript)
- в серверной разработке (менее распространено, но возможно)
- в десктопной разработке (через Flutter Desktop)

### 1.2 Основные характеристики Dart

**Статическая типизация с выводом типов (Type Inference)**  
Dart требует указания типов переменных, но часто может сам определить тип на основе значения. Это обеспечивает безопасность типов при компиляции и помогает выловить ошибки на ранней стадии разработки.

**Null Safety**  
Одна из самых инновационных особенностей Dart — встроенная защита от ошибок, связанных с null-значениями. В Dart переменная не может быть null, если её тип это не позволяет. Это предотвращает огромное количество ошибок времени выполнения.

**Объектно-ориентированное программирование**  
Всё в Dart является объектом, включая числа, строки и даже null. Язык полностью поддерживает наследование, интерфейсы и абстрактные классы.

**Функциональное программирование**  
Dart поддерживает функции как объекты первого класса (first-class functions), замыкания (closures), лямбда-выражения и многие функциональные парадигмы.

**Быстрая компиляция**  
Dart компилируется как в машинный код (для мобильных приложений), так и в JavaScript (для веба). Компиляция происходит достаточно быстро, что позволяет использовать функцию Hot Reload в Flutter.

### 1.3 Почему выбирают Dart

1. **Простота изучения** — синтаксис похож на Java, JavaScript и C#. Если вы знакомы с одним из этих языков, Dart будет легко осваивать.

2. **Кроссплатформенность** — напишите код один раз, запустите везде (iOS, Android, Web, Windows, macOS, Linux).

3. **Производительность** — благодаря компиляции в машинный код и оптимизированному JIT-компилятору, приложения на Dart работают быстро.

4. **Сообщество** — большое и растущее сообщество разработчиков, много готовых пакетов и библиотек.

5. **Инструментарий** — хорошие инструменты для разработки, отладки и тестирования.

---

## Часть 2: Типы данных в Dart

### 2.1 Числовые типы

#### 2.1.1 Integer (int)

Integer — целые числа без десятичной части. В Dart тип `int` может представлять как маленькие числа, так и очень большие числа (если компилировано в JavaScript, есть ограничения).

```dart
void main() {
  int age = 25;
  int negativeNumber = -100;
  int largeNumber = 9223372036854775807; // макс значение в 64-битном int

  print('Age: $age');
  print('Negative: $negativeNumber');
  print('Large: $largeNumber');

  // Операции с int
  int sum = 10 + 5;        // 15
  int difference = 10 - 3; // 7
  int product = 4 * 5;     // 20
  int quotient = 20 ~/ 3;  // 6 (целочисленное деление)
  int remainder = 20 % 3;  // 2 (остаток от деления)

  print('Sum: $sum');
  print('Quotient: $quotient');
  print('Remainder: $remainder');

  // Полезные методы
  print('Absolute: ${-10.abs()}');      // 10
  print('Is Even: ${10.isEven}');       // true
  print('Is Odd: ${10.isOdd}');         // false
  print('Sign: ${-5.sign}');            // -1
}
```

**Особенности int:**
- В Dart Web (компиляция в JavaScript) int может быть максимум 2^53 - 1
- В Dart VM (машинный код) int может быть до 2^63 - 1
- Деление `a / b` возвращает double, даже если оба операнда int
- Целочисленное деление `a ~/ b` возвращает int
- Получить остаток можно через `%`

#### 2.1.2 Double (double)

Double — числа с плавающей точкой. Представляют собой числа с дробной частью.

```dart
void main() {
  double pi = 3.14159;
  double height = 1.75;
  double negative = -2.5;
  double scientific = 1.23e5; // 123000.0 (научная нотация)
  double verySmall = 1.5e-3;  // 0.0015

  print('Pi: $pi');
  print('Height: $height');
  print('Scientific: $scientific');
  print('Very small: $verySmall');

  // Операции с double
  double sum = 10.5 + 2.3;     // 12.8
  double difference = 10.5 - 2.3; // 8.2
  double product = 3.5 * 2.0;    // 7.0
  double quotient = 10.0 / 3.0;  // 3.333...

  print('Sum: $sum');
  print('Quotient: $quotient');

  // Полезные методы
  print('Absolute: ${-5.5.abs()}');           // 5.5
  print('Ceil: ${3.2.ceil()}');               // 4
  print('Floor: ${3.9.floor()}');             // 3
  print('Round: ${3.5.round()}');             // 4
  print('To Int: ${3.9.toInt()}');            // 3
  print('Is Finite: ${(10.0).isFinite}');     // true
  print('Is Infinite: ${double.infinity.isInfinite}'); // true
  print('Is NaN: ${double.nan.isNaN}');       // true

  // Специальные значения
  print('Infinity: ${double.infinity}');
  print('Negative Infinity: ${double.negativeInfinity}');
  print('NaN: ${double.nan}');
}
```

**Особенности double:**
- Double в Dart соответствует IEEE 754 стандарту (64-битные значения)
- Могут быть не совсем точными из-за представления в виде двоичных дробей
- Поддерживает специальные значения: `infinity`, `negativeInfinity`, `nan`
- Может быть записано в научной нотации (`1.5e-3`)

#### 2.1.3 num (числовой супертип)

Тип `num` является супертипом для `int` и `double`. Используется, когда функция должна принимать оба типа.

```dart
void main() {
  num integer = 10;
  num floating = 3.14;

  print('Integer: $integer');
  print('Floating: $floating');

  // Функция, принимающая num
  print('Integer + 5 = ${add(10, 5)}');
  print('Double + 2.5 = ${add(3.14, 2.5)}');
}

// Функция, принимающая num
num add(num a, num b) {
  return a + b;
}
```

### 2.2 Строки (String)

Строки в Dart представляют последовательность символов Unicode. Это один из самых часто используемых типов данных.

#### 2.2.1 Создание строк

```dart
void main() {
  // Одинарные кавычки
  String single = 'Hello';

  // Двойные кавычки
  String double = "Hello";

  // Тройные кавычки (многострочные)
  String multiline = '''
    Это многострочная
    строка в Dart.
    Хорошо сохраняет
    форматирование
  ''';

  // Сырые строки (raw strings) - не интерпретирует символы
  String raw = r'Это \n не будет новой строкой';

  print('Single: $single');
  print('Double: $double');
  print('Multiline:\n$multiline');
  print('Raw: $raw');
}
```

#### 2.2.2 Интерполяция строк

Интерполяция позволяет вставлять переменные прямо в строку.

```dart
void main() {
  String name = 'Иван';
  int age = 25;
  double salary = 50000.50;

  // Простая интерполяция
  print('Имя: $name');
  print('Возраст: $age');
  print('Зарплата: $salary');

  // Интерполяция с выражениями
  print('Завтра мне будет ${age + 1} лет');
  print('Годовая зарплата: ${salary * 12}');
  print('Строчное преобразование: ${name.toUpperCase()}');

  // Сложные выражения в интерполяции
  print('Расчёт: ${(10 + 5) * 2}');
  print('Условие: ${age >= 18 ? "взрослый" : "ребенок"}');

  // Если нужно вывести $, используйте $$
  print('Цена: \$100');
}
```

#### 2.2.3 Операции со строками

```dart
void main() {
  String text = 'Hello, Dart!';

  // Длина строки
  print('Length: ${text.length}'); // 12

  // Доступ к символу по индексу
  print('First char: ${text[0]}'); // H
  print('Last char: ${text[text.length - 1]}'); // !

  // Преобразование регистра
  print('Upper: ${text.toUpperCase()}');   // HELLO, DART!
  print('Lower: ${text.toLowerCase()}');   // hello, dart!

  // Поиск подстроки
  print('Contains "Dart": ${text.contains('Dart')}'); // true
  print('Index of "Dart": ${text.indexOf('Dart')}');  // 7
  print('Starts with "Hello": ${text.startsWith('Hello')}'); // true
  print('Ends with "!": ${text.endsWith('!')}'); // true

  // Подстрока
  print('Substring [0:5]: ${text.substring(0, 5)}'); // Hello
  print('Substring [7:11]: ${text.substring(7, 11)}'); // Dart

  // Разделение строки
  String csv = 'apple,banana,orange';
  List<String> fruits = csv.split(',');
  print('Fruits: $fruits');

  // Замена
  print('Replace: ${text.replaceAll('Dart', 'World')}');
  print('Replace first: ${text.replaceFirst('l', 'L')}');

  // Удаление пробелов
  String spaces = '  hello world  ';
  print('Trimmed: "${spaces.trim()}"');

  // Повтор строки
  print('Repeat: ${'Ha'.padRight(10, '*')}');

  // Проверка пустоты
  print('Is empty: ${"".isEmpty}'); // true
  print('Is not empty: ${text.isNotEmpty}'); // true
}
```

#### 2.2.4 Специальные символы в строках

```dart
void main() {
  // Новая строка
  print('Line 1\nLine 2');

  // Табуляция
  print('Column1\tColumn2\tColumn3');

  // Слэш
  print('Path: C:\\Users\\Name');

  // Кавычка
  print('He said "Hello"');
  print("She said 'Hi'");

  // Обратный слэш
  print('Backslash: \\');

  // Unicode символы
  print('Unicode: \u0048\u0065\u006C\u006C\u006F'); // Hello
  print('Emoji: \u{1F600}'); // 😀
}
```

### 2.3 Boolean (bool)

Логический тип, который может быть `true` или `false`.

```dart
void main() {
  bool isActive = true;
  bool isCompleted = false;

  print('Is Active: $isActive');
  print('Is Completed: $isCompleted');

  // Логические операции
  bool a = true;
  bool b = false;

  print('a && b: ${a && b}');   // AND - false
  print('a || b: ${a || b}');   // OR - true
  print('!a: ${!a}');           // NOT - false

  // Сравнения возвращают bool
  int x = 10;
  int y = 5;

  print('x > y: ${x > y}');     // true
  print('x == y: ${x == y}');   // false
  print('x != y: ${x != y}');   // true
  print('x >= y: ${x >= y}');   // true

  // Условное выражение
  String result = isActive ? 'Active' : 'Inactive';
  print('Status: $result');
}
```

### 2.4 Dynamic тип

Тип `dynamic` позволяет переменной содержать значение любого типа. Это противоположность строгой типизации.

```dart
void main() {
  dynamic value = 'Hello';
  print('Value: $value, Type: ${value.runtimeType}');

  value = 42;
  print('Value: $value, Type: ${value.runtimeType}');

  value = 3.14;
  print('Value: $value, Type: ${value.runtimeType}');

  value = true;
  print('Value: $value, Type: ${value.runtimeType}');

  // Опасно! Ошибка проявится только в runtime
  dynamic name = 'Иван';
  // print(name + 5); // RuntimeError!

  // Проверка типа во время выполнения
  if (name is String) {
    print('$name is a String');
  }
}
```

**Важно:** использование `dynamic` снижает безопасность типов. Избегайте его, если возможно. Используйте `var` или конкретные типы.

---

## Часть 3: Коллекции (Collections)

### 3.1 List (Список)

List — это упорядоченная коллекция элементов одного типа.

#### 3.1.1 Создание и основные операции

```dart
void main() {
  // Создание списка
  List<int> numbers = [1, 2, 3, 4, 5];
  List<String> fruits = ['Apple', 'Banana', 'Orange'];
  List<dynamic> mixed = [1, 'two', 3.0, true];

  // Пустой список
  List<int> empty = [];
  List<String> emptyWithType = <String>[];

  print('Numbers: $numbers');
  print('Fruits: $fruits');
  print('Mixed: $mixed');

  // Доступ к элементам
  print('First number: ${numbers[0]}');    // 1
  print('Second fruit: ${fruits[1]}');     // Banana
  print('Last element: ${numbers[numbers.length - 1]}'); // 5

  // Изменение элемента
  numbers[0] = 10;
  print('Modified: $numbers'); // [10, 2, 3, 4, 5]

  // Проверка длины
  print('Length: ${numbers.length}'); // 5

  // Проверка пустоты
  print('Is empty: ${empty.isEmpty}');     // true
  print('Is not empty: ${numbers.isNotEmpty}'); // true
}
```

#### 3.1.2 Методы для добавления и удаления

```dart
void main() {
  List<int> numbers = [1, 2, 3];

  // Добавление элемента в конец
  numbers.add(4);
  print('After add: $numbers'); // [1, 2, 3, 4]

  // Добавление нескольких элементов
  numbers.addAll([5, 6]);
  print('After addAll: $numbers'); // [1, 2, 3, 4, 5, 6]

  // Вставка элемента в определённую позицию
  numbers.insert(2, 99);
  print('After insert: $numbers'); // [1, 2, 99, 3, 4, 5, 6]

  // Вставка нескольких элементов
  numbers.insertAll(0, [-1, 0]);
  print('After insertAll: $numbers'); // [-1, 0, 1, 2, 99, 3, 4, 5, 6]

  // Удаление элемента по значению (первое вхождение)
  numbers.remove(99);
  print('After remove: $numbers'); // [-1, 0, 1, 2, 3, 4, 5, 6]

  // Удаление элемента по индексу
  numbers.removeAt(0);
  print('After removeAt: $numbers'); // [0, 1, 2, 3, 4, 5, 6]

  // Удаление последнего элемента
  var last = numbers.removeLast();
  print('Removed last: $last, List: $numbers'); // Removed last: 6, List: [0, 1, 2, 3, 4, 5]

  // Удаление элементов по условию
  List<int> nums = [1, 2, 3, 4, 5];
  nums.removeWhere((n) => n > 3);
  print('After removeWhere: $nums'); // [1, 2, 3]

  // Очистка списка
  nums.clear();
  print('After clear: $nums'); // []
}
```

#### 3.1.3 Поиск в списке

```dart
void main() {
  List<int> numbers = [1, 2, 3, 4, 5, 3, 2, 1];

  // Проверка наличия элемента
  print('Contains 3: ${numbers.contains(3)}');   // true
  print('Contains 10: ${numbers.contains(10)}'); // false

  // Индекс первого вхождения
  print('Index of 3: ${numbers.indexOf(3)}');      // 2
  print('Index of 10: ${numbers.indexOf(10)}');    // -1 (не найдено)

  // Индекс последнего вхождения
  print('Last index of 3: ${numbers.lastIndexOf(3)}'); // 5

  // Поиск по условию
  print('First > 3: ${numbers.firstWhere((n) => n > 3, orElse: () => -1)}'); // 4
  print('Last < 3: ${numbers.lastWhere((n) => n < 3, orElse: () => -1)}');   // 2

  // Проверка наличия элемента по условию
  print('Any > 4: ${numbers.any((n) => n > 4)}');   // true
  print('All > 0: ${numbers.all((n) => n > 0)}');   // true
  print('All > 3: ${numbers.all((n) => n > 3)}');   // false
}
```

#### 3.1.4 Преобразование и фильтрация

```dart
void main() {
  List<int> numbers = [1, 2, 3, 4, 5];

  // Map - преобразование каждого элемента
  List<int> doubled = numbers.map((n) => n * 2).toList();
  print('Doubled: $doubled'); // [2, 4, 6, 8, 10]

  List<String> strings = numbers.map((n) => 'Num: $n').toList();
  print('Strings: $strings'); // [Num: 1, Num: 2, Num: 3, Num: 4, Num: 5]

  // Where - фильтрация элементов
  List<int> evens = numbers.where((n) => n % 2 == 0).toList();
  print('Even: $evens'); // [2, 4]

  List<int> odds = numbers.where((n) => n % 2 != 0).toList();
  print('Odd: $odds'); // [1, 3, 5]

  // Expand - развёртывание элементов
  List<int> expanded = numbers.expand((n) => [n, n]).toList();
  print('Expanded: $expanded'); // [1, 1, 2, 2, 3, 3, 4, 4, 5, 5]

  // Reduce - свёртка списка в одно значение
  int sum = numbers.reduce((a, b) => a + b);
  print('Sum: $sum'); // 15

  int product = numbers.reduce((a, b) => a * b);
  print('Product: $product'); // 120

  // Fold - свёртка с начальным значением
  int sumWithInitial = numbers.fold(10, (prev, n) => prev + n);
  print('Sum with initial 10: $sumWithInitial'); // 25

  String concatenated = numbers.fold('', (prev, n) => prev + n.toString());
  print('Concatenated: $concatenated'); // 12345
}
```

#### 3.1.5 Сортировка и упорядочение

```dart
void main() {
  List<int> numbers = [5, 2, 8, 1, 9, 3];

  // Сортировка по умолчанию
  numbers.sort();
  print('Sorted ascending: $numbers'); // [1, 2, 3, 5, 8, 9]

  // Сортировка в обратном порядке
  numbers.sort((a, b) => b.compareTo(a));
  print('Sorted descending: $numbers'); // [9, 8, 5, 3, 2, 1]

  // Список строк
  List<String> words = ['banana', 'apple', 'cherry'];
  words.sort();
  print('Sorted strings: $words'); // [apple, banana, cherry]

  // Обратный порядок
  List<int> reversed = [1, 2, 3, 4, 5].reversed.toList();
  print('Reversed: $reversed'); // [5, 4, 3, 2, 1]

  // Получение подсписка
  List<int> sublist = [1, 2, 3, 4, 5].sublist(1, 4);
  print('Sublist [1:4]: $sublist'); // [2, 3, 4]
}
```

#### 3.1.6 Итерация по списку

```dart
void main() {
  List<String> fruits = ['Apple', 'Banana', 'Orange'];

  // for цикл
  print('=== for loop ===');
  for (int i = 0; i < fruits.length; i++) {
    print('$i: ${fruits[i]}');
  }

  // for-in цикл
  print('=== for-in loop ===');
  for (String fruit in fruits) {
    print(fruit);
  }

  // forEach метод
  print('=== forEach ===');
  fruits.forEach((fruit) {
    print('Fruit: $fruit');
  });

  // forEach с индексом
  print('=== forEach with index ===');
  fruits.asMap().forEach((index, fruit) {
    print('$index: $fruit');
  });
}
```

### 3.2 Map (Словарь)

Map — это коллекция пар "ключ-значение".

#### 3.2.1 Создание и доступ

```dart
void main() {
  // Создание Map
  Map<String, int> ages = {
    'Иван': 25,
    'Мария': 28,
    'Петр': 30
  };

  // Создание с типом
  Map<String, String> capitals = <String, String>{
    'Россия': 'Москва',
    'Франция': 'Париж',
    'Германия': 'Берлин'
  };

  // Создание пустого Map
  Map<String, int> empty = {};
  Map<String, int> emptyWithType = <String, int>{};

  print('Ages: $ages');
  print('Capitals: $capitals');

  // Доступ к значению по ключу
  print('Ivan age: ${ages['Иван']}');         // 25
  print('Russia capital: ${capitals['Россия']}'); // Москва

  // Доступ к несуществующему ключу возвращает null
  print('Unknown: ${ages['Unknown']}');       // null

  // Получение значения с значением по умолчанию
  print('France capital: ${capitals['Франция'] ?? 'Unknown'}'); // Париж
}
```

#### 3.2.2 Добавление и удаление

```dart
void main() {
  Map<String, int> ages = {'Иван': 25, 'Мария': 28};

  // Добавление нового элемента
  ages['Петр'] = 30;
  print('After adding: $ages');

  // Обновление существующего элемента
  ages['Иван'] = 26;
  print('After update: $ages');

  // Добавление нескольких элементов
  ages.addAll({'Анна': 27, 'Виктор': 29});
  print('After addAll: $ages');

  // Удаление элемента по ключу
  ages.remove('Виктор');
  print('After remove: $ages');

  // Удаление элементов по условию
  Map<String, int> nums = {'a': 1, 'b': 2, 'c': 3, 'd': 4};
  nums.removeWhere((key, value) => value > 2);
  print('After removeWhere: $nums'); // {a: 1, b: 2}

  // Очистка Map
  nums.clear();
  print('After clear: $nums');
}
```

#### 3.2.3 Проверки и поиск

```dart
void main() {
  Map<String, int> ages = {
    'Иван': 25,
    'Мария': 28,
    'Петр': 30
  };

  // Проверка наличия ключа
  print('Contains "Иван": ${ages.containsKey('Иван')}');     // true
  print('Contains "Виктор": ${ages.containsKey('Виктор')}'); // false

  // Проверка наличия значения
  print('Contains 25: ${ages.containsValue(25)}');   // true
  print('Contains 35: ${ages.containsValue(35)}');   // false

  // Получение всех ключей
  print('Keys: ${ages.keys}');     // (Иван, Мария, Петр)

  // Получение всех значений
  print('Values: ${ages.values}');  // (25, 28, 30)

  // Получение записей (ключ-значение)
  print('Entries: ${ages.entries}');

  // Проверка пустоты
  print('Is empty: ${ages.isEmpty}');     // false
  print('Is not empty: ${ages.isNotEmpty}'); // true

  // Размер
  print('Length: ${ages.length}'); // 3
}
```

#### 3.2.4 Итерация и преобразование

```dart
void main() {
  Map<String, int> ages = {
    'Иван': 25,
    'Мария': 28,
    'Петр': 30
  };

  // Итерация через forEach
  print('=== forEach ===');
  ages.forEach((name, age) {
    print('$name: $age лет');
  });

  // Итерация через entries
  print('=== entries ===');
  for (var entry in ages.entries) {
    print('${entry.key}: ${entry.value}');
  }

  // Map преобразование (ключи и значения)
  Map<String, int> agesPlus = {};
  ages.forEach((name, age) {
    agesPlus[name] = age + 1;
  });
  print('Ages + 1: $agesPlus');

  // Фильтрация
  Map<String, int> adults = Map.fromEntries(
    ages.entries.where((entry) => entry.value >= 30)
  );
  print('Adults (30+): $adults');
}
```

### 3.3 Set (Множество)

Set — это неупорядоченная коллекция уникальных элементов.

#### 3.3.1 Создание и основные операции

```dart
void main() {
  // Создание Set
  Set<int> numbers = {1, 2, 3, 4, 5};
  Set<String> colors = {'red', 'green', 'blue'};

  // Пустой Set
  Set<int> empty = <int>{};

  print('Numbers: $numbers');
  print('Colors: $colors');

  // Добавление элемента
  numbers.add(6);
  print('After add: $numbers');

  // Добавление нескольких элементов
  numbers.addAll([7, 8, 9]);
  print('After addAll: $numbers');

  // Проверка наличия элемента
  print('Contains 5: ${numbers.contains(5)}');  // true
  print('Contains 10: ${numbers.contains(10)}'); // false

  // Размер
  print('Length: ${numbers.length}');

  // Удаление элемента
  numbers.remove(1);
  print('After remove: $numbers');

  // Удаление по условию
  numbers.removeWhere((n) => n > 7);
  print('After removeWhere: $numbers');

  // Очистка
  empty.clear();
  print('After clear: $empty');
}
```

#### 3.3.2 Операции множеств

```dart
void main() {
  Set<int> set1 = {1, 2, 3, 4};
  Set<int> set2 = {3, 4, 5, 6};

  // Объединение (Union)
  Set<int> union = set1.union(set2);
  print('Union: $union'); // {1, 2, 3, 4, 5, 6}

  // Пересечение (Intersection)
  Set<int> intersection = set1.intersection(set2);
  print('Intersection: $intersection'); // {3, 4}

  // Разность (Difference)
  Set<int> difference = set1.difference(set2);
  print('Difference: $difference'); // {1, 2}

  // Проверка подмножества
  Set<int> subset = {1, 2};
  print('${subset} is subset of ${set1}: ${subset.containsAll(set1.toList())}');

  // Проверка надмножества
  print('${set1} contains all of ${subset}: ${set1.containsAll(subset.toList())}');
}
```

---

## Часть 4: Переменные, константы и область видимости

### 4.1 Объявление переменных

```dart
void main() {
  // var - автоматический вывод типа
  var name = 'Dart';  // String
  var number = 42;    // int
  var pi = 3.14;      // double

  print('Name: $name, Type: ${name.runtimeType}');
  print('Number: $number, Type: ${number.runtimeType}');
  print('Pi: $pi, Type: ${pi.runtimeType}');

  // Явное указание типа
  String greeting = 'Hello';
  int count = 10;
  double rate = 0.95;

  print('Greeting: $greeting');
  print('Count: $count');
  print('Rate: $rate');

  // Позднее связывание типов (избегайте)
  dynamic value = 'text';
  value = 123;
  value = true;
  print('Dynamic: $value');
}
```

### 4.2 final и const

```dart
void main() {
  // final - значение задаётся один раз и не может изменяться
  final String country = 'Russia';
  final List<int> numbers = [1, 2, 3];

  // country = 'USA';  // ОШИБКА!
  // numbers = [4, 5]; // ОШИБКА!

  // Но можно изменять элементы коллекции
  numbers.add(4);
  print('Numbers: $numbers'); // [1, 2, 3, 4]

  // const - константа времени компиляции
  const String language = 'Dart';
  const double radius = 5.0;
  const List<int> codes = [1, 2, 3];

  // language = 'Python'; // ОШИБКА!
  // codes.add(4);        // ОШИБКА!

  print('Language: $language');
  print('Radius: $radius');
  print('Codes: $codes');

  // final может быть инициализирована позже
  final int age;
  age = 25;
  print('Age: $age');

  // const должна быть инициализирована при объявлении
  // const int value;  // ОШИБКА!
}
```

### 4.3 Область видимости

```dart
// Глобальная переменная
int globalCounter = 0;

void function1() {
  // Локальная переменная функции
  int localCounter = 0;
  globalCounter++;
  localCounter++;

  print('Global: $globalCounter, Local: $localCounter');
}

void function2() {
  // globalCounter видна здесь
  print('Global in function2: $globalCounter');

  // localCounter из function1 недоступна
  // print(localCounter); // ОШИБКА!
}

void main() {
  function1(); // Global: 1, Local: 1
  function2(); // Global in function2: 1

  // Блокировка области видимости
  {
    int blockVar = 100;
    print('Block var: $blockVar');
  }

  // blockVar недоступна
  // print(blockVar); // ОШИБКА!
}
```

---

## Часть 5: Null Safety в Dart

### 5.1 Nullable и Non-nullable типы

```dart
void main() {
  // Non-nullable - не может быть null
  String name = 'Dart';
  int age = 25;

  // name = null;  // ОШИБКА при компиляции!
  // age = null;   // ОШИБКА при компиляции!

  // Nullable - может быть null (обозначается ?)
  String? nickname;
  int? score;

  nickname = 'D';
  nickname = null;  // OK

  score = 100;
  score = null;     // OK

  print('Name: $name');
  print('Nickname: $nickname');
  print('Score: $score');
}
```

### 5.2 Операторы для работы с null

#### 5.2.1 Null coalescing (??)

```dart
void main() {
  String? nickname;
  int? score;

  // ?? возвращает левое значение если оно не null, иначе правое
  String displayName = nickname ?? 'Guest';
  print('Name: $displayName'); // Guest

  nickname = 'Developer';
  displayName = nickname ?? 'Guest';
  print('Name: $displayName'); // Developer

  // Цепочка ??
  String? value1;
  String? value2;
  String value3 = 'default';
  String result = value1 ?? value2 ?? value3;
  print('Result: $result'); // default
}
```

#### 5.2.2 Null-aware navigation (?.)

```dart
void main() {
  String? text;

  // print(text.length); // ОШИБКА!

  // ?. - только если не null
  print(text?.length);  // null
  print(text?.toUpperCase()); // null

  text = 'Hello';
  print(text?.length);  // 5
  print(text?.toUpperCase()); // HELLO
}
```

#### 5.2.3 Null assertion (!)

```dart
void main() {
  String? text = 'Hello';

  // ! - утверждение, что значение не null (опасно!)
  String nonNull = text!;
  print('Non-null: $nonNull'); // Hello
  print('Length: ${nonNull.length}');

  // Если значение null, выбросится исключение
  String? nullValue;
  // String error = nullValue!; // ОШИБКА в runtime!
}
```

---

## Часть 6: Типизация и вывод типов

### 6.1 Явная типизация

```dart
void main() {
  // Явное указание типов
  int intValue = 42;
  double doubleValue = 3.14;
  String stringValue = 'Hello';
  bool boolValue = true;
  List<int> listValue = [1, 2, 3];
  Map<String, int> mapValue = {'a': 1, 'b': 2};
  Set<String> setValue = {'x', 'y', 'z'};

  print('Int: $intValue, Type: ${intValue.runtimeType}');
  print('Double: $doubleValue, Type: ${doubleValue.runtimeType}');
  print('String: $stringValue, Type: ${stringValue.runtimeType}');
  print('Bool: $boolValue, Type: ${boolValue.runtimeType}');
  print('List: $listValue, Type: ${listValue.runtimeType}');
  print('Map: $mapValue, Type: ${mapValue.runtimeType}');
  print('Set: $setValue, Type: ${setValue.runtimeType}');
}
```

### 6.2 Вывод типов через var

```dart
void main() {
  // var - тип определяется по значению
  var x = 10;        // int
  var y = 3.14;      // double
  var z = 'Hello';   // String
  var w = true;      // bool
  var list = [1, 2, 3]; // List<int>
  var map = {'a': 1}; // Map<String, int>

  print('x: ${x.runtimeType}');
  print('y: ${y.runtimeType}');
  print('z: ${z.runtimeType}');
  print('w: ${w.runtimeType}');
  print('list: ${list.runtimeType}');
  print('map: ${map.runtimeType}');

  // var не может измениться на другой тип
  // x = 'text'; // ОШИБКА!
}
```

### 6.3 Проверка типов во время выполнения

```dart
void main() {
  dynamic value = 'Hello';

  // is - проверка типа
  if (value is String) {
    print('$value is a String');
  }

  if (value is int) {
    print('$value is an int');
  }

  // is! - отрицание
  if (value is! int) {
    print('$value is not an int');
  }

  // as - приведение типа (опасно!)
  String text = value as String;
  print('As String: $text');

  // Безопасное приведение
  var num = value as int?; // null если неудачно
  print('As int: $num');
}
```

---

## Часть 7: Специальные типы

### 7.1 Void

`void` используется для функций, которые не возвращают значение.

```dart
void printMessage(String message) {
  print('Message: $message');
}

void main() {
  printMessage('Hello');
  printMessage('Dart');
}
```

### 7.2 Never

`Never` используется для функций, которые никогда не возвращают значение (выбрасывают исключение или зацикливаются).

```dart
Never throwError(String message) {
  throw Exception(message);
}

Never infiniteLoop() {
  while (true) {
    print('Loop');
  }
}

void main() {
  // throwError('Test');
  // infiniteLoop();
}
```

---

## Заключение

Типизация в Dart является одной из её главных сильных сторон. Понимание типов данных, null safety и работы с коллекциями критически важно для эффективного программирования на Dart.

Основные точки для запоминания:
- Dart имеет строгую статическую типизацию с выводом типов
- Null safety предотвращает ошибки с null-значениями
- Коллекции (List, Map, Set) являются основными структурами данных
- Используйте `var` для автоматического вывода типов
- Используйте `final` для неизменяемых переменных
- Понимайте разницу между nullable (?) и non-nullable типами
