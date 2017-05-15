---
title: "Лямбда-выражения в C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "лямбда-выражения [C++]"
  - "лямбда-выражения [C++], общие сведения"
  - "лямбда-выражения [C++], или объекты функций"
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Лямбда-выражения в C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Лямбда\-выражение \(или просто *лямбда*\) в C\+\+11 — это удобный способ определения анонимного объекта\-функции непосредственно в месте его вызова или передачи в функцию в качестве аргумента.  Обычно лямбда\-выражения используются для инкапсуляции нескольких строк кода, передаваемых алгоритмам или асинхронным методам.  В этой статье приводится определение лямбда\-выражений, их сравнение с другими методами программирования, описание их преимуществ и простой пример.  
  
## Структура лямбда\-выражения  
 В стандарте ISO C\+\+ демонстрируется простое лямбда\-выражение, передаваемое функции `std::sort()` в качестве третьего аргумента:  
  
```cpp  
#include <algorithm>  
#include <cmath>  
  
void abssort(float* x, unsigned n) {  
    std::sort(x, x + n,  
        // Lambda expression begins  
        [](float a, float b) {  
            return (std::abs(a) < std::abs(b));  
        } // end of lambda expression  
    );  
}  
  
```  
  
 На следующем рисунке показана структура лямбда\-выражения:  
  
 ![Структурные элементы лямбда&#45;выражения](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *предложение фиксации* \(в спецификации C\+\+ это *lambda\-introducer*.\)  
  
2.  *список параметров* \(необязательно\).  \(Также именуется как *lambda declarator*.\)  
  
3.  *отключаемая спецификация* \(необязательно\).  
  
4.  *спецификация исключений* \(необязательно\).  
  
5.  *завершающий возвращаемый тип* \(необязательно\).  
  
6.  *тело лямбда\-выражения*\)  
  
### Предложение фиксации  
 В теле лямбда\-выражения могут вводиться новые переменные \(в **C \+\+14**\). Кроме того, лямбда\-выражения могут использовать, или *фиксировать*, переменные из окружающей области видимости.  Лямбда\-выражение начинается с предложения фиксации \(в синтаксисе стандарта — *lambda\-introducer*\), в котором указываются фиксируемые переменные, а также способ фиксации: по значению или по ссылке.  Доступ к переменным с префиксом с амперсандом \(`&`\) осуществляется по ссылке, а к переменным без префикса — по значению.  
  
 Пустое предложение фиксации \(`[ ]`\) показывает, что тело лямбда\-выражения не осуществляет доступ к переменным во внешней области видимости.  
  
 Чтобы задать способ фиксации внешних переменных, на которые ссылается лямбда\-выражение, вы можете использовать режим фиксации по умолчанию \(в синтаксисе стандарта — `capture-default`\): \[&\] — все переменные фиксируются по ссылке, \[\=\] — по значению.  Можно сначала использовать режим фиксации по умолчанию, а затем применить для определенных переменных другой режим.  Например, если тело лямбда\-выражения осуществляет доступ к внешней переменной `total` по ссылке, а к внешней переменной `factor` по значению, следующие предложения фиксации эквивалентны:  
  
```cpp  
  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 При использовании `capture-default` фиксируются только переменные, упомянутые в лямбда\-выражении.  
  
 Если предложение фиксации включает `capture-default` `&`, ни один `identifier` в параметре `capture` этого предложения фиксации не может иметь форму `& identifier`.  Аналогично, если предложение фиксации включает `capture-default` `=`, ни один параметр `capture` этого предложения фиксации не может иметь форму `= identifier`.  Идентификатор или `this` не могут использоваться более одного раза в предложении захвата.  В следующем фрагменте кода приводится несколько примеров.  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};    // OK  
    [&, &i]{};   // ERROR: i preceded by & when & is the default  
    [=, this]{}; // ERROR: this when = is the default  
    [i, i]{};    // ERROR: i repeated  
}  
```  
  
 `capture` с последующим многоточием является расширением пакета, как показано в следующем примере [шаблона с переменным числом аргументов](../cpp/ellipses-and-variadic-templates.md):  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 Чтобы использовать лямбда\-выражения в теле метода класса, необходимо передать указатель `this` предложению фиксации, чтобы обеспечить доступ к методам и данным\-членам включающего класса.  Пример использования лямбда\-выражений с методами классов см. в разделе [Примеры лямбда\-выражений](../cpp/examples-of-lambda-expressions.md) \(подраздел "Использование лямбда\-выражения в методе"\).  
  
 При использовании предложения фиксации рекомендуется помнить об этих важных аспектах, особенно при использовании лямбда\-выражений с многопоточностью:  
  
-   Фиксацию ссылок можно использовать для изменения переменных снаружи, тогда как фиксацию значений нельзя.  \(`mutable` позволяет изменять копии, но не оригиналы.\)  
  
-   Фиксация ссылок отражает изменение переменных снаружи, тогда как фиксация значений — нет.  
  
-   Фиксация ссылки вводит зависимость от времени существования, тогда как фиксация значения не обладает зависимостями от времени существования.  Это особенно важно в случае асинхронного использования лямбда\-выражений.  Если в асинхронном лямбда\-выражении по ссылке фиксируется локальная переменная, вполне вероятно, что к моменту его вызова она станет недоступной, что вызовет исключение нарушения прав доступа во время выполнения.  
  
 **Обобщенная фиксация \(C\+\+14\)**  
  
 В C\+\+14 вы можете объявлять и инициализировать новые переменные в предложении фиксации. Для этого не требуется, чтобы эти переменные существовали во внешней области видимости лямбда\-функции.  Инициализация может быть выражена в качестве любого произвольного выражения. Тип новой переменной определяется типом, который создается выражением.  Одно из преимуществ этой возможности заключается в том, что в C\+\+14 таким образом можно фиксировать переменные из окружающей области видимости, доступные только для перемещения \(например std::unique\_ptr\), и использовать их в лямбда\-выражении.  
  
```  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### Список параметров  
 В дополнение к возможности фиксации переменных, лямбда\-выражения могут принимать входные параметры.  Список параметров \(в синтаксисе стандарта — *lambda declarator*\) является необязательным элементом и, по большей части, походит на список параметров функции.  
  
```  
int y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 В **C\+\+14**, если используются универсальные параметры, в качестве спецификатора типа можно задействовать ключевое слово auto.  Это отдает компилятору команду создать оператор вызова функции в качестве шаблона.  Каждый экземпляр ключевого слова auto в списке параметров эквивалентен параметру отдельного типа.  
  
```  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Лямбда\-выражение может принимать другое лямбда\-выражение в качестве своего аргумента.  Дополнительные сведения см. в разделе [Примеры лямбда\-выражений](../cpp/examples-of-lambda-expressions.md) \(подраздел "Лямбда\-выражения высшего порядка"\).  
  
 Поскольку список параметров является необязательным, можно опустить пустые скобки, если аргументы не передаются в лямбда\-выражение и `lambda-declarator:` не содержит элементы *exception\-specification*, *trailing\-return\-type* или `mutable`.  
  
### Отключаемая спецификация  
 Как правило, оператор вызова функции лямбда\-выражения является константой по значению, но ключевое слово `mutable` отменяет это.  Он не создает изменяемые данные\-члены.  Отключаемая спецификация позволяет телу лямбда\-выражения изменять переменные, захваченные по значению.  Некоторые примеры далее в этой статье демонстрируют использование ключевого слова `mutable`.  
  
### Спецификация исключений  
 Можно использовать спецификацию исключений `throw()`, чтобы указать, что лямбда\-выражение не создает исключений.  Как и в случае с обычными функциями, компилятор Visual C\+\+ создает предупреждение [C4297](../Topic/Compiler%20Warning%20\(level%201\)%20C4297.md), если лямбда\-выражение объявляет спецификацию исключения `throw()`, и тело лямбда\-выражения вызывает исключение, как показано ниже:  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() throw() { throw 5; }();  
}  
```  
  
 Дополнительные сведения см. в разделе [Спецификации исключений \(throw\)](../cpp/exception-specifications-throw-cpp.md).  
  
### Тип возвращаемого значения  
 Возвращаемый тип лямбда\-выражения выводится автоматически.  Использовать ключевое слово [auto](../cpp/auto-cpp.md) не нужно, если не указывается *завершающий возвращающий тип*.  *trailing\-return\-type* похож на часть стандартного метода или функции, содержащую возвращаемый тип.  Однако тип возвращаемого значения следует списку параметров, и необходимо включить ключевое слово `->` элемента trailing\-return\-type перед типом возвращаемого значения.  
  
 Можно опустить часть возвращаемого типа лямбда\-выражения, если тело лямбда\-выражения содержит только один оператор return или лямбда\-выражение не возвращает значение.  Если тело лямбда\-выражения содержит один оператор return, компилятор выводит тип возвращаемого значения из типа возвращаемого выражения.  В противном случае компилятор выводит следующий тип возвращаемого значения: `void`.  Рассмотрим следующие примеры кода, иллюстрирующие этот принцип.  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
  
```  
  
 Лямбда\-выражение может создавать другое лямбда\-выражение в качестве своего возвращаемого значения.  Дополнительные сведения см. в разделе [Примеры лямбда\-выражений](../cpp/examples-of-lambda-expressions.md) \(подраздел "Лямбда\-выражения высшего порядка"\).  
  
### Тело лямбда\-выражения  
 Часть лямбда\-выражения, содержащая его тело \(*compound\-statement* в синтаксисе стандарта\), может содержать те же элементы, что и тело обычного метода или функции.  Тело обычной функции и лямбда\-выражения может осуществлять доступ к следующим типам переменных:  
  
-   Фиксированные переменные из внешней области видимости \(см. выше\).  
  
-   Параметры  
  
-   Локально объявленные переменные  
  
-   Данные\-члены класса \(при объявлении внутри класса и фиксации `this`\)  
  
-   Любая переменная, которая имеет статическую длительность хранения \(например, глобальная переменная\)  
  
 В следующем примере содержится лямбда\-выражение, которое явно фиксирует переменную `n` по значению и неявно фиксирует переменную `m` по ссылке.  
  
```cpp  
// captures_lambda_expression.cpp  
// compile with: /W4 /EHsc   
#include <iostream>  
using namespace std;  
  
int main()  
{  
   int m = 0;  
   int n = 0;  
   [&, n] (int a) mutable { m = ++n + a; }(4);  
   cout << m << endl << n << endl;  
}  
```  
  
 **Результат:**  
  
  **5**  
**0** Поскольку переменная `n` фиксируется по значению, ее значение после вызова лямбда\-выражения остается равным `0`.  Спецификация `mutable` позволяет изменять `n` внутри лямбда\-выражения.  
  
 Несмотря на то что лямбда\-выражение может фиксировать только переменные с автоматической длительностью хранения, в теле лямбда\-выражения можно использовать переменные, которые имеют статическую длительность хранения.  В следующем примере функция `generate` и лямбда\-выражение используются для присвоения значения каждому элементу объекта `vector`.  Лямбда\-выражение изменяет статическую переменную для получения значения следующего элемента.  
  
```cpp  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });   
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
```  
  
 Дополнительные сведения см. разделе [создание](../Topic/generate.md).  
  
 В следующем примере кода используется функция из предыдущего примера и добавляется пример лямбда\-выражения с алгоритмом STL `generate_n`.  Это лямбда\-выражение назначает элемент объекта `vector` сумме предыдущих двух элементов.  Ключевое слово `mutable` используется, чтобы тело лямбда\-выражения могло изменять соответствующие копии внешних переменных `x` и `y`, захваченные лямбда\-выражением по значению.  Поскольку лямбда\-выражение захватывает исходные переменные `x` и `y` по значению, их значения остаются равными `1` после выполнения лямбда\-выражения.  
  
```cpp  
// compile with: /W4 /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });  
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
  
int main()  
{  
    // The number of elements in the vector.  
    const int elementCount = 9;  
  
    // Create a vector object with each element set to 1.  
    vector<int> v(elementCount, 1);  
  
    // These variables hold the previous two elements of the vector.  
    int x = 1;  
    int y = 1;  
  
    // Sets each element in the vector to the sum of the   
    // previous two elements.  
    generate_n(v.begin() + 2,  
        elementCount - 2,  
        [=]() mutable throw() -> int { // lambda is the 3rd parameter  
        // Generate current value.  
        int n = x + y;  
        // Update previous two values.  
        x = y;  
        y = n;  
        return n;  
    });  
    print("vector v after call to generate_n() with lambda: ", v);  
  
    // Print the local variables x and y.  
    // The values of x and y hold their initial values because   
    // they are captured by value.  
    cout << "x: " << x << " y: " << y << endl;  
  
    // Fill the vector with a sequence of numbers  
    fillVector(v);  
    print("vector v after 1st call to fillVector(): ", v);  
    // Fill the vector with the next sequence of numbers  
    fillVector(v);  
    print("vector v after 2nd call to fillVector(): ", v);  
}  
  
```  
  
 **Результат:**  
  
  **vector v after call to generate\_n\(\) with lambda: 1 1 2 3 5 8 13 21 34**  
**x: 1 y: 1**  
**vector v after 1st call to fillVector\(\): 1 2 3 4 5 6 7 8 9**  
**vector v after 2nd call to fillVector\(\): 10 11 12 13 14 15 16 17 18** Дополнительные сведения см. в разделе [generate\_n](../Topic/generate_n.md).  
  
## Только для систем Майкрософт  
 Лямбда\-выражения не поддерживаются в следующих управляемых сущностях среды CLR: `ref class`, `ref struct`, `value class` и `value struct`.  
  
 Если вы используете модификаторы, характерные для систем Майкрософт, такие как [\_\_declspec](../cpp/declspec.md), их можно вставить в лямбда\-выражение сразу после `parameter-declaration-clause`, например:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
  
```  
  
 Сведения о том, как определить, поддерживается ли модификатор лямбда\-выражениями, см. в соответствующей статье в разделе [Модификаторы, используемые в системах Майкрософт](../Topic/Microsoft-Specific%20Modifiers.md) данного документа.  
  
 Visual Studio поддерживает синтаксис и функции лямбда\-выражений стандарта C\+\+11 со следующими исключениями:  
  
-   Как и все другие классы, лямбда\-выражения не получают автоматически созданные конструкторы перемещения и операторы присваивания с перемещением.  Дополнительные сведения о поддержке ссылок rvalue см. в разделе [Поддержка возможностей C\+\+ 11\/14\/17](../Topic/Support%20For%20C++11-14-17%20Features%20\(Modern%20C++\).md) \(подраздел "Ссылки rvalue"\).  
  
-   Необязательный параметр *attribute\-specifier\-seq* не поддерживается в этой версии.  
  
 Visual Studio включает следующие функции в дополнение к функциям лямбда\-выражений стандарта C\+\+11:  
  
-   Не имеющие состояний лямбда\-выражения являются универсально преобразуемыми в указатели функций с произвольными соглашениями о вызовах.  
  
-   Автоматически выведенные возвращаемые типы для тела лямбда\-выражений, которые сложнее, чем `{ return expression; }`, при условии, что все возвращаемые выражения относятся к одному типу.  \(Эта функция является частью предложенного стандарта C\+\+14.\)  
  
## См. также  
 [Справочник по языку C\+\+](../cpp/cpp-language-reference.md)   
 [Объекты функций в библиотеке STL](../standard-library/function-objects-in-the-stl.md)   
 [Вызов функции](../Topic/Function%20Call%20\(C++\).md)   
 [for\_each](../Topic/for_each.md)