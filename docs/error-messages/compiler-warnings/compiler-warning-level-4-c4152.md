---
title: "Предупреждение (уровень 4) C4152 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4152
dev_langs:
- C++
helpviewer_keywords:
- C4152
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
caps.latest.revision: 6
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
ms.openlocfilehash: 4c8a1b57463ceaee36d72e4c8f7680b392cc9ced
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4152"></a>Предупреждение компилятора (уровень 4) C4152
нестандартное расширение, преобразование указателя функции/указателя данных в выражении  
  
 Указатель функции преобразуется в указатель данных или наоборот. Подобное преобразование допустимо при использовании расширений Майкрософт (/Ze), но не в ANSI C.