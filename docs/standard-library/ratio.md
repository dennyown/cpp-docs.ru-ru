---
title: "&lt;ratio&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ratio/std::mega
- ratio/std::peta
- ratio/std::ratio_greater
- ratio/std::micro
- ratio/std::ratio_add
- ratio/std::ratio_not_equal
- ratio/std::hecto
- ratio/std::nano
- ratio/std::ratio_less_equal
- ratio/std::ratio_less
- ratio/std::centi
- ratio/std::ratio_greater_equal
- ratio/std::ratio_subtract
- <ratio>
- ratio/std::atto
- ratio/std::tera
- ratio/std::milli
- ratio/std::ratio_multiply
- ratio/std::kilo
- ratio/std::ratio_divide
- ratio/std::giga
- ratio/std::pico
- ratio/std::femto
- ratio/std::ratio_equal
- ratio/std::ratio
- ratio/std::exa
- ratio/std::deci
- ratio/std::deca
dev_langs:
- C++
ms.assetid: 8543e912-2d84-45ea-b3c0-bd7bfacee405
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 39fdef1976a506c36a553d575c83462e7c6e9ee0
ms.lasthandoff: 02/24/2017

---
# <a name="ltratiogt"></a>&lt;ratio&gt;
Включите стандартный заголовок \<ratio> для определения констант и шаблонов, которые используются для хранения и обработки рациональных чисел во время компиляции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
#include <ratio>  
```  
  
### <a name="ratio-structure"></a>Структура ratio  

```
struct ratio
{
    static constexpr intmax_t num;
    static constexpr intmax_t den;
    typedef ratio<num, den>  type;
};
```  
 Структура [ratio](http://msdn.microsoft.com/en-us/3f7961f4-802b-4251-b3c3-090ef91c0dba) определяет статические константы `num` и `den`, так что `num` / `den` == N / D и `num` и `den` не имеют общих делителей. `num` / `den` — это `value`, представленный классом-шаблоном. Таким образом `type` определяет экземпляр `ratio<N0, D0>`, для которого `num` == N0 и `den` == D0.  
  
### <a name="specializations"></a>Специализации  
 \<ratio> также определяет специализации `ratio`, которые имеют следующую форму.  
  
 `template <class R1, class R2> struct ratio_specialization`  
  
 Каждая специализация принимает два параметра-шаблона, которые также должны быть специализациями `ratio`. Значение `type` определяется связанной логической операцией.  
  
|Имя|Значение `type`|  
|----------|------------------|  
|`ratio_add`|`R1 + R2`|  
|`ratio_divide`|`R1 / R2`|  
|`ratio_equal`|`R1 == R2`|  
|`ratio_greater`|`R1 > R2`|  
|`ratio_greater_equal`|`R1 >= R2`|  
|`ratio_less`|`R1 < R2`|  
|`ratio_less_equal`|`R1 <= R2`|  
|`ratio_multiply`|`R1 * R2`|  
|`ratio_not_equal`|`!(R1 == R2)`|  
|`ratio_subtract`|`R1 - R2`|  
  
### <a name="typedefs"></a>определения типов  
  
```
typedef ratio<1,  1000000000000000000> atto;
typedef ratio<1,     1000000000000000> femto;
typedef ratio<1,        1000000000000> pico;
typedef ratio<1, 1000000000> nano;
typedef ratio<1, 1000000> micro;
typedef ratio<1, 1000> milli;
typedef ratio<1,  100> centi;
typedef ratio<1,   10> deci;
typedef ratio<10, 1> deca;
typedef ratio<100, 1> hecto;
typedef ratio<1000, 1> kilo;
typedef ratio<1000000, 1> mega;
typedef ratio<1000000000, 1> giga;
typedef ratio<1000000000000, 1> tera;
typedef ratio<1000000000000000, 1> peta;
typedef ratio<1000000000000000000, 1> exa;
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)



