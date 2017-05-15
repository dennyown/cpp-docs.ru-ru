---
title: "Неустранимая ошибка C1091 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f014e2b9d34cdac17adefe88c4947ee5fb66cfcc
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1091"></a>Неустранимая ошибка C1091
ограничение компилятора: длина строки превышает "длину" байт  
  
 Длина строковой константы превышает установленное ограничение.  
  
 Может потребоваться разбить статическую строку на две (или более) переменных и использовать [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) для объединения результатов в рамках объявления или во время выполнения.