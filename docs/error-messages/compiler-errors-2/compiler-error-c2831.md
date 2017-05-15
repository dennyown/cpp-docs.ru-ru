---
title: "Ошибка компилятора C2831 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2831"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2831"
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C2831
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"operator оператор" не может иметь параметры по умолчанию  
  
 Параметры по умолчанию могут иметь только три оператора:  
  
-   [new](../../cpp/new-operator-cpp.md)  
  
-   Присваивание "\=";  
  
-   Левая круглая скобка "\(".  
  
 Следующий пример приводит к возникновению ошибки C2831:  
  
```  
// C2831.cpp  
// compile with: /c  
#define BINOP <=  
class A {  
public:  
   int i;  
   int operator BINOP(int x = 1) {   // C2831  
   // try the following line instead  
   // int operator BINOP(int x) {  
      return i+x;  
   }  
};  
```