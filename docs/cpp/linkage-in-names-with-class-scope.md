---
title: "Компоновка в именах в области класса | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "имена классов [C++], компоновка"
  - "область класса [C++], компоновка в именах с"
  - "классы [C++], имена"
  - "классы [C++], область действия"
  - "внешняя компоновка, правила связи областей"
  - "компоновка [C++], правила связи областей"
  - "имена [C++], правила связи областей"
  - "область [C++], имена классов"
  - "область [C++], правила связи"
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Компоновка в именах в области класса
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Для имен с областью видимости класса применяются следующие правила компоновки:  
  
-   статические члены класса имеют внешнюю компоновку;  
  
-   функции\-члены класса имеют внешнюю компоновку;  
  
-   перечислители и имена `typedef` не имеют компоновки.  
  
 **Блок, относящийся только к системам Microsoft**  
  
-   Функции, объявленные как функции `friend`, должны иметь внешнюю компоновку.  Объявление статической функции как функции `friend` приводит к ошибке.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## См. также  
 [Программа и компоновка](../cpp/program-and-linkage-cpp.md)