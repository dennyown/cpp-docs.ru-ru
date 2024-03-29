---
title: "Постоянные выражения C++ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd30dd51b3d87b7d82b917734d187ae2278837a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="c-constant-expressions"></a>Постоянные выражения C++
Объект *константой* значение является одним из не изменяется. В C++ имеется два ключевых слова, позволяющих указать, что объект не должен изменяться, и для осуществления этого намерения.  
  
 В C++ требуются константные выражения, то есть выражения, результатом вычисления которых является константа, для объявления следующих элементов.  
  
-   Границы массива.  
  
-   Селекторы в операторах case.  
  
-   Спецификация длины битового поля.  
  
-   Инициализаторы перечисления.  
  
 Ниже перечислены единственные допустимые операнды в константных выражениях.  
  
-   Литералы  
  
-   Константы перечисления.  
  
-   Значения, объявленные как константы, которые инициализированы с константными выражениями.  
  
-   Выражения `sizeof`  
  
 Нецелочисленные константы должны преобразовываться (явно или неявно) в целочисленные типы, чтобы быть допустимыми в константном выражении. Поэтому следующий код допустим.  
  
```  
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
 Явные преобразования в целочисленные типы допустимы в константных выражениях. Все другие типы и производные типы недопустимы, за исключением случаев использования в качестве операндов оператора `sizeof`.  
  
 Запятую-оператор и операторы присваивания невозможно использовать в константных выражениях.  
  
## <a name="see-also"></a>См. также  
 [Типы выражений](../cpp/types-of-expressions.md)