---
title: "Ошибка компилятора C2437 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2437"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2437"
ms.assetid: 2d2b3c6c-856a-4b27-ae10-64813b3e5483
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Ошибка компилятора C2437
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"идентификатор": инициализация уже выполнена  
  
 Объект можно инициализировать только один раз.  
  
 Следующий пример приводит к возникновению ошибки C2437:  
  
```  
// C2437.cpp  
// compile with: /c  
class A {  
public:  
   A(int i) {}  
};  
  
class B : A {  
   B() : A(1), A(2) {}   // C2437  
   B() : A(1) {}   // OK  
};  
```