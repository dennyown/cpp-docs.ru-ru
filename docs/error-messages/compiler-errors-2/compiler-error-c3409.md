---
title: "Ошибка компилятора C3409 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3409"
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Ошибка компилятора C3409
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Пустой блок атрибута не допускается  
  
 Компилятор интерпретировал квадратные скобки как блок [атрибута](../../windows/cpp-attributes-reference.md), однако атрибуты не были обнаружены.  
  
 Эта ошибка компилятора может возникать при использовании квадратных скобок как части определения лямбда\-выражения.  Ошибка возникает, если компилятор не может определить, являются ли квадратные скобки частью определения лямбда\-выражения или частью блока атрибутов.  Дополнительные сведения о лямбда\-выражениях см. в разделе [Лямбда\-выражения](../../cpp/lambda-expressions-in-cpp.md).  
  
### Исправление этой ошибки  
  
1.  Если квадратные скобки являются частью блока атрибутов:  
  
    1.  укажите как минимум один атрибут в блоке атрибутов;  
  
    2.  удалите блок атрибутов.  
  
2.  Если квадратные скобки являются частью лямбда\-выражения:  
  
    1.  убедитесь, что в лямбда\-выражении соблюдаются правила синтаксиса.  
  
         Дополнительные сведения о синтаксисе лямбда\-выражений см. в разделе [Синтаксис лямбда\-выражений](../../cpp/lambda-expression-syntax.md).  
  
## Пример  
 Следующий пример вызывает ошибку C3409.  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## Пример  
 Следующий пример вызывает ошибку C3409, поскольку в лямбда\-выражении используется спецификация `mutable`, но не предоставлен список параметров.  Компилятор не может определить, являются ли квадратные скобки частью определения лямбда\-выражения или частью блока атрибутов.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## См. также  
 [атрибут](../../windows/cpp-attributes-reference.md)   
 [Лямбда\-выражения](../../cpp/lambda-expressions-in-cpp.md)   
 [Синтаксис лямбда\-выражений](../../cpp/lambda-expression-syntax.md)