---
title: "Функции to | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
dev_langs:
- C++
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef97b5e5ab2c21b375814cf117d6155b4a502795
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="to-functions"></a>Функции to
Каждая из функций **to** и связанный с ней макрос, если таковой имеется, преобразуют один символ в другой.  
  
|||  
|-|-|  
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## <a name="remarks"></a>Примечания  
 Функции **to** и макросы преобразования выглядят следующим образом.  
  
|Подпрограмма|Макрос|Описание:|  
|-------------|-----------|-----------------|  
|`__toascii`|`__toascii`|Преобразует `c` в ASCII символ|  
|`tolower`|`tolower`|Преобразует `c` в нижний регистр при необходимости|  
|`_tolower`|`_tolower`|Преобразует `c` в нижний регистр|  
|`towlower`|Нет|Преобразует `c` в соответствующую букву, представленную расширенным символом нижнего регистра|  
|`toupper`|`toupper`|Преобразует `c` в верхний регистр при необходимости|  
|`_toupper`|`_toupper`|Преобразует `c` в верхний регистр|  
|`towupper`|Нет|Преобразует c в соответствующую букву, представленную расширенным символом нижнего регистра|  
  
 Чтобы использовать функциональные версии подпрограмм **to**, которые также определены как макросы, либо удалите определения макросов с помощью директив `#undef`, либо не включайте CTYPE.H. Если используется параметр компилятора /Za, то компилятор использует функциональную версию `toupper` или `tolower`. Объявления функций `toupper` и `tolower` находятся в STDLIB.H.  
  
 Подпрограмма `__toascii` устанавливает все, кроме младших 7 бит `c`, в 0, поэтому преобразованное значение представляет символ в кодировке ASCII. Если `c` уже представляет символ ASCII, `c` не изменяется.  
  
 Подпрограммы `tolower` и `toupper`:  
  
-   зависят от категории `LC_CTYPE` текущего языкового стандарта (`tolower` вызывает `isupper` и `toupper` вызывает `islower`);  
  
-   преобразовывают `c`, если `c` представляет пригодную для преобразования букву соответствующего регистра текущего языкового стандарта и если существует обратный регистр для данного языкового стандарта. В противном случае `c` не изменяется.  
  
 Подпрограммы `_tolower` и `_toupper`:  
  
-   представляют собой не зависящие от языкового стандарта, намного более быстрые версии `tolower` и **toupper**.  
  
-   Могут использоваться только когда **isascii(**`c`**)** и either **isupper(**`c`**)** или **islower(**`c`**)**, соответственно, отличны от нуля.  
  
-   имеют неопределенные результаты, если `c` не является буквой ASCII соответствующего регистра для преобразования;  
  
 Функции `towlower` и `towupper` возвращают преобразованную копию `c` только в том случае, если выполняются оба приведенных ниже условия. В противном случае `c` не изменяется.  
  
-   `c` является расширенным символом соответствующего регистра (т. е. для которого `iswupper` или **iswlower**, соответственно, не равны нулю).  
  
-   Существует соответствующий расширенный символ нужного регистра (т. е. для которого `iswlower` или **iswupper**, соответственно, не равны нулю).  
  
## <a name="example"></a>Пример  
  
```  
// crt_toupper.c  
/* This program uses toupper and tolower to  
 * analyze all characters between 0x0 and 0x7F. It also  
 * applies _toupper and _tolower to any code in this  
 * range for which these functions make sense.  
 */  
  
#include <ctype.h>  
#include <string.h>  
  
char msg[] = "Some of THESE letters are Capitals.";  
char *p;  
  
int main( void )  
{  
   printf( "%s\n", msg );  
  
   /* Reverse case of message. */  
   for( p = msg; p < msg + strlen( msg ); p++ )  
   {  
      if( islower( *p ) )  
         putchar( _toupper( *p ) );  
      else if( isupper( *p ) )  
         putchar( _tolower( *p ) );  
      else  
         putchar( *p );  
   }  
}  
```  
  
```Output  
Some of THESE letters are Capitals.  
sOME OF these LETTERS ARE cAPITALS.  
```  
  
## <a name="see-also"></a>См. также  
 [Преобразование данных](../c-runtime-library/data-conversion.md)   
 [Языковой стандарт](../c-runtime-library/locale.md)   
 [Подпрограммы is, isw](../c-runtime-library/is-isw-routines.md)