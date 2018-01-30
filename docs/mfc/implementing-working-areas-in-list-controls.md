---
title: "Реализация рабочих областей в элементах управления списками | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cefb8007fd9b73dda4c0e8a99e9ae9daa1bfcc34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-working-areas-in-list-controls"></a>Реализация рабочих областей в элементах управления "Список"
По умолчанию элемент управления списком упорядочивает все элементы в виде стандартной сетки. Однако поддерживается одного метода другим, рабочих областей, которые упорядочивает элементы списка по группам прямоугольные. Для изображения элемента управления списка, который реализует рабочие области в разделе с использованием элементов управления представление списка в Windows SDK.  
  
> [!NOTE]
>  Рабочие области видимы только в том случае, когда элемент управления список находится в режиме маленького значка или значок. Тем не менее любой текущий рабочие области сохраняются, если представление переключается в режим отчета или списка.  
  
 Рабочие области можно использовать для отображения пустой границы (на left, top или справа от элементов) или привести к горизонтальной полосы прокрутки для отображения при обычно не будет существовать один. Другим распространенным вариантом применения является создание нескольких рабочие области, к которым можно перемещать и удалении элементов. С помощью этого метода можно создать области в одном представлении, имеют различные значения. Пользователь может затем упорядочивания элементов, поместив их в другой области. Примером будет представление файловой системы, имеющий область для чтения и записи файлов и в другой области для файлов только для чтения. Если элемент файлы были перемещены в область только для чтения, автоматически станут доступны только для чтения. Перемещение файла из области «только для чтения» в область чтения и записи сделает файл чтения и записи.  
  
 `CListCtrl`предоставляет несколько функций-членов для создания и управления рабочие области в элементе управления списка. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) и [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) получить и задать массив `CRect` объектов (или `RECT` структуры), который хранения текущей реализации рабочие области для элемента управления списка. Кроме того [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) получает текущее число рабочие области для элемента управления списка (по умолчанию, ноль).  
  
## <a name="items-and-working-areas"></a>Элементы и рабочих областей  
 При создании рабочей области элементов, которые находятся в пределах рабочей области, становятся членами его. Аналогичным образом Если элемент был перемещен в рабочей области, становится членом рабочей области, к которой он был перемещен. Если элемент не находится внутри любой рабочей области, он автоматически становится членом первая рабочая область (с индексом 0). Если вы хотите создать элемент и его размещения в определенной рабочей области, необходимо будет создать элемент и затем переместить его в нужное рабочую область с помощью вызова [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Во втором примере демонстрируется данный метод.  
  
 В следующем примере реализуется четыре рабочие области (`rcWorkAreas`), одинакового размера, с 10 пикселей всей границы вокруг каждого рабочую область в элементе управления списком (`m_WorkAreaListCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 Вызов [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) был сделан для оценки общей области, необходимые для отображения всех элементов в одном регионе. Эта оценка затем разделены на четыре области и заполняются 5 пикселей всей границы.  
  
 Следующий пример назначает существующих элементов списка для каждой группы (`rcWorkAreas`) и обновляет представление элемента управления (`m_WorkAreaListCtrl`) для завершения эффект.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>См. также  
 [Использование CListCtrl](../mfc/using-clistctrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)
