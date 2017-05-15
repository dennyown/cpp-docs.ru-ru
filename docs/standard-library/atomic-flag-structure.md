---
title: "Структура atomic_flag | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 9fe3617331c7019956af5d64789624e299c17242
ms.contentlocale: ru-ru
ms.lasthandoff: 04/29/2017

---
# <a name="atomicflag-structure"></a>Структура atomic_flag
Описывает объект, который автоматически устанавливает и очищает флаг `bool`. Операции с атомарными флагами всегда неблокирующие.  
  
## <a name="syntax"></a>Синтаксис  
  
```
struct atomic_flag;
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[clear](#clear)|Устанавливает сохраненный флаг в значение `false`.|  
|[test_and_set](#test_and_set)|Устанавливает сохраненный флаг в значение `true` и возвращает начальное значение флага.|  
  
## <a name="remarks"></a>Примечания  
 Объекты `atomic_flag` могут передаваться в функции [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) и [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit), которые не являются функциями-членами. Их можно инициализировать с помощью значения `ATOMIC_FLAG_INIT`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<atomic >  
  
 **Пространство имен:** std  
  
##  <a name="clear"></a>atomic_flag::Clear
 Устанавливает флаг `bool`, хранящийся в объекте `*this``false` с соблюдением указанных ограничений [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Параметры  
 `Order`  
 Перечисление [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="test_and_set"></a>atomic_flag::test_and_set
 Устанавливает флаг `bool`, хранящийся в объекте `*this``true` с соблюдением указанных ограничений [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Параметры  
 `Order`  
 Перечисление [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Возвращаемое значение  
 Начальное значение флага, который хранится в `*this`.  
  
## <a name="see-also"></a>См. также  
 [\<atomic>](../standard-library/atomic.md)



