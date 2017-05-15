---
title: "Добавление потребителя OLE DB библиотеки ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "потребитель OLE DB библиотеки ATL"
  - "проекты ATL, добавление потребителей ATL OLE DB"
  - "OLE DB, добавление потребителей ATL OLE DB в проект"
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Добавление потребителя OLE DB библиотеки ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Этот мастер используется для добавления в проект потребителя OLE DB библиотеки ATL.  Потребитель OLE DB библиотеки ATL состоит из класса метода доступа к OLE DB и привязок данных, необходимых для доступа к источнику данных.  Проект должен быть создан как COM\-приложение библиотеки ATL или как приложение MFC или Win32, содержащее поддержку ATL \(которую мастер потребителей OLE DB библиотеки ATL добавляет автоматически\).  
  
 **Примечание**  Можно добавить объект\-получатель OLE DB в проект MFC.  Если это сделано, мастер потребителей ATL OLE DB добавляет в проект необходимую поддержку COM.  При этом предполагается, что при создании проекта MFC был установлен флажок **Элементы управления ActiveX** \(на странице **Дополнительные возможности** мастера приложений проекта MFC\), который по умолчанию установлен.  Установка этого флажка гарантирует, что приложение вызывает **CoInitialize** и **CoUninitialize**.  Если же флажок **Элементы управления ActiveX** не был установлен при создании проекта MFC, вызов **CoInitialize** и **CoUninitialize** необходимо организовать в своем собственном коде.  
  
### Добавление в проект потребителя OLE DB ATL  
  
1.  Щелкните проект правой кнопкой мыши в окне классов.  В контекстном меню выберите команду **Добавить**, а затем выберите **Добавить класс**.  
  
2.  В папке Visual C\+\+ дважды щелкните значок **Потребитель OLE DB ATL** или выделите его и нажмите кнопку **Открыть**.  
  
     Откроется мастер потребителей ATL OLE DB.  
  
3.  Задайте параметры, как указано в [мастере потребителей ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).  
  
4.  Нажмите кнопку **Готово**, чтобы завершить работу мастера.  Вновь созданный код потребителя OLE DB будет вставлен в проект.  
  
## См. также  
 [Добавление функциональных возможностей с помощью мастеров кода](../../ide/adding-functionality-with-code-wizards-cpp.md)