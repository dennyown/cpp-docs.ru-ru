---
title: "/HEAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "выделение кучи, задание размера кучи"
  - "Параметр HEAP editbin"
  - "Параметр -HEAP editbin"
  - "Параметр /HEAP editbin"
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /HEAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Задает размер кучи в байтах.  Этот параметр применяется только к исполняемым файлам.  
  
```  
  
/HEAP:  
reserve[,commit]  
  
```  
  
## Заметки  
 Аргумент `reserve` задает полное начальное выделение кучи в виртуальной памяти.  По умолчанию размер кучи 1 МБ.  [Справочник ЕDITBIN](../Topic/EDITBIN%20Reference.md) округляет вверх указанное значение ближе к многократному чтению 4 байт.  
  
 Необязательный аргумент `commit` интерпретируется операционной системой.  В операционной системе Windows, оно указывает начальную объем физической памяти для выделения и объем дополнительной памяти для выделения кучи, когда необходимо развернуть.  Выделенная виртуальная память резервирует пространство в файле разбиения по страницам.  Более высокое `commit` значение позволяет системе для распределения памяти часто, когда приложению требуется больше места кучи, но увеличивает требования к памяти и, возможно, длительность запуска приложения.  `commit` значение должно быть меньше или равно `reserve` значение.  
  
 Укажите значения `reserve` и `commit` в шестнадцатеричной системе счисления десятичного числа или языка C\# или восьмиштырьковой нотации.  Например, значение 1 МБ, можно задать 1048576 в десятичном количества или как 0x100000 в шестнадцатеричной системе счисления или как 04000000 в восьмиштырьковом.  
  
## См. также  
 [Параметры EDITBIN](../../build/reference/editbin-options.md)