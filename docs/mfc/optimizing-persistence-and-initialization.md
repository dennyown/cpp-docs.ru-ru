---
title: "Оптимизация постоянства и инициализации | Microsoft Docs"
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
  - "MFC ActiveX - элементы управления, оптимизация"
  - "оптимизация, элементы управления ActiveX"
  - "оптимизация производительности, элементы управления ActiveX"
  - "производительность, элементы управления ActiveX"
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Оптимизация постоянства и инициализации
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

По умолчанию сохранение и инициализация в элементе управления обрабатываются функцией\-членом `DoPropExchange`.  В типичном элементе управления, эта функция содержит вызовы несколько функций **PX\_** \(`PX_Color`, `PX_Font` и т д\), по одному для каждого свойства.  
  
 Данный подход имеет то преимущество, что одной реализации `DoPropExchange` можно использовать для инициализации, для сохранения в бинарном формате и для сохранения в формате, называемом «свойств контейнера» используется несколькими контейнерами.  Эта одной функции содержатся все сведения о свойствах и их значения по умолчанию в любом удобном месте.  
  
 Однако эта обобщения поступает это сделает эффективности.  Функции **PX\_** получают их гибкость по многоуровневые реализации, является менее эффективны, чем более непосредственно, но менее гибким, подходы.  Кроме того, если элемент управления передает значение по умолчанию для функции **PX\_**, то значение по умолчанию необходимо предоставить каждый раз, даже в случае, когда значение по умолчанию не обязательно может использоваться.  Если создание значение по умолчанию нетривиальная задача \(например, когда значение извлекается из внешнего свойства\), а кроме того, лишняя работа выполняется в случаях, когда значение по умолчанию не используется.  
  
 Можно увеличить производительность сохранения элемента управления бинарную путем переопределения функция `Serialize` элемента управления.  Реализация по умолчанию этого функции\-члена вызовет функцию `DoPropExchange`.  Можно переопределить это, можно задать более непосредственно реализацию бинарного сохранения.  Например, рассмотрим эту функцию `DoPropExchange`:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_1.cpp)]  
  
 Для повышения производительности сохранения этого элемента управления бинарного можно переопределить функцию `Serialize` следующим образом:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_2.cpp)]  
  
 Локальную переменную `dwVersion` можно использовать для определения версии сохраненного состояния элемента управления, загружаемая постоянного или.  Можно использовать эту переменную вместо вызова [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md).  
  
 Чтобы сохранить немного места в постоянном формате для свойства **bool** \(и сохранить его совместимым с форматом, `PX_Bool`\) можно магазин как свойство **byte** следующим образом:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_3.cpp)]  
  
 Обратите внимание, что в грузовом контейнере, используется временная переменная затем ее присвоено значение, а не приведет `m_boolProp` в ссылке **byte**.  Метод приведения привело бы к только одним байтом, изменяющего `m_boolProp`, и остальные байты не инициализируется.  
  
 Для одного элемента управления можно оптимизировать инициализация элемента управления путем переопределения [COleControl::OnResetState](../Topic/COleControl::OnResetState.md) следующим образом:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_4.cpp)]  
  
 Хотя `Serialize` и `OnResetState` были переопределены, функция `DoPropExchange` должна быть сдержана неповрежденной, поскольку она по\-прежнему используется для сохранения в формате свойств контейнера.  Необходимо поддерживать все 3 из этих функций, чтобы гарантировать, что элемент управления находится в его свойства последовательно, независимо от выбранной механизм сохранения использует контейнер.  
  
## См. также  
 [Элементы управления ActiveX в MFC. Оптимизация](../mfc/mfc-activex-controls-optimization.md)