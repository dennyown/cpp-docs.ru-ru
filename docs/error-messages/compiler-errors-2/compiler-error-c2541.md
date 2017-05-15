---
title: "Ошибка компилятора C2541 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2541"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2541"
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C2541
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"delete" : удаление : невозможно удалить объекты, не являющиеся указателями  
  
 Оператор [delete](../../cpp/delete-operator-cpp.md) используется с объектом, не являющимся указателем.  
  
 Следующий пример приводит к возникновению ошибки C2541:  
  
```  
// C2541.cpp  
int main() {  
   int i;  
   delete i;   // C2541 i not a pointer  
  
   // OK  
   int *ip = new int;  
   delete ip;  
}  
```