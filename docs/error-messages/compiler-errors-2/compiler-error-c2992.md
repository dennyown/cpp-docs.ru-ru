---
title: "Ошибка компилятора C2992 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2992
dev_langs:
- C++
helpviewer_keywords:
- C2992
ms.assetid: 01b16447-43fe-4e91-9a5a-af884a166a31
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb7da305c28b528d40a9a0f90964008be9ba927
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2992"></a>Ошибка компилятора C2992
"класс": список параметров типов недопустим или отсутствует  
  
 Классу предшествует ключевое слово `template` или **generic** с отсутствующими или недопустимыми параметрами.  
  
## <a name="example"></a>Пример  
 При компиляции следующего примера возникнет ошибка C2992:  
  
```  
// C2992.cpp  
// compile with: /c  
template <class T>   
struct TC1 {  
   template <class U>  
   struct TC2;  
};  
  
template <class T>   struct TC1<T>::TC2 {};   // C2992  
  
// OK  
template <class T>  
template <class U>  
struct TC1<T>::TC2 {};  
 // C2992 can also occur when using generics:  
// C2992c.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T> ref struct GC1<T>::GC2 {};   // C2992  
  
// OK  
generic <class T>  
generic <class U>  
ref struct GC1<T>::GC2 {};  
```