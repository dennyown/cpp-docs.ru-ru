---
title: "Ошибка компилятора C3755 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3755"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3755"
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Ошибка компилятора C3755
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"делегат": делегат не может быть определен  
  
 Делегат \([delegate](../../windows/delegate-cpp-component-extensions.md)\) может быть объявлен, но не определен.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки C3755.  
  
```  
// C3755.cpp  
// compile with: /clr /c  
delegate void MyDel() {};   // C3755  
```  
  
## Пример  
 Ошибка C3755 может также возникать при попытке создания шаблона делегата.  Следующий пример приводит к возникновению ошибки C3755.  
  
```  
// C3755_b.cpp  
// compile with: /clr /c  
ref struct R {  
   template<class T>  
   delegate void D(int) {}   // C3755  
};  
```