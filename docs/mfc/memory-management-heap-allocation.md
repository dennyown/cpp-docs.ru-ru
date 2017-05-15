---
title: "Управление памятью. Выделение кучи | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete - оператор, использование с MFC отладки"
  - "обнаружение утечек памяти"
  - "выделение кучи"
  - "выделение кучи, описание"
  - "выделение памяти, память в куче"
  - "утечки памяти, обнаружение"
  - "память, обнаружение утечек"
  - "new - оператор, использование с MFC отладки"
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Управление памятью. Выделение кучи
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Куче зарезервировано для выделения памяти программы.  Область в дополнение к программного кода и стека.  Типичные написанные на C программы используют функции `malloc` и **free** для выделения и освобождения памяти кучи.  Отладочная версия MFC предоставляет измененные версии операторов **новыйудалить** C\+\+ встроенных для выделения и освобождения памяти объекты в куче.  
  
 При использовании метода **новый** и **удалить**, а не `malloc` и **free**, можно воспользоваться усовершенствований отладки управления памятью библиотеки классов, которые могут быть полезны в обнаружения утечек памяти.  При построении выпуска программы с версией MFC, версии стандартных операторов **новый** и **удалить** предоставляют эффективный способ выделения и освобождения памяти \(исходная версия MFC не предоставляет измененные версии этих операторов\).  
  
 Обратите внимание, что общий размер выбранных объектов в куче ограничен только виртуальной памятью системы доступна.  
  
## См. также  
 [Управление памятью](../mfc/memory-management.md)