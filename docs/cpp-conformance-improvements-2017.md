---
title: "Улучшения соответствия компилятора C++ | Документы Майкрософт"
ms.custom: 
ms.date: 08/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3bd6838166a5471190e4c19c1a5f356901551dbb
ms.contentlocale: ru-ru
ms.lasthandoff: 10/09/2017

---
   
# <a name="c-conformance-improvements-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Улучшения соответствия C++ в [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]

## <a name="new-language-features"></a>Новые возможности языка  
Благодаря поддержке обобщенного constexpr и NSDMI для статистических выражений теперь компилятор готов к использованию функций, добавленных в стандарте C++14. Обратите внимание, что в компиляторе по-прежнему отсутствует несколько функций из стандартов C++11 и C++98. Сведения о текущем состоянии компилятора см. в статье [Соответствие стандартам языка Visual C++](visual-cpp-language-conformance.md).

### <a name="c11"></a>C++11
**Поддержка выражения SFINAE в дополнительных библиотеках**. В компиляторе Visual C++ улучшена поддержка выражения SFINAE, которое необходимо для вычета аргумента шаблона и подстановки, где выражения decltype и constexpr могут отображаться в виде параметров шаблона. Дополнительные сведения см. в разделе [Усовершенствования выражения SFINAE в версии-кандидате Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3). 


### <a name="c-14"></a>C++ 14
**NSDMI для статистических выражений**. Статистическое выражение является массивом или классом без предоставленного пользователем конструктора, без закрытых или защищенных нестатических данных-членов, без базовых классов и виртуальных функций. Начиная с версии C++14, статистические выражения могут содержать инициализаторы членов. Дополнительные сведения см. в разделе [Инициализаторы членов и статистические выражения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

**Расширенный constexpr**. Выражения, объявленные как constexpr, теперь могут содержать определенные виды объявлений, операторы if и switch, операторы циклов и изменения объектов, время жизни которых началось в вычислении выражения constexpr. Кроме того, больше не требуется, чтобы нестатическая функция-член была явной константой. Дополнительные сведения см. в статье [Нестрогие ограничения для функций constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html). 

### <a name="c17"></a>C++17
**Сжатый static_assert** (доступен с /std:c++latest). В C++17 параметр сообщения для static_assert является необязательным. Дополнительные сведения см. в разделе [Расширение static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf). 

**атрибут [[fallthrough]]** (доступен с /std:c++latest) Атрибут [[fallthrough]] можно использовать в контексте операторов switch как подсказку для компилятора о том, что требуется поведение проваливания. Это позволит избежать вывода предупреждений компилятора. Дополнительные сведения см. в разделе [Формулировка для атрибута [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf). 

**Обобщенные циклы for на основе диапазона** (параметр компилятора не требуется). Для циклов for на основе диапазона больше не требуется, чтобы функции begin() и end() возвращали объекты одного типа. Это позволяет функции end() возвращать объект sentinel, используемый, например, диапазонами, как определено в предложении Ranges-V3. Дополнительные сведения см. в разделе [Обобщение цикла For на основе диапазона](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) и в документе о [библиотеке range-v3 на сайте GitHub](https://github.com/ericniebler/range-v3). 

**Visual Studio 2017 версия 15.3**:

**Лямбда-выражения constexpr** Лямбда-выражения теперь можно использоваться в константных выражениях. Дополнительные сведения см. в документе о [лямбда-выражениях](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

**Инструкция if constexpr в шаблонах функций** Шаблон функции может содержать инструкции `if constexpr` для включения ветвления во время компиляции. Дополнительные сведения см. в документе об [if constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

**Инструкции выбора с инициализаторами** Инструкция `if` может включать инициализатор, представляющий переменную в области блока в самой инструкции. Дополнительные сведения см. в документе об [инструкциях выбора с инициализатором](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

**Атрибуты [[maybe_unused]] и [[nodiscard]]** Новые атрибуты для отключения предупреждения, когда сущность не используется, или для их создания, если возвращаемое значение вызова функции удаляется. Дополнительные сведения см. в документах о [формулировке для атрибута maybe_unused](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) и [предложении атрибутов unused,nodiscard и fallthrough](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

**Использование пространств имен атрибута без повторения** Новый синтаксис позволяет включить только один идентификатор пространства имен в списке атрибутов. Дополнительные сведения см. в статье [Attributes in C++](cpp/attributes2.md) (Атрибуты в C++).

**Структурированная привязка** Теперь в одном объявлении можно хранить значения с именами отдельных компонентов, когда значение представлено массивом, std::tuple или std::pair, либо содержит все открытые нестатические элементы данных. Дополнительные сведения см. в документе по [структурированным привязкам](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

**Правила конструкции для значений класса enum** Теперь существует способ неявного и не ограничивающего преобразования базового типа ограниченного перечисления в само перечисление, если в его определении нет перечислителя, а в источнике используется синтаксис инициализации списка. Дополнительные сведения см. в документе о [правилах конструкции значений класса enum](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

**Захват объекта *this по значению** Объект \*this в лямбда-выражении теперь можно захватывать по значению. Так появляется возможность реализации сценариев, в которых лямбда вызывается в параллельных асинхронных операциях, особенно на компьютерах с новой архитектурой. Дополнительные сведения см. в документе о [захвате объекта \*this по значению в виде [=,\*this] в лямбда-выражении](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

**Удаление operator ++ для типа bool** operator ++ больше не поддерживается для типов `bool`. Дополнительные сведения см. в документе об [удалении устаревшего объекта operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

**Удаление нерекомендуемого ключевого слова register** Ключевое слово `register` Ключевое слово, ранее признанное устаревшим (и игнорируемое в компиляторе Visual C++), удалено из языка. Дополнительные сведения см. в документе об [удалении нерекомендуемого ключевого слова register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Полный список улучшений соответствия вплоть до Visual Studio 2015 с обновлением 3 см. в разделе [Новые возможности Visual C++ 2003–2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx).

## <a name="bug-fixes"></a>Исправления ошибок
### <a name="copy-list-initialization"></a>Инициализация копии списка
Visual Studio 2017 правильно вызывает ошибки компилятора, связанные с созданием объектов с использованием списков инициализаторов, которые не обнаруживались в Visual Studio 2015 и могли приводить к сбоям или неопределенному поведению во время выполнения. Согласно N4594 13.3.1.7p1 в инициализации копии списка компилятор должен учитывать явный конструктор для разрешения перегрузки, но должен выдавать ошибку, если эта перегрузка выбирается на самом деле. 

Следующие два примера кода компилируются в Visual Studio 2015, но не в Visual Studio 2017.
```cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```
Чтобы исправить эту ошибку, следует использовать прямую инициализацию:
```cpp  
A a1{ 1 };
const A& a2{ 1 };
```

В Visual Studio 2015 компилятор ошибочно интерпретировал инициализацию копии списка так же, как обычную инициализацию копии. Он рассматривал только преобразование конструкторов для разрешения перегрузки. В следующем примере Visual Studio 2015 выбирает MyInt(23), но Visual Studio 2017 правильно выводит ошибку. 

```cpp  
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
       explicit MyStore(int initialCapacity);
};

struct MyInt {
       MyInt(int i);
};

struct Printer {
       void operator()(MyStore const& s);
       void operator()(MyInt const& i);
};

void f() {
       Printer p;
       p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Этот пример аналогичен предыдущему, но выводит другую ошибку. Он выполняется успешно в Visual Studio 2015, а в Visual Studio 2017 с C2668 завершается ошибкой. 

```cpp  
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Нерекомендуемые определения типов
Теперь Visual Studio 2017 выдает правильное предупреждение для нерекомендуемых определений типов, объявленных в классе или структуре. В следующем примере показана компиляция без предупреждений в Visual Studio 2015, но в Visual Studio 2017 выводится предупреждение C4996.

```cpp  
struct A 
{
    // also for __declspec(deprecated) 
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr
Visual Studio 2017 правильно выдает ошибку, если левый операнд в операции условного вычисления является недопустимым в контексте constexpr. Следующий код компилируется в Visual Studio 2015, но не в Visual Studio 2017 (ошибка C3615: функция «f» с квалификатором constexpr не может выдавать константное выражение):

```cpp  
template<int N>
struct array 
{
       int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
       return arr.size() == 10 || arr.size() == 11; // C3615    
}
```
Чтобы исправить эту ошибку, объявите функцию array::size() как constexpr или удалите квалификатор constexpr из f. 

### <a name="class-types-passed-to-variadic-functions"></a>Типы классов, передаваемые в функции с переменным числом аргументов
В Visual Studio 2017 классы и структуры, передаваемые в функцию с переменным числом аргументов, например printf, должны быть доступны для простого копирования. При передаче таких объектов компилятор просто выполняет побитовое копирование и не вызывает конструктор или деструктор. 

```cpp  
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called; 
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```
Чтобы исправить эту ошибку, можно вызвать функцию-член, возвращающую тип, доступный для простого копирования, 

```cpp  
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```
или выполнить статическое приведение для преобразования объекта перед его передачей:
```cpp  
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```
Для строк, созданных и управляемых с помощью CStringW, следует использовать предоставленный `operator LPCWSTR()` для приведения объекта CStringW к указателю C, ожидаемому строкой формата.

```cpp  
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>CV-квалификаторы при построении класса
В Visual Studio 2015 компилятор иногда ошибочно игнорирует cv-квалификатор при создании объекта класса путем вызова конструктора. Это может привести к сбою или непредсказуемому поведению среды выполнения. Следующий пример компилируется в Visual Studio 2015, но вызывает ошибку компилятора в Visual Studio 2017:

```cpp  
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```
Чтобы исправить эту ошибку, объявите оператор int() как константу. 

### <a name="access-checking-on-qualified-names-in-templates"></a>Проверка доступа к полным именам в шаблонах
В предыдущих версиях компилятора проверка доступа к полным именам в некоторых контекстах шаблонов не выполнялась. Это может помешать ожидаемой работе SFINAE там, где подстановка должна завершиться ошибкой из-за отсутствия доступа к имени. Такая ситуация может приводить к сбою или неожиданному поведению во время выполнения из-за того, что компилятор неправильно вызывает неверную перегрузку оператора. В Visual Studio 2017 выводится ошибка компилятора. Ошибки могут различаться, но, как правило, это ошибка C2672: "Совпадающая перегруженная функция не найдена". Следующий код компилируется в Visual Studio 2015, но выводит ошибку в Visual Studio 2017:

```cpp  
#include <type_traits>

template <class T> class S {
       typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
       f(10); // C2672: No matching overloaded function found. 
}
```

### <a name="missing-template-argument-lists"></a>Отсутствующие списки аргументов шаблона
В Visual Studio 2015 и более ранних версиях компилятор не диагностировал отсутствующие списки аргументов шаблона при отображении шаблона в списке параметров шаблона (например, в составе аргумента шаблона по умолчанию или как параметр шаблона, не являющийся типом). Это может привести к непредсказуемому поведению, включая сбои компилятора или непредсказуемое поведение среды выполнения. Следующий код компилируется в Visual Studio 2015, но выводит ошибку в Visual Studio 2017.

```cpp  
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;  
```

### <a name="expression-sfinae"></a>Выражение SFINAE
Для поддержки выражения SFINAE компилятор теперь анализирует аргументы decltype при объявлении, а не создании шаблонов. Соответственно, независимая специализация, обнаруженная в аргументе decltype, не откладывается до момента создания и немедленно обрабатывается. Кроме того, в это время выявляются все возникающие ошибки.  

В следующем примере показана такая ошибка компилятора, возникающая во время объявления.

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
       struct BadType {};
       template <class U>
       static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
       template <class U>
       static BadType Test(...);
       static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```
### <a name="classes-declared-in-anonymous-namespaces"></a>Классы, объявляемые в анонимных пространствах имен
Согласно стандарту C++ класс, объявленный внутри анонимного пространства имен, имеет внутреннюю компоновку и не может быть экспортирован. В Visual Studio 2015 и более ранних версиях это правило не применялось. В Visual Studio 2017 это правило применяется частично. Приведенный ниже пример кода вызывает в Visual Studio 2017 такую ошибку: "Ошибка C2201: const anonymous в пространстве имен ::S1::vftable: требуется внешняя ссылка для экспорта или импорта".

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Инициализаторы по умолчанию для членов класса значения (C++/CLI)
В Visual Studio 2015 и более ранних версиях компилятор допускал (но игнорировал) инициализатор членов по умолчанию для члена класса значений. Инициализатор по умолчанию для класса значений всегда инициализирует члены нулевым значением. Конструктор по умолчанию не допускается. В Visual Studio 2017 инициализаторы членов по умолчанию вызывают ошибку компилятора, как показано в следующем примере:

```cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Индексаторы по умолчанию (C++/CLI)
В Visual Studio 2015 и более ранних версиях в некоторых случаях компилятор неправильно определял свойство по умолчанию как индексатор по умолчанию. Эту проблему удалось решить с использованием значения по умолчанию идентификатора для доступа к свойству. Возможное решение само по себе стало создавать проблемы после того, как значение умолчанию было представлено как ключевое слово в C++ 11. Поэтому в Visual Studio 2017 были исправлены ошибки, требующие обходного решения. Теперь компилятор выдает ошибку, когда значение по умолчанию используется для доступа к свойству по умолчанию для класса.

```cpp  
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

 
// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

В Visual Studio 2017 оба свойства значения доступны по их именам:

```cpp  
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Исправления ошибок в Visual Studio 2017 версии 15.3
### <a name="calls-to-deleted-member-templates"></a>Вызовы шаблонов удаленного элемента
В предыдущих версиях Visual Studio компилятор в некоторых случаях не сообщал об ошибках при некорректных вызовах шаблона удаленного элемента, которые могли стать причиной сбоев в среде выполнения. Теперь для приведенного ниже кода возвращается ошибка C2280, "'int S<int>:: f<int>(void)': попытка ссылки на удаленную функцию":
```cpp
template<typename T> 
struct S { 
   template<typename U> static int f() = delete; 
}; 
 
void g() 
{ 
   decltype(S<int>::f<int>()) i; // this should fail 
}
```
Чтобы устранить эту ошибку, объявите элемент "i" как `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Проверки предварительных условий для признаков типов
В Visual Studio 2017 версии 15.3 улучшены проверки предварительных условий для признаков типов на более строгое следование стандарту. Одна из проверок проверяет присвоение. Для следующего кода создается ошибка C2139 в обновлении версии 15.3:

```cpp
struct S; 
enum E; 
 
static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Новое предупреждение компилятора и проверки среды выполнения для маршалинга между собственными и управляемыми функциями
Вызов собственных функций из управляемых функций требует маршалинга. Среда CLR выполняет такой маршалинг, но не понимает семантики C++. Если вы передадите собственный объект по значению, CLR вызовет конструктор копий объекта или применит функцию BitBlt, что может привести к неопределенному поведению во время выполнения. 
 
Теперь компилятор выдает предупреждение, если во время компиляции у него есть информация о том, что собственный объект с удаленным конструктором копий передается по значению через границу собственных и управляемых функций. В тех случаях, когда компилятор во время компиляции не имеет такой информации, он внедряет проверку времени выполнения, чтобы программа немедленно вызвала std::terminate при проявлении некорректного маршалинга. В обновлении версии 15.3 для следующего кода будет создана ошибка C4606 "'A': для передачи аргумента по значению через границы собственного и управляемого требуется действительный конструктор копии. В противном случае поведение в среде выполнения будет неопределенным".
```cpp
class A 
{ 
public: 
   A() : p_(new int) {} 
   ~A() { delete p_; } 
 
   A(A const &) = delete; 
   A(A &&rhs) { 
   p_ = rhs.p_; 
} 
 
private: 
   int *p_; 
}; 
 
#pragma unmanaged 
 
void f(A a) 
{ 
} 
 
#pragma managed 
 
int main() 
{ 
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which will result in a double-free later. 
}
```
Чтобы устранить такую ошибку, удалите директиву `#pragma managed`, чтобы вызывающая функция стала собственной. Это позволит избежать маршалинга. 

### <a name="experimental-api-warning-for-winrt"></a>Экспериментальные предупреждения API для WinRT
API-интерфейсы WinRT, выпускаемые для экспериментов и обратной связи, будут обозначаться атрибутом `Windows.Foundation.Metadata.ExperimentalAttribute`. В Visual Studio 2017 версии 15.3 компилятор выдает предупреждение C4698 при обнаружении этого атрибута. Несколько интерфейсов API в предыдущих версиях Windows SDK уже помечены этим атрибутом, следовательно вызов таких интерфейсов API приведет к появлению указанного предупреждения компилятора. В новых Windows SDK атрибут будет удален из всех поставляемых типов, но если вы используете старые версии SDK, эти предупреждения нужно скрыть для всех вызовов поставляемых типов.
Для следующего кода создается предупреждение C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' предоставляется только для ознакомительных целей и подлежит изменению или удалению в будущих обновлениях":
```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() //C4698
```

Чтобы отключить это предупреждение, добавьте атрибут #pragma.

```cpp
#pragma warning(push) 
#pragma warning(disable:4698) 
 
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() 
 
#pragma warning(pop)
```
### <a name="out-of-line-definition-of-a-template-member-function"></a>Определение функции-члена шаблона вне строки 
Visual Studio 2017 версии 15.3 выводит сообщение об ошибке, если встречает вне строки определения функции элемента шаблона, не объявленной в классе. Для следующего кода создается ошибка C2039: элемент 'f': не является членом элемента 'S':

```cpp
struct S {}; 
 
template <typename T> 
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Чтобы исправить такую ошибку, добавьте в класс следующее объявление:

```cpp
struct S { 
    template <typename T> 
    void f(T t); 
}; 
template <typename T> 
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Попытка получить адрес указателя "this"
В C++ указатель "this" является значением prvalue с типом указателя для X. Невозможно получить адрес "this" или привязать его к ссылке lvalue. В предыдущих версиях Visual Studio компилятор позволял обойти это ограничение, выполнив приведение. В Visual Studio 2017 версии 15.3 компилятор выдает ошибку C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Преобразование в недоступный базовый класс
Visual Studio 2017 версии 15.3 выводит сообщение об ошибке при попытке преобразовать тип в недоступный базовый класс. В компиляторе появляется "ошибка C2243: "приведение типа": преобразование из "D *" в "B *" существует, но является недоступным". Следующий код является некорректным и может привести к сбою в среде выполнения. Теперь компилятор создает ошибку C2243 для такого кода:

```cpp
#include <memory> 
 
class B { }; 
class D : B { }; // C2243. should be public B { }; 
 
void f() 
{ 
   std::unique_ptr<B>(new D()); 
}
```
### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>Аргументы по умолчанию не допускаются в определениях функций-членов вне строки
Аргументы по умолчанию запрещено использовать в определениях вне строки функций элементов в классах шаблонов. Компилятор выдаст предупреждение в каталоге /permissive и критическую ошибку в /permissive-. 

В предыдущих версиях Visual Studio следующий некорректный код может вызвать сбой среды выполнения. В Visual Studio 2017 версии 15.3 выводится предупреждение C5034: "A<T>:: f": определение вне строки для элемента шаблона класса не может иметь аргументы по умолчанию:
```cpp
 
template <typename T> 
struct A { 
    T f(T t, bool b = false); 
}; 
 
template <typename T> 
T A<T>::f(T t, bool b = false) // C5034
{ 
... 
}
```
Чтобы устранить такую ошибку, удалите аргумент по умолчанию "= false". 

### <a name="use-of-offsetof-with-compound-member-designator"></a>Использование offsetof с обозначением составного члена
В Visual Studio 2017 версии 15.3 используется offsetof (T, m), где m является обозначением составного члена, создает предупреждение при компиляции с параметром /Wall. Следующий код является некорректным и может привести к сбою во время выполнения. Visual Studio 2017 версии 15.3 выдает "предупреждение C4841: использовано нестандартное расширение: обозначение составного элемента в offsetof":

```cpp
  
struct A { 
int arr[10]; 
}; 
 
// warning C4841: non-standard extension used: compound member designator in offsetof 
constexpr auto off = offsetof(A, arr[2]);
```
Чтобы исправить этот код, можно отключить предупреждение с помощью директивы pragma или убрать из кода использование offsetof: 

```cpp
#pragma warning(push) 
#pragma warning(disable: 4841) 
constexpr auto off = offsetof(A, arr[2]); 
#pragma warning(pop) 
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Использование offsetof со статическими данными-членом или функцией-членом
В Visual Studio 2017 версии 15.3 при использовании offsetof (T, m), где m ссылается на статические данные или функции элемента, возникает ошибка. Для следующего примера кода создается "ошибка C4597: неопределенное поведение: offsetof применяется к функции-члену 'foo'" и "ошибка C4597: неопределенное поведение: offsetof применяется к данным-члену 'bar'" :
```cpp
 
#include <cstddef> 
 
struct A { 
int foo() { return 10; } 
static constexpr int bar = 0; 
}; 
 
constexpr auto off = offsetof(A, foo); 
Constexpr auto off2 = offsetof(A, bar);
```
 
Этот код является некорректным и может привести к сбою во время выполнения. Чтобы устранить такую ошибку, измените код так, чтобы он не создавал неопределенное поведение. Это код не является переносимым и запрещен стандартом C++.

### <a name="new-warning-on-declspec-attributes"></a>Новое предупреждение для атрибутов declspec
В Visual Studio 2017 версии 15.3 компилятор больше не игнорирует атрибуты, "if __declspec(...)" применяется до указания компоновки extern "C". Ранее компилятор игнорировал такой атрибут, что могло повлиять на поведение во время выполнения. Если установлен параметр `/Wall /WX`, для следующего кода создается "предупреждение C4768: атрибуты __declspec перед указанием компоновки игнорируются":

```cpp
 
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Чтобы устранить это предупреждение, переместите extern "C" вперед:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
Это предупреждение по умолчанию отключено и влияет только на код, скомпилированный с `/Wall /WX`.

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype и вызовы удаленных деструкторов
В предыдущих версиях Visual Studio компилятор не отслеживал возникновение вызовов удаленных деструкторов в контексте выражений, связанных с "decltype". В Visual Studio 2017 версии 15.3 для приведенного ниже кода появляется ошибка C2280, "'A<T>::~A(void)': попытка ссылки на удаленную функцию":

```cpp
template<typename T> 
struct A 
{ 
   ~A() = delete; 
}; 
 
template<typename T> 
auto f() -> A<T>; 
 
template<typename T> 
auto g(T) -> decltype((f<T>())); 
 
void h() 
{ 
   g(42); 
}
```
### <a name="uninitialized-const-variables"></a>Неинициализированные переменные const
В выпуске Visual Studio 2017 RTW была допущена регрессия, из-за которой компилятор C++ не выдавал диагностических сообщений о том, что переменная "const" не инициализирована. Эта регрессия была устранена в Visual Studio 2017 версии 15.3. Для следующего примера кода теперь выдается "предупреждение C4132: 'Значение': объект const необходимо инициализировать":

```cpp
const int Value; //C4132
```
Чтобы исправить эту ошибку, присвойте значение переменной `Value`.

### <a name="empty-declarations"></a>Пустые объявления
Теперь Visual Studio 2017 версии 15.3 предупреждает о пустых объявлениях для всех типов, а не только для встроенных. Теперь для следующего кода создаются предупреждения C4091 уровня 2 для всех четырех объявлений:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };
 
int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Чтобы устранить эти предупреждения, закомментируйте или удалите все пустые объявления. В случаях, когда объекты без имен созданы специально для побочных эффектов (например, RAII), им следует присвоить имена.
 
Это предупреждение отключено при использовании /Wv:18 и включено по умолчанию на уровне предупреждений W2.


### <a name="stdisconvertible-for-array-types"></a>std::is_convertible для типов массива
В предыдущих версиях компилятора класс [std::is_convertible](standard-library/is-convertible-class.md) выдавал неверные результаты для типов массива. Из-за этого разработчикам библиотек необходимо было особым образом обрабатывать в компиляторе Visual C++ признаки типа `std::is_convertible<…>`. В следующем примере статические функции assert успешно срабатывают в предыдущих версиях Visual Studio, но в Visual Studio 2017 версии 15.3 завершаются ошибкой:

```cpp
#include <type_traits>
 
using Array = char[1];
 
static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

**std::is_convertible<From, To>** проверяет, правильно ли сформировано определение произвольной функции:
```cpp 
   To test() { return std::declval<From>(); }
``` 

### <a name="private-destructors-and-stdisconstructible"></a>Закрытые деструкторы и std::is_constructible
Предыдущие версии компилятора не проверяли, является ли деструктор закрытым, при получении результата [std::is_constructible](standard-library/is-constructible-class.md). Теперь это принимается во внимание. В следующем примере статические функции assert успешно срабатывают в предыдущих версиях Visual Studio, но в Visual Studio 2017 версии 15.3 завершаются ошибкой:

```cpp
#include <type_traits>
 
class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};
 
// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```  

Закрытые деструкторы могут сделать тип неконструируемым. При вычислении **std::is_constructible<T, Args...>** подразумевается следующее объявление.
```cpp 
   T obj(std::declval<Args>()…)
``` 
Этот вызов подразумевает вызов деструктора.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: неоднозначное разрешение перегрузки
Предыдущим версиям компилятора иногда не удавалось обнаружить неоднозначность, когда при использовании объявлений и при поиске функций по аргументам выявлялись различные кандидаты. Это может привести к некорректному выбору перегрузки и непредсказуемому поведению в среде выполнения. В следующем примере Visual Studio 2017 версии 15.3 корректно выдает ошибку C2668, неоднозначный вызов перегруженной функции "f":

```cpp
namespace N {
   template<class T>
   void f(T&, T&);
 
   template<class T>
   void f();
}
 
template<class T>
void f(T&, T&);
 
struct S {};
void f()
{
   using N::f; 
 
   S s1, s2;
   f(s1, s2); // C2668
}
```
Чтобы исправить код, удалите оператор «using N::f», если вы намереваетесь вызвать «::f()».

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: локальные объявления функций и проверка по аргументам
При локальном объявлении функции скрываются внутри области, поэтому поиск по аргументам не осуществляется.
Но предыдущие версии компилятора Visual C++ в этом случае выполняли поиск функции по аргументам, что могло привести к некорректному выбору перегрузки и непредсказуемому поведению в среде выполнения. Как правило, ошибка возникает из-за неправильной сигнатуры в локальном объявлении функции. В следующем примере Visual Studio 2017 версии 15.3 корректно выдает ошибку C2660, функция "f" не принимает 2 аргумента.

```cpp
struct S {}; 
void f(S, int);
 
void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Чтобы устранить эту проблему, либо измените сигнатуру **f(S)**, либо удалите ее.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: порядок инициализации в списках инициализатора
Члены класса инициализируются в порядке их объявления, а не порядке их отображения в списках инициализаторов. В предыдущих версиях компилятора, когда порядок списка инициализаторов отличался от порядка объявления, никакого предупреждения не выводилось. Это могло приводить к неопределенному поведению во время выполнения, если инициализация одного члена зависела от другого уже инициализированного члена в списке. В следующем примере Visual Studio 2017 версии 15.3 (с /Wall) выдает предупреждение C5038: элемент данных «A::y» будет инициализирован после элемента данных «A::x»:

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};

```
Чтобы устранить проблему, список инициализатора должен иметь тот же порядок, что и объявления. Похожее предупреждение возникает, когда один инициализатор или оба ссылаются на члены базового класса.

Обратите внимание, что это предупреждение по умолчанию отключено и относится только к коду, скомпилированному с /Wall.

## <a name="see-also"></a>См. также  
[Соответствие стандартам языка Visual C++](visual-cpp-language-conformance.md)  
