---
title: "Ошибка компилятора C3537 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3537"
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Ошибка компилятора C3537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"тип": приведение к типу, содержащему ключевое слово "auto", невозможно  
  
 Нельзя привести переменную к указанному типу, поскольку тип содержит ключевое слово `auto` и применяется параметр компилятора по умолчанию [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md).  
  
## Пример  
 Следующий код вызывает ошибку C3537, поскольку переменные приводятся к типу, содержащему ключевое слово `auto`.  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## См. также  
 [Ключевое слово auto](../../cpp/auto-keyword.md)