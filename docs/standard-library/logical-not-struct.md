---
title: "Структура logical_not | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- logical_not
- xfunctional/std::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not class
- logical_not struct
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 2f84361ba71a50601349542797840e2d45ffad21
ms.lasthandoff: 02/24/2017

---
# <a name="logicalnot-struct"></a>Структура logical_not
Предопределенный объект функции, который выполняет над своими аргументами операцию логического отрицания ( `operator!`).  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class Type = void>
struct logical_not : public unary_function<Type, bool>  
{
    bool operator()(const Type& Left) const;
};

// specialized transparent functor for operator!
template <>
struct logical_not<void>  
{
  template <class Type>
  auto operator()(Type&& Left) const`
     -> decltype(!std::forward<Type>(Left));
 };
```  
  
#### <a name="parameters"></a>Параметры  
 `Type`  
 Любой тип, поддерживающий `operator!`, принимающий операнды указанного или выводимого типа.  
  
 `Left`  
 Операнд операции логического отрицания. Неспециализированный шаблон принимает ссылочный аргумент lvalue типа `Type`. Специализированный шаблон выполняет точную пересылку ссылочных аргументов lvalue и rvalue выводимого типа `Type`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Результат `!``Left`. Специализированный шаблон выполняет точную пересылку результата типа, возвращаемого `operator!`.  
  
## <a name="example"></a>Пример  
  
```cpp  
// functional_logical_not.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2 ( 7 );  
   deque<bool>::iterator iter1, iter2;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((i % 2) != 0));  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   // To flip all the truth values of the elements,  
   // use the logical_not function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );  
   cout << "The deque with its values negated is:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
}  
/* Output:  
Original deque:  
 d1 = ( false true false true false true false )  
The deque with its values negated is:  
 d2 = ( true false true false true false true )  
 */  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<functional>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)



