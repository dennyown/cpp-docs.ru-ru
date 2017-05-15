---
title: "Структура multiplies | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multiplies
- xfunctional/std::multiplies
dev_langs:
- C++
helpviewer_keywords:
- multiplies class
- multiplies struct
ms.assetid: ec85e8af-70ad-44ad-90f0-d961a5847864
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
ms.openlocfilehash: 10f5a34631f713218873d508e41a793b7851bf7c
ms.lasthandoff: 02/24/2017

---
# <a name="multiplies-struct"></a>Структура multiplies
Стандартный объект функции, который выполняет над своими аргументами операцию умножения (двоичное `operator*`).  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class Type = void>
struct multiplies : public binary_function <Type, Type, Type>  
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator*
template <>
struct multiplies<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) * std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>Параметры  
 `Type`, `T`, `U`  
 Тип, поддерживающий бинарный `operator*`, который принимает операнды указанного или выводимого типа.  
  
 `Left`  
 Левый операнд в операции умножения. Неспециализированный шаблон принимает ссылочный аргумент lvalue типа `Type`. Специализированный шаблон выполняет точную пересылку ссылочных аргументов lvalue и rvalue выводимого типа `T`.  
  
 `Right`  
 Правый операнд в операции умножения. Неспециализированный шаблон принимает ссылочный аргумент lvalue типа `Type`. Специализированный шаблон выполняет точную пересылку ссылочных аргументов lvalue и rvalue выводимого типа `U`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Результат `Left``*``Right`. Специализированный шаблон выполняет точную пересылку результата типа, возвращаемого `operator*`.  
  
## <a name="example"></a>Пример  
  
```cpp  
// functional_multiplies.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2, v3 ( 6 );  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 1 ; i <= 6 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int j;  
   for ( j = 1 ; j <= 6 ; j++ )  
   {  
      v2.push_back( 3 * j );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise products of the elements of v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      multiplies<int>( ) );  
  
   cout << "The element-wise products of vectors V1 & v2\n are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
\* Output:   
The vector v1 = ( 2 4 6 8 10 12 )  
The vector v2 = ( 3 6 9 12 15 18 )  
The element-wise products of vectors V1 & v2  
 are: ( 6 24 54 96 150 216 )  
*\  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<functional>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)



