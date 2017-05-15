---
title: "Ошибка вычислителя выражений CXX0019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0019"
  - "CXX0019"
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Ошибка вычислителя выражений CXX0019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

неправильное приведение типа  
  
 Вычислителю выражения С не удалось выполнить приведение типа согласно записи.  
  
 Эта ошибка идентична ошибке CAN0019.  
  
### Чтобы устранить ошибку, следует проверить следующие возможные причины ее возникновения.  
  
1.  Указанный тип неизвестен.  
  
2.  Слишком много уровней типов указателя.  Например, приведение типа  
  
    ```  
    (char **)h_message  
    ```  
  
     не может быть вычислено с помощью вычислителя выражений С.