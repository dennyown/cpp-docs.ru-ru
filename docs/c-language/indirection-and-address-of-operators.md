---
title: "Операторы косвенного обращения и адреса операнда | Microsoft Docs"
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
  - "& - оператор, address-of - оператор"
  - "* - оператор"
  - "* - оператор, address-of - оператор"
  - "* - оператор, оператор косвенного обращения"
  - "адреса [C++]"
  - "адреса [C++], косвенное обращение"
  - "address-of - оператор (&)"
  - "оператор амперсанд (&)"
  - "оператор косвенного обращения"
  - "null - указатели [C++]"
  - "операторы [C++], address-of"
  - "операторы [C++], косвенное обращение"
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Операторы косвенного обращения и адреса операнда
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Оператор косвенного обращения \(**\***\) получает значение не напрямую, а через указатель.  Операнд должен быть указателем.  Результатом операции является значение в том адресе, на который указывает операнд.  Тип результата совпадает с типом значения в адресе операнда.  
  
 Если операнд указывает на функцию, результатом является указатель функции.  Если он указывает на место хранения, результатом является l\-значение, указывающее на место хранения.  
  
 Если значение указателя недопустимо, результат становится неопределенным.  Ниже приведены наиболее распространенные условия, при которых значение указателя становится недопустимым.  
  
-   Указатель является пустым указателем.  
  
-   Указатель определяет адрес локального элемента, не видимого во время обращения.  
  
-   Указатель определяет адрес, выравнивание которого не подходит для типа указываемого объекта.  
  
-   Указатель определяет адрес, который не используется выполняемой программой.  
  
 Оператор взятия адреса \(**&**\) предоставляет адрес своего операнда.  Операнд операции взятия адреса может быть либо указателем функции, либо l\-значением, указывающим на объект, который не является битовым полем и не объявлен со спецификатором класса хранения **register**.  
  
 Результатом операции взятия адреса является указатель на операнд.  Значение по адресу, который определяет указатель, совпадает со значением операнда.  
  
 Оператор взятия адреса может применяться только к переменным фундаментального типа или типа структуры или объединения, которые были объявлены в области видимости файла, а также к ссылкам на массив с индексом.  В таких выражениях из выражения взятия адреса можно вычитать \(или прибавлять к нему\) константное выражение, которое не содержит выражения взятия адреса.  
  
## Примеры  
 Такие объявления используются в следующих примерах:  
  
```  
int *pa, x;  
int a[20];  
double d;  
```  
  
 В следующей инструкции используется оператор взятия адреса:  
  
```  
pa = &a[5];  
```  
  
 Оператор взятия адреса \(**&**\) принимает адрес шестого элемента массива `a`.  Результат сохраняется в переменной указателя `pa`.  
  
```  
x = *pa;  
```  
  
 Оператор косвенного обращения \(**\***\) в этом примере обращается к значению `int`, которое находится по адресу, сохраненному в переменной `pa`.  Значение присваивается целочисленной переменной `x`.  
  
```  
if( x == *&x )  
    printf( "True\n" );  
```  
  
 В этом примере выводится слово `True`. Это означает, что оператор косвенного обращения, примененный к адресу `x` дает результат, равный значению `x`.  
  
```  
int roundup( void );     /* Function declaration */  
  
int  *proundup  = roundup;  
int  *pround  = &roundup;  
```  
  
 После объявления функции `roundup` объявляются и инициализируются два указателя на `roundup`.  При инициализации первого из них, `proundup`, указывается только имя функции, а для второго, `pround`, используется оператор взятия адреса.  Обе инициализации эквивалентны.  
  
## См. также  
 [Оператор косвенного обращения: \*](../cpp/indirection-operator-star.md)   
 [Оператор address\-of: &](../cpp/address-of-operator-amp.md)