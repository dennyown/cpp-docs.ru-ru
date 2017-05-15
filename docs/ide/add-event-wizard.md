---
title: "Мастер добавления события | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.event.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "мастер добавления события [C++]"
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Мастер добавления события
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Этот мастер используется для добавления события в проект элемента управления MFC ActiveX.  Можно задать собственное событие, настроить автоматически инициализируемое событие или выбрать из списка автоматически инициализируемых событий.  
  
 **Имя события**  
 Задает имя, используемое клиентами автоматизации для запроса события из класса.  Введите имя или выберите его из списка.  
  
 **Тип события**  
 Указывает тип добавляемого события.  Доступен только при выборе из списка **Имя события**.  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Стандартное**|Показывает, что для данного класса будет реализовано автоматически инициализируемое событие хранения, например нажатие кнопки.  Автоматически инициализируемые события определены в библиотеке Microsoft Foundation Class \(MFC\).|  
|**Пользовательское**|Указывает на то, что предоставляется собственная реализация события.|  
  
 **Внутреннее имя**  
 Задает имя функции\-члена, которая отправляет событие.  Доступен только для пользовательских событий.  Это имя основано на имени **Имя события**.  Можно изменить внутреннее имя, если необходимо предоставить имя, отличное от **Имя события**.  
  
 **Тип параметра**  
 Задает тип параметра для **имени параметра**.  Выберите тип из списка.  
  
 **Имя параметра**  
 Задает имя параметра для передачи через событие.  После ввода имени нужно нажать кнопку **Добавить**, чтобы добавить его в список параметров.  
  
 После нажатия кнопки **Добавить** в **Списке параметров** появляется имя параметра.  
  
> [!NOTE]
>  Если после ввода имени параметра нажать кнопку **Готово** прежде кнопки **Добавить**, параметр не добавляется к событию.  Необходимо найти метод и ввести параметр вручную. **Список параметров**  
  
 **Добавить**  
 Добавляет параметр, который указан в поле **Имя параметра**, и его тип в **Список параметров**.  Чтобы добавить параметр в список, нажмите кнопку **Добавить**.  
  
 **Удалить**  
 Удаляет выбранный параметр из **Списка параметров**.  
  
 **Список параметров**  
 Отображает все параметры и их типы, добавленные в метод в настоящий момент.  После добавления параметров мастер обновляет **Список параметров** и отображает каждый параметр вместе с его типом.  
  
## См. также  
 [Добавление события](../Topic/Adding%20an%20Event%20\(Visual%20C++\).md)