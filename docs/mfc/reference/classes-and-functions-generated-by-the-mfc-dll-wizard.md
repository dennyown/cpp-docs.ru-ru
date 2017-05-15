---
title: "Классы и функции, создаваемые мастером MFC DLL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [MFC]
- functions [MFC], DLLs
- MFC DLL Wizard
- DLLs [C++], wizard classes and functions
- classes [C++], generated by MFC DLL wizard
- code [C++], generated by MFC DLL wizard
ms.assetid: e69e62fe-4953-42bf-a2fc-50bbf9bdaeaf
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 631b8ce97cfe98fe84b9e90f88a1c0b0d0f2a41d
ms.lasthandoff: 02/24/2017

---
# <a name="classes-and-functions-generated-by-the-mfc-dll-wizard"></a>Классы и функции, создаваемые мастером MFC DLL
Код, формируемый мастером MFC DLL зависит от типа создаваемой библиотеки DLL и параметры, которые вы выбрали. Мастера библиотек DLL MFC создает такой же код для обеих форм регулярных библиотек DLL.  
  
|Тип библиотеки DLL|Параметр|Классы|Функции|  
|-----------------|------------|-------------|---------------|  
|[Расширение](../../build/extension-dlls-overview.md)|Нет|Нет|`DllMain`|  
|[Обычный](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Нет|Приложения класса, производного от`CWinApp`|Нет|  
|[Обычный](../../build/regular-dlls-dynamically-linked-to-mfc.md)|автоматизация|Приложения класса, производного от`CWinApp`|**DllGetClassObjectDllCanUnloadNowDllRegisterServer**|  
|[Расширение](../../build/extension-dlls-overview.md)|Окно сокетов|Нет|`DllMain`|  
|[Обычный](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Окно сокетов|Приложения класса, производного от`CWinApp`|`InitInstance`содержит вызов`AfxSocketInit`|  
  
## <a name="see-also"></a>См. также  
 [Мастера библиотек DLL MFC](../../mfc/reference/mfc-dll-wizard.md)

