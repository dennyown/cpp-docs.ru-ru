---
title: "&lt;tuple&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <tuple>
dev_langs:
- C++
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
caps.latest.revision: 20
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
ms.openlocfilehash: 212b2b5af678bd39b4ecc7d6622c71db20db5a26
ms.contentlocale: ru-ru
ms.lasthandoff: 04/29/2017

---
# <a name="lttuplegt"></a>&lt;tuple&gt;
Определяет шаблон `tuple`, экземпляры которого содержат объекты различных типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#include <tuple>  
```  
  
### <a name="classes"></a>Классы  
  
|||  
|-|-|  
|[tuple](../standard-library/tuple-class.md)|Создает последовательность элементов фиксированной длины.|  
|[Класс tuple_element](../standard-library/tuple-element-class-tuple.md)|Заключает в оболочку тип элемента `tuple`.|  
|[Класс tuple_size](../standard-library/tuple-size-class-tuple.md)|Создает оболочку для счетчика элементов `tuple`.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор==](../standard-library/tuple-operators.md#op_eq_eq)|Сравнение объектов `tuple`, равенство|  
|[оператор!=](../standard-library/tuple-operators.md#op_neq)|Сравнение объектов `tuple`, неравенство|  
|[оператор<](../standard-library/tuple-operators.md#op_lt)|Сравнение объектов `tuple`, меньше|  
|[оператор<=](../standard-library/tuple-operators.md#op_lt_eq)|Сравнение объектов `tuple`, меньше или равно|  
|[оператор>](../standard-library/tuple-operators.md#op_gt)|Сравнение объектов `tuple`, больше|  
|[оператор>=](../standard-library/tuple-operators.md#op_gt_eq)|Сравнение объектов `tuple`, больше или равно|  
  
### <a name="functions"></a>Функции  
  
|||  
|-|-|  
|[get](../standard-library/tuple-functions.md#get)|Возвращает элемент из объекта `tuple`.|  
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|Создает `tuple` из значений элементов.|  
|[tie](../standard-library/tuple-functions.md#tie)|Создает `tuple` из ссылок на элементы.|  
  
## <a name="see-also"></a>См. также  
 [\<array>](../standard-library/array.md)

