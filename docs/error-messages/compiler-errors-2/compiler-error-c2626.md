---
title: "Ошибка компилятора C2626 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2626
dev_langs:
- C++
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 837fae0a32d473b5bf9adcf5c5fd4c564c7b033a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2626"></a>Ошибка компилятора C2626
identifier: закрытый или защищенный элемент данных не допускается в анонимной структуре или объединении  
  
 У элемента анонимной структуры или объединения должен быть открытый доступ.  
  
 Следующий пример приводит к возникновению ошибки C2626:  
  
```  
// C2626.cpp  
int main() {  
   union {  
   protected:  
      int j;     // C2626, j is protected  
   private:  
      int k;     // C2626, k is private  
   };  
}  
```  
  
 Чтобы устранить эту проблему, удалите теги private или protected:  
  
```  
// C2626b.cpp  
int main() {  
   union {  
   public:  
      int i;   // OK, i is public  
   };  
}  
```