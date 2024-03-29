---
title: "Отправка и получение сообщений | Документы Microsoft"
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
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c587e3b84ae7afd7869a5c1405d8ddc4ab417b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="message-sending-and-receiving"></a>Отправка и получение сообщений
Рассмотрите возможность отправки частью процесса и реакция платформу.  
  
 Большинство сообщений в результате взаимодействия пользователя с программой. Команды создаются щелчки мышью в пункты меню или кнопок панели инструментов или сочетания клавиш. Пользователь также приводит к возникновению ошибки сообщения Windows, например, перемещении или изменении размера окна. Другие Windows сообщения отправляются при возникновении события, такие как запуск программы или завершения, как windows получить или потеряет фокус и т. д. Уведомление элемента управления сообщения создаются щелчки мыши или другие варианты взаимодействия пользователя с элементом управления, таких как кнопки или списка элемент управления в диалоговом окне.  
  
 **Запуска** функции-члена класса `CWinApp` получает сообщения и перенаправляет его в соответствующее окно. Большинство команд сообщения отправляются фрейма главного окна приложения. `WindowProc` Предопределенную возвращает библиотеки классов сообщений и направляет их по-разному, в зависимости от категории полученного сообщения.  
  
 Теперь рассмотрим принимающей часть процесса.  
  
 Начальный получатель сообщения должен быть объектом окна. Сообщения Windows обычно обрабатываются непосредственно, объект окна. Команда сообщения, обычно возникают в окне главного фрейма приложения будут перенаправляться цепочки целевой объект команды, описанной в [маршрутизация команд](../mfc/command-routing.md).  
  
 Каждый объект может принимать сообщения или команды имеет свое собственное сообщение сопоставление этой пары сообщений или команды с именем его обработчик.  
  
 Если целевой объект команды получает сообщение или команды, схему сообщений, поиск совпадения. При обнаружении обработчик для сообщения, он вызывает обработчик. Дополнительные сведения о том, как производится поиск схемы сообщений см. в разделе [как Framework поиск схемы сообщений](../mfc/how-the-framework-searches-message-maps.md). Повторно обратитесь к рисунку [команды в Framework](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>См. также  
 [Вызовы обработчика со стороны платформы](../mfc/how-the-framework-calls-a-handler.md)

