---
title: "Метод WeakRef::AsIID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID - метод"
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод WeakRef::AsIID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Задает определенный указатель ComPtr для представления идентификатора указанного интерфейса.  
  
## Синтаксис  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### Параметры  
 `riid`  
 Идентификатор интерфейса.  
  
 `ptr`  
 Когда эта операция завершается, объект, представляющий параметр `riid`.  
  
## Возвращаемое значение  
  
-   Значение S\_OK, если операция завершилась успешно; в противном случае — значение HRESULT, указывающее на причину неудачного завершения операции, а `ptr` устанавливается в значение `nullptr`.  
  
-   Значение S\_ОК, если операция завершилась успешно, но текущий объект WeakRef уже был выпущен. Параметр `ptr` устанавливается в значение `nullptr`.  
  
-   Значение S\_OK, если операция завершилась успешно, но текущий объект WeakRef не получен из параметра `riid`. Параметр `ptr` устанавливается в значение `nullptr`. \(Дополнительные сведения см. в разделе "Примечания".\)  
  
## Примечания  
 Ошибка создается, если параметр `riid` не получен из IInspectable. Эта ошибка заменяет возвращаемое значение.  
  
 Первый шаблон — это форма, которую необходимо использовать в коде. Второй шаблон \(не показанный здесь, но объявленный в файле заголовка\) является внутренней вспомогательной специализацией, которая поддерживает функции языка C\+\+, например ключевое слово выведения типа [auto](../cpp/auto-cpp.md).  
  
 Начиная с пакета SDK для Windows 10 этот метод не устанавливает экземпляр WeakRef в значение `nullptr`, если не удалось получить слабую ссылку, поэтому следует избегать использования кода проверки ошибок, который проверяет наличие `nullptr` для WeakRef. Вместо этого проверьте возвращенное значение HRESULT, чтобы узнать, успешно ли выполнен метод, или проверьте `ptr` на наличие `nullptr`.  
  
## Требования  
 **Заголовок:** client.h  
  
 **Пространство имен:** Microsoft::WRL  
  
## См. также  
 [Класс WeakRef](../windows/weakref-class.md)