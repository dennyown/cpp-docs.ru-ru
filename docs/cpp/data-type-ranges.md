---
title: "Диапазоны типов данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af0601299046276c135571be2bac615df1571140
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-ranges"></a>Диапазоны типов данных
Компиляторы Visual C++ (32-разрядные и 64-разрядные) поддерживают типы, указанные в приведенной ниже таблице.  
  
-   `int` (`unsigned int`)  
  
-   `__int8` (`unsigned __int8`)  
  
-   `__int16` (`unsigned __int16`)  
  
-   `__int32` (`unsigned __int32`)  
  
-   `__int64` (`unsigned __int64`)  
  
-   `short` (`unsigned short`)  
  
-   `long` (`unsigned long`)  
  
-   `long` `long` (`unsigned long long`)  
  
 Если имя начинается с двух символов подчеркивания (`__`), тип данных является нестандартным.  
  
 Диапазоны, представленные в следующей таблице, включают указанные значения.  
  
|Имя типа|Байты|Другие имена|Диапазон значений|  
|---------------|-----------|-----------------|---------------------|  
|int|4|signed|От -2 147 483 648 до 2 147 483 647|  
|unsigned int|4|без знака|От 0 до 4 294 967 295|  
|__int8|1|char|От -128 до 127|  
|unsigned __int8|1|unsigned char|От 0 до 255|  
|__int16|2|короткое, короткое целочисленное, короткое целочисленное со знаком|От -32 768 до 32 767|  
|unsigned __int16|2|короткое без знака, короткое целочисленное без знака|От 0 до 65 535|  
|__int32|4|со знаком, целочисленное со знаком, целочисленное|От -2 147 483 648 до 2 147 483 647|  
|unsigned __int32|4|без знака, целочисленное без знака|От 0 до 4 294 967 295|  
|__int64|8|длинное длинное, со знаком длинное длинное|От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807|  
|unsigned __int64|8|без знака длинное длинное|От 0 до 18 446 744 073 709 551 615|  
|bool|1|Нет|false или true|  
|char|1|Нет|-128 до 127 по умолчанию<br /><br /> При компиляции при помощи [/J](../build/reference/j-default-char-type-is-unsigned.md)— от 0 до 255|  
|signed char|1|Нет|От -128 до 127|  
|unsigned char|1|Нет|От 0 до 255|  
|short|2|короткое целочисленное, короткое целочисленное со знаком|От -32 768 до 32 767|  
|unsigned short|2|короткое целочисленное число без знака|От 0 до 65 535|  
|long|4|длинное целочисленное, длинное целочисленное со знаком|От -2 147 483 648 до 2 147 483 647|  
|unsigned long|4|длинное целочисленное число без знака|От 0 до 4 294 967 295|  
|длинное длинное|8|Нет (но эквивалентно __int64)|От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807|  
|без знака длинное длинное|8|Нет (но эквивалентно unsigned__int64)|От 0 до 18 446 744 073 709 551 615|  
|enum|Возможны разные варианты|Нет| |  
|float|4|Нет|3,4E +/- 38 (7 знаков)|  
|double|8|Нет|1,7E +/- 308 (15 знаков)|  
|длинное двойное|То же, что и для двойного|Нет|То же, что и для двойного|  
|wchar_t|2|__wchar_t|От 0 до 65 535|  
  
 В зависимости от характера использования переменная типа `__wchar_t` обозначает расширенный символьный или многобайтовый символьный тип. Чтобы указать константу расширенного символьного типа, перед символьной или строковой константой следует использовать префикс `L` .  
  
 `signed` и `unsigned` — это модификаторы, которые можно использовать с любым целочисленным типом, кроме типа `bool`. Обратите внимание, что `char`, `signed char`и `unsigned char` — это три разных типа, предназначенных для механизмов, подобных перегрузке и шаблонам.  
  
 Размер типов `int` и `unsigned int` — 4 байта. Однако переносимый код не должен зависеть от размера `int` , поскольку языковой стандарт позволяет варьировать его в зависимости от реализации.  
  
 C и C++ в Visual Studio также поддерживают целочисленные типы с указанием размера. Дополнительные сведения см. в разделах [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) и [Пределы целых чисел](../cpp/integer-limits.md).  
  
 Дополнительные сведения об ограничениях, связанных с размером, каждого типа см. в статье [Фундаментальные типы](../cpp/fundamental-types-cpp.md).  
  
 Диапазон перечисляемых типов зависит от контекста языка и указанных флажков компилятора. Дополнительные сведения см. в статьях [Объявления перечислений C](../c-language/c-enumeration-declarations.md) и [Объявления перечислений C++](../cpp/enumerations-cpp.md).  
  
## <a name="see-also"></a>См. также  
 [Ключевые слова](../cpp/keywords-cpp.md)   
 [Базовые типы](../cpp/fundamental-types-cpp.md)