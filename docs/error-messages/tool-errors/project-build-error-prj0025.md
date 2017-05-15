---
title: "Ошибка построения проекта PRJ0025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0025"
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Ошибка построения проекта PRJ0025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Не удается преобразовать пакетный файл "файл", содержащий знаки Юникод, в кодовую страницу ANSI пользователя.  
  
 ***Содержимое файла в кодировке Юникод***  
  
 Система проектов обнаружила в пользовательском правиле построения или в событии построения содержимое в кодировке Юникод, которое не удается корректно преобразовать в текущую кодовую страницу ANSI пользователя.  
  
 Устранить данную проблему возможно с помощью обновления содержимого правила построения или события построения для использования ANSI, либо с помощью установки кодовой страницы на компьютере в качестве системной настройки по умолчанию.  
  
 Дополнительные сведения об этапах пользовательского построения и событиях построения см. в разделе [Понятие об этапах и событиях пользовательского построения](../../ide/understanding-custom-build-steps-and-build-events.md).