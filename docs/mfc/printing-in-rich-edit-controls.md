---
title: "Печать в элементах управления Rich Edit | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab8e15e25e2d419bb7c3ac67fc2c6f3453fb03c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="printing-in-rich-edit-controls"></a>Печать в элементах управления "Rich Edit"
Можно определить элемент управления rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) для отображения его выходных данных для заданного устройства, такие как принтер. Можно также указать, что устройство вывода, для которого элемент управления rich edit форматирует его текст.  
  
 Чтобы отформатировать часть содержимого элемента управления "rich edit" для конкретного устройства, можно использовать [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) функции-члена. [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) структура, используемая с помощью этой функции указывает диапазон текста для форматирования, а также контекст устройства (DC) для целевого устройства.  
  
 После форматирования текста для вывода устройства, можно отправить выходные данные на устройстве с помощью [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) функции-члена. С помощью многократно `FormatRange` и `DisplayBand`, приложение, на печать выводится содержимое элемента управления rich edit можно реализовать чередования. (Полосы — деления на более мелкие части выходных данных для печати).  
  
 Можно использовать [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) функции-члена для указания целевого устройства, для которого элемент управления rich edit форматирует его текст. Эта функция полезна для WYSIWYG (что видите вы получаете) «форматирование», в котором приложение располагает текст, с помощью метрики шрифтов принтер по умолчанию вместо экрана.  
  
## <a name="see-also"></a>См. также  
 [Использование CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)

