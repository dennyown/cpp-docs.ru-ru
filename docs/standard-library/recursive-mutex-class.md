---
title: "Класс recursive_mutex | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
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
ms.openlocfilehash: 0e5fccf4d1c1019d8922ae0676d7f5fe8e8dfd2a
ms.contentlocale: ru-ru
ms.lasthandoff: 04/29/2017

---
# <a name="recursivemutex-class"></a>Класс recursive_mutex
Представляет *тип мьютекса*. В отличие от класса [mutex](../standard-library/mutex-class-stl.md), поведение вызовов методов блокировки для объектов, которые уже заблокированы, четко определено.  
  
## <a name="syntax"></a>Синтаксис  
  
```
class recursive_mutex;
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|[recursive_mutex](#recursive_mutex)|Создает объект `recursive_mutex`.|  
|[Деструктор ~recursive_mutex](#dtorrecursive_mutex_destructor)|Освобождает все ресурсы, используемые объектом `recursive_mutex`.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[lock](#lock)|Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца мьютекса.|  
|[try_lock](#try_lock)|Попытки получить права владельца мьютекса без блокировки.|  
|[unlock](#unlock)|Освобождает права владения мьютексом.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<мьютекс >  
  
 **Пространство имен:** std  
  
##  <a name="lock"></a>  lock  
 Блокирует вызывающий поток до тех пор, пока этот поток не получит права владельца объекта `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Примечания  
 Если вызывающий поток уже владеет `mutex`, метод немедленно возвращает значение и предыдущая блокировка остается в силе.  
  
##  <a name="recursive_mutex"></a>  recursive_mutex  
 Создает объект `recursive_mutex`, который не заблокирован.  
  
```cpp  
recursive_mutex();
```  
  
##  <a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex  
 Освобождает все ресурсы, используемые объектом.  
  
```cpp  
~recursive_mutex();
```  
  
### <a name="remarks"></a>Примечания  
 Если при выполнении деструктора объект заблокирован, поведение не определено.  
  
##  <a name="try_lock"></a>  try_lock  
 Попытки получить права владельца объекта `mutex` без блокировки.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 `true`, если метод успешно получает права владельца `mutex` или если вызывающий поток уже владеет `mutex`; в противном случае — `false`.  
  
### <a name="remarks"></a>Примечания  
 Если вызывающий поток уже владеет `mutex`, метод немедленно возвращает `true` и предыдущая блокировка остается в силе.  
  
##  <a name="unlock"></a>  unlock  
 Освобождает права владения мьютексом.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Примечания  
 Этот метод освобождает владение `mutex` только после его вызова столько раз, сколько [lock](#lock) и [try_lock](#try_lock) были успешно вызваны для объекта`recursive_mutex`.  
  
 Если вызывающий поток не является владельцем `mutex`, поведение не определено.  
  
## <a name="see-also"></a>См. также  
 [Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



