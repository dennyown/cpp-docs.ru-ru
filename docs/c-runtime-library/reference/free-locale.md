---
title: "_free_locale | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _free_locale
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c3582f51b4a66f33cf0926b12cbeccfc1f621c48
ms.contentlocale: ru-ru
ms.lasthandoff: 03/30/2017

---
# <a name="freelocale"></a>_free_locale
Освобождает объект языкового стандарта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `locale`  
 Объект языкового стандарта, который необходимо освободить.  
  
## <a name="remarks"></a>Примечания  
 Функция `_free_locale` используется, чтобы освободить объект языкового стандарта, полученный из вызова функции `_get_current_locale` или `_create_locale`.  
  
 Предыдущее название данной функции `__free_locale` (с 2 символами подчеркивания в начале) использовать не рекомендуется.  
  
## <a name="requirements"></a>Требования  
  
|`Routine`|Обязательный заголовок|  
|---------------|---------------------|  
|`_free_locale`|\<locale.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="see-also"></a>См. также  
 [_get_current_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)