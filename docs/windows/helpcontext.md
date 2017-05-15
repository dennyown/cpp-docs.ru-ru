---
title: "helpcontext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpcontext attribute"
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# helpcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Указывает идентификатор контекста, который позволяет пользователю просматривать сведения об этом элементе в файле Справки.  
  
## Синтаксис  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### Параметры  
 `id`  
 Ид контекста темы справки.  См. [Справка HTML. Контекстная справка для программ](../mfc/html-help-context-sensitive-help-for-your-programs.md) дополнительные сведения об идентификаторах контекста.  
  
## Заметки  
 **Контекст справки** Атрибут C\+\+ имеет ту же функциональность, что и  [Контекст справки](http://msdn.microsoft.com/library/windows/desktop/aa366851) атрибут MIDL.  
  
## Пример  
 Эти пример [defaultvalue](../Topic/defaultvalue.md) пример использования  **Контекст справки**.  
  
## Требования  
  
### Контекст атрибута  
  
|||  
|-|-|  
|**Применение**|`interface`"  `typedef`"  **класс**метод, свойство|  
|**Repeatable**|Нет|  
|**Обязательные атрибуты**|None|  
|**Недопустимые атрибуты**|None|  
  
 Дополнительные сведения см. в разделе [Контексты атрибута](../windows/attribute-contexts.md).  
  
## См. также  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpfile](../Topic/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/ru-ru/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)