---
title: "Серверы. Элементы сервера | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "архитектура [C++], server-item"
  - "приложения сервера OLE, элементы сервера"
  - "элементы сервера"
  - "элементы сервера, реализация"
  - "серверы [C++], элементы сервера"
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Серверы. Элементы сервера
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Когда контейнер запущен сервер, чтобы пользователь мог изменять внедренный или связанное элемент OLE, серверное приложение создает элемент сервера «.» Элемент сервера, который является объектом, производном от класса `COleServerItem`, предоставляет интерфейс между серверным документом и из приложения контейнера.  
  
 Класс `COleServerItem` определяет несколько функции\-члены переопределяемого метода, которые называются OLE, обычно в ответ на запросы из контейнера.  Серверные элементы могут представлять часть серверного документа или весь документ.  Если элемент OLE внедряется в документе контейнера, элемент сервера представляет все серверные документ.  Если элемент OLE связанного сервера, элемент может представлять часть серверного документа или документа целиком, в зависимости от того, является ли ссылка на части или к целому.  
  
 В примере [HIERSVR](../top/visual-cpp-samples.md), например классе сервера элемента, **CServerItem** содержит член, указатель на объект класса **CServerNode**.  Объект **CServerNode** узел в документе приложения HIERSVR, дерево.  Когда объект **CServerNode** корневой узел, объект **CServerItem** представляет документ целиком.  Когда объект **CServerNode** дочерний узел, объект **CServerItem** представляет часть документа.  В примере MFC [HIERSVR](../top/visual-cpp-samples.md) OLE для этого примера взаимодействия.  
  
##  <a name="_core_implementing_server_items"></a> Реализация серверные  
 При использовании мастера приложений для создания кода «стартера» для приложения, то все, что нужно сделать, чтобы включить элементы сервера в стартере код выбрать один из параметров сервера из OLE страницы параметров.  При добавлении элементов сервера в существующее приложение, выполните следующие действия.  
  
#### Предоставить элемент сервера  
  
1.  Наследование класса от класса `COleServerItem`.  
  
2.  В производном классе, переопределить функцию\-член `OnDraw`.  
  
     Платформа вызывает `OnDraw` для отображения элемент OLE в метафайл.  Контейнерное приложение использует этот метафайл, чтобы отобразить элемент.  Класс представления приложения также содержит функцию\-член `OnDraw`, который используется для отображения элемента при серверное приложение активно.  
  
3.  Реализуйте переопределение `OnGetEmbeddedItem` класса серверного документа.  Дополнительные сведения см. в статье [Серверы: Реализация серверные документы](../mfc/servers-implementing-server-documents.md) и в примере MFC [HIERSVR](../top/visual-cpp-samples.md) OLE.  
  
4.  Реализуйте функции\-члена `OnGetExtent` класса сервера элемента.  Платформа вызывает данную функцию, чтобы получить размер элемента.  Реализация по умолчанию не выполняет никаких действий.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Подсказка для архитектуры сервера элемента  
 Как отмечалось в [Реализация серверные](#_core_implementing_server_items), серверные приложения должны иметь возможность обрабатывать элементы находятся в представлении сервера и в метафайле " из приложения контейнера.  В архитектуре приложения библиотеки Microsoft Foundation Class, функцию\-член `OnDraw` класса представления отображает элемент при его редактирования \(см. в разделе [CView::OnDraw](../Topic/CView::OnDraw.md) в *справочнике библиотеки классов*\).  `OnDraw` элемента сервера отображает элемент в метафайл во всех остальных случаях \(см. раздел [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)\).  
  
 Чтобы избежать дублирования кода, используя вспомогательные функции в классе серверного документа и вызывать их из функций `OnDraw` классы по в представлении и сервера элементом.  В примере MFC [HIERSVR](../top/visual-cpp-samples.md) OLE использует эту стратегию: функции **CServerView::OnDraw** и **CServerItem::OnDraw** вызывают **CServerDoc::DrawTree** и для отображения элемента.  
  
 Представление и элемент имеют функции\-члены `OnDraw`, поскольку они котором демонстрируется рисование в различных условиях.  Представление должно учитывать такие факторы, как увеличить размер и масштаб выделения, обрезка и элементы пользовательского интерфейса, такие как полосы прокрутки.  Элемент сервера, с другой стороны, всегда рисуется весь объект OLE.  
  
 Дополнительные сведения см. в разделе [CView::OnDraw](../Topic/CView::OnDraw.md), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md) и [COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) справочника *по библиотеке классов*.  
  
## См. также  
 [Серверы](../mfc/servers.md)