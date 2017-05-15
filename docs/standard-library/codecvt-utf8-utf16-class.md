---
title: "codecvt_utf8_utf16 | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt_utf8_utf16
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: e628eb145b52cd3ab9b1e36770363c34099c6cb4
ms.lasthandoff: 02/24/2017

---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16
Представляет аспект [языкового стандарта](../standard-library/locale-class.md), который выполняет преобразование между расширенными символами в кодировке UTF-16 и потоком байтов в кодировке UTF-8.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Параметры

`Elem`  
Тип двухбайтового элемента.  
`Maxcode`  
Максимальное количество символов для аспекта языкового стандарта.  
`Mode`  
Сведения о конфигурации для аспекта языкового стандарта.  

## <a name="remarks"></a>Примечания

Поток байтов может записываться в двоичный файл или текстовый файл.  

## <a name="requirements"></a>Требования

Заголовок: <codecvt> Пространство имен: std
