---
title: "Ошибка компилятора C3910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3910"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3910"
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C3910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"событие": должен быть определен член "метод"  
  
 В определенном событии отсутствует указанный обязательный метод доступа.  
  
 Дополнительные сведения см. в описании [событий](../../windows/event-cpp-component-extensions.md).  
  
 Следующий пример приводит к возникновению ошибки C3910:  
  
```  
// C3910.cpp  
// compile with: /clr /c  
delegate void H();  
ref class X {  
   event H^ E {  
      // uncomment the following lines  
      // void add(H^) {}  
      // void remove( H^ h ) {}  
      // void raise( ) {}  
   };   // C3910  
  
   event H^ E2; // OK data member  
};  
```