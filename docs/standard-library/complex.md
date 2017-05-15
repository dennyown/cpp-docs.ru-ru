---
title: "&lt;complex&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <complex>
- std.<complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 02d651b3e3ca4dc643b01463a85762a6427b8e83
ms.contentlocale: ru-ru
ms.lasthandoff: 04/29/2017

---
# <a name="ltcomplexgt"></a>&lt;complex&gt;
Определяет класс шаблонов контейнеров **сложных** и его вспомогательные шаблоны.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#include <complex>  
```  
  
## <a name="remarks"></a>Примечания  
 Комплексные числа — это упорядоченная пара вещественных чисел. С геометрической точки зрения комплексная плоскость — это вещественная двумерная плоскость. Отличия комплексной плоскости от вещественной состоят в том, что у нее есть дополнительная алгебраическая структура. У этой структуры есть две основные операции.  
  
-   Addition defined as (*a*, *b*) + (*c*, *d*) = (*a* + *c*, *b* + *d*)  
  
-   Multiplication defined as (*a*, *b*) \* (*c*, *d*) = (*ac* - *bd*, *ad* + *bc*)  
  
 Набор комплексных чисел с операциями комплексного сложения и комплексного умножения — это поле с точки зрения стандартной алгебры:  
  
-   Операции сложения и умножения коммутативны и ассоциативны, а умножение распределяется над сложением точно так же, как для вещественного сложения и умножения в поле вещественных чисел.  
  
-   Комплексное число (0, 0) имеет аддитивный идентификатор и (1, 0) — мультипликативный идентификатор.  
  
-   Аддитивная Инверсия комплексного числа (**, *b*) — (-**, -*b*), а мультипликативная Инверсия для всех таких комплексных чисел, за исключением (0, 0) —  
  
     (*a*/(*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/(*a*<sup>2</sup> + *b*<sup>2</sup>))  
  
 Представляя комплексное число *z* = (**, *b*) в виде *z* = ** + *bi*, где *я*<sup>2</sup> = -1, правила алгебры набора вещественных чисел могут применяться к набору комплексных чисел и их компонентам. Пример:  
  
  (1 + 2*i*) \* (2 + 3*i*)  
  = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*)  
  = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
  = (2 - 6) + (3 + 4)*i*  
  = -4 + 7*i*  
  
 Система комплексных чисел — это поле, но оно не упорядоченное. Нет, не порядок комплексных чисел как поле вещественных чисел и их подмножеств, поэтому отношение неравенства не может применяться к комплексные числа, как они вещественных чисел.  
  
 Существует три общие формы представления комплексного числа *z*:  
  
-   Cartesian: *z* = *a* + *bi*  
  
-   Polar: *z* = *r* (cos *p* + *i* sin *p*)  
  
-   Exponential: *z* = *r* \* *e*<sup>*ip*</sup>  
  
 В этих стандартных представлениях комплексных чисел используются следующие термины.  
  
-   Вещественный компонент арифметического представления или действительная часть *a*.  
  
-   Мнимый компонент арифметического представления или мнимая часть *b*.  
  
-   Модуль или абсолютное значение комплексного числа *r*.  
  
-   Аргумент или угол фазы *p* в радианах.  
  
 Если не указано иное, функции, которые могут возвращать несколько значений, должны возвращать основное значение для их аргументов больше - π и меньше чем или равно + π, чтобы обеспечить одно значение. Все углы должны выражаться в радианах, где в круге 2π радиан (360 градусов).  
  
### <a name="functions"></a>Функции  
  
|||  
|-|-|  
|[abs](../standard-library/complex-functions.md#abs)|Вычисляет модуль комплексного числа.|  
|[arg](../standard-library/complex-functions.md#arg)|Извлекает аргумент из комплексного числа.|  
|[conj](../standard-library/complex-functions.md#conj)|Возвращает комплексно-сопряженную величину комплексного числа.|  
|[cos](../standard-library/complex-functions.md#cos)|Возвращает косинус комплексного числа.|  
|[cosh](../standard-library/complex-functions.md#cosh)|Возвращает гиперболический косинус комплексного числа.|  
|[exp](../standard-library/complex-functions.md#exp)|Возвращает экспоненциальную функцию комплексного числа.|  
|[imag](../standard-library/complex-functions.md#imag)|Извлекает мнимую часть комплексного числа.|  
|[log](../standard-library/complex-functions.md#log)|Возвращает натуральный логарифм комплексного числа.|  
|[log10](../standard-library/complex-functions.md#log10)|Возвращает десятичный логарифм комплексного числа.|  
|[norm](../standard-library/complex-functions.md#norm)|Извлекает норму комплексного числа.|  
|[polar](../standard-library/complex-functions.md#polar)|Возвращает комплексное число, соответствующее указанному модулю и аргументу, в декартовой форме.|  
|[pow](../standard-library/complex-functions.md#pow)|Вычисляет комплексное число, получаемое в результате возведения основания (комплексное число) в степень другого комплексного числа.|  
|[real](../standard-library/complex-functions.md#real)|Извлекает вещественную часть комплексного числа.|  
|[sin](../standard-library/complex-functions.md#sin)|Возвращает синус комплексного числа.|  
|[sinh](../standard-library/complex-functions.md#sinh)|Возвращает гиперболический синус комплексного числа.|  
|[sqrt](../standard-library/complex-functions.md#sqrt)|Возвращает квадратный корень комплексного числа.|  
|[tan](../standard-library/complex-functions.md#tan)|Возвращает тангенс комплексного числа.|  
|[tanh](../standard-library/complex-functions.md#tanh)|Возвращает гиперболический тангенс комплексного числа.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[operator!=](../standard-library/complex-operators.md#op_neq)|Проверяет на неравенство два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator*](../standard-library/complex-operators.md#op_star)|Умножает два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator+](../standard-library/complex-operators.md#op_add)|Складывает два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator-](../standard-library/complex-operators.md#operator-)|Вычитает два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator/](../standard-library/complex-operators.md#op_div)|Делит два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|Функция шаблона, вставляющая комплексное число в поток вывода.|  
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Проверяет на равенство два комплексных числа, по крайней мере одно из которых может принадлежать к подмножеству типа для вещественной и мнимой частей.|  
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Функция шаблона, извлекающая комплексное число из входного потока.|  
  
### <a name="classes"></a>Классы  
  
|||  
|-|-|  
|[complex\<double>](../standard-library/complex-double.md)|Явно специализированный класс шаблона описывает объект, который хранит упорядоченную пару объектов, оба типа **двойные**, где первый представляет вещественную часть комплексного числа, а второй представляет мнимую часть.|  
|[complex\<float>](../standard-library/complex-float.md)|Явно специализированный класс шаблона описывает объект, который хранит упорядоченную пару объектов, оба типа **float**, где первый представляет вещественную часть комплексного числа, а второй представляет мнимую часть.|  
|[complex\<long double>](../standard-library/complex-long-double.md)|Явно специализированный класс шаблона описывает объект, который хранит упорядоченную пару объектов, оба типа **long double**, где первый представляет вещественную часть комплексного числа, а второй представляет мнимую часть.|  
|[complex](../standard-library/complex-class.md)|Этот класс шаблона описывает объект, используемый для представления системы комплексных чисел и выполнения сложных арифметических операций.|  
  
### <a name="literals"></a>Литералы  
 Заголовок \<complex> определяет следующие [пользовательские литералы](../cpp/user-defined-literals-cpp.md), которые создают комплексное число с нулевой действительной частью и мнимой частью, являющейся значением входного параметра.  
  
|||  
|-|-|  
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Возвращает:`complex<long double>{0.0L, static_cast<long double>(d)}`|  
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Возвращает `complex<double>{0.0, static_cast<double>(d)}`.|  
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Возвращает `complex<float>{0.0f, static_cast<float>(d)}`.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



