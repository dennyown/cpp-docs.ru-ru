---
title: "_com_error::Error | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a318ba69fe5e5d19bacb6d5890889d31a5a44d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorerror"></a>_com_error::Error
**Блок, относящийся только к системам Microsoft**  
  
 Получает элемент `HRESULT`, переданный конструктору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Необработанный элемент `HRESULT`, переданный в конструктор.  
  
## <a name="remarks"></a>Примечания  
 Получает инкапсулированный элемент `HRESULT` в объекте `_com_error`.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Класс _com_error](../cpp/com-error-class.md)