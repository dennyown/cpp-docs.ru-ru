---
title: "_flushall | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 230d52cf98e7dc563ea5d0067de7df31af8549f9
ms.contentlocale: ru-ru
ms.lasthandoff: 03/30/2017

---
# <a name="flushall"></a>_flushall
Сбрасывает все потоки; очищает все буферы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
int _flushall( void );  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 `_flushall` возвращает число открытых потоков (ввода и вывода). Ошибка не возвращается.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию функция `_flushall` записывает в соответствующие файлы содержимое всех буферов, связанных с открытыми потоками вывода. Все буферы, связанные с открытыми входными потоками, очищаются. (Эти буферы обычно обслуживаются операционной системой, которая автоматически определяет оптимальное время записи данных на диск: при заполнении буфера, при закрытии потока или при нормальном завершении программы без закрытия потоков).  
  
 Если после вызова функции `_flushall` выполняется операция чтения, из входных файлов в буферы считываются новые данные. После вызова функции `_flushall` все потоки остаются открытыми.  
  
 Предусмотренная в библиотеке времени выполнения функция фиксации на диск позволяет обеспечить запись критически важных данных непосредственно на диск, а не в буферы операционной системы. Эту функцию можно включить, не переписывая программу, а скомпоновав объектные файлы программы с файлом Commode.obj. В создаваемом исполняемом файле вызовы функции `_flushall` записывают содержимое всех буферов на диск. Файл Commode.obj влияет только на функции `_flushall` и `fflush`.  
  
 Дополнительные сведения об управлении возможностью фиксации на диск см. в разделах [Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md), [fopen](../../c-runtime-library/reference/fopen-wfopen.md) и [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
## <a name="requirements"></a>Требования  
  
|Функция|Обязательный заголовок|  
|--------------|---------------------|  
|`_flushall`|\<stdio.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="example"></a>Пример  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
```Output  
There were 3 streams flushed  
```  
  
## <a name="see-also"></a>См. также  
 [Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)   
 [_commit](../../c-runtime-library/reference/commit.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)