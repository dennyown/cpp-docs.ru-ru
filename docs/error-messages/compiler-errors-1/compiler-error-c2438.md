---
title: "Ошибка компилятора C2438 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2438"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2438"
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Ошибка компилятора C2438
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"идентификатор" : не удается инициализировать статические данные класса с помощью конструктора  
  
 Конструктор используется для инициализации статических членов класса.  Статические члены должны инициализироваться в определении, расположенном вне объявления класса.  
  
 Следующий пример приводит к возникновению ошибки C2438:  
  
```  
// C2438.cpp  
struct X {  
   X(int i) : j(i) {}   // C2438  
   static int j;  
};  
  
int X::j;  
  
int main() {  
   X::j = 1;  
}  
```