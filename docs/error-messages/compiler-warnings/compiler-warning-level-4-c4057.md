---
title: "Компилятор C4057 предупреждение (уровень 4) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ad1013a90b2b3d6ad1f7148ea62c05ae505348d4
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4057"></a>Предупреждение компилятора (уровень 4) C4057
"оператор": "идентификатор1" отличается от "идентификатор2" по косвенному обращению к слегка разным базовым типам  
  
 Два выражения указателя ссылаются на разные базовые типы. Выражения используются без преобразования.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Чтобы устранить ошибку, проверьте указанные ниже возможные причины ее возникновения.  
  
1.  Сочетание типов со знаком и без знака.  
  
2.  Сочетание **коротких** и **длинных** типов.