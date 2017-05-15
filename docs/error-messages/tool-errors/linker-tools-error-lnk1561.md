---
title: "Ошибка средств компоновщика LNK1561 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: f918c51e6f4539c020bc59ad28c867f8e2d1ae75
ms.contentlocale: ru-ru
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1561"></a>Ошибка средств компоновщика LNK1561
точка входа должна быть определена  
  
Не удалось найти компоновщик *точки входа*, начальной функции, вызываемой в исполняемый файл. По умолчанию компоновщик будет искать `main` или `wmain` функции для консольного приложения, `WinMain` или `wWinMain` функции для приложения Windows, или `DllMain` для DLL-Библиотеки, требующий инициализации. Можно указать другой функции с помощью [/Entry](../../build/reference/entry-entry-point-symbol.md) компоновщика.  
  
Эта ошибка может иметь несколько причин:  
-   Возможно, не включен файл, который определяет точку входа в список файлов для связывания. Проверьте, связанного файла, содержащего функцию точки входа в приложение.  
-   Определенные точки входа, с помощью подписи неправильной функции; Например вы может опечатка или используемого неправильного регистра в имени функции или неправильно указан тип возвращаемого значения или типы параметров.  
-   Не указан [/DLL](../../build/reference/dll-build-a-dll.md) параметр при создании библиотеки DLL.  
-   Вы может неверно указанного имени функции точки входа при использовании [/Entry](../../build/reference/entry-entry-point-symbol.md) компоновщика.  
-   Если вы используете [LIB](../../build/reference/lib-reference.md) инструмент для создания библиотеки DLL, указанный DEF-файла. В этом случае удалите DEF-файл из сборки.    
  
При построении приложения, компоновщик будет искать функцию точки входа для вызова для запуска кода. Это функция, которая вызывается после загрузки приложения и инициализации среды выполнения. Необходимо указать функцию точки входа для приложения, или не удается запустить приложение. Точкой входа является необязательным для библиотеки DLL. По умолчанию компоновщик будет искать функцию точки входа, который имеет один из нескольких конкретные имена и подписи, такие как `int main(int, char**)`. Можно указать другое имя функции в качестве записи точки с помощью параметра компоновщика/ENTRY.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```