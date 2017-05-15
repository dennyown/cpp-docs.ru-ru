---
title: "Преимущества использования DLLs | Microsoft Docs"
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
  - "DLL-библиотеки [C++], преимущества"
  - "динамическая компоновка [C++]"
  - "динамическая загрузка - связывание [C++]"
  - "связывание [C++], динамическое или статическое"
  - "ссылки [C++], динамическое или статическое"
ms.assetid: 8956c8ee-e7b3-446f-a0c6-462381747690
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Преимущества использования DLLs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Динамическая компоновка имеет следующие преимущества:  
  
-   Экономия памяти и уменьшение объема выгрузки.  Многие процессы используют одновременно одну библиотеку DLL — при этом в памяти хранится только один ее экземпляр для всех процессов.  Для каждого приложения, построенного с помощью статически компонуемой библиотеки, Windows, напротив, должна загрузить копию кода библиотеки в память.  
  
-   Экономия места на диске.  Многие приложения совместно используют одну копию библиотеки DLL на диске.  В каждом приложении, построенном на основе статически компонуемой библиотеки, код библиотеки, напротив, компонуется в исполняемый образ в виде отдельной копии.  
  
-   Обновление библиотек DLL проще и удобнее.  При изменении функций в библиотеке DLL не требуется перекомпиляция или перекомпоновка приложений, использующих эти библиотеки, если аргументы функций и возвращаемые значения остались прежними.  Напротив, при использовании статически компонуемого объектного кода требуется перекомпоновка приложения в случае изменения функций.  
  
-   Обеспечивается послепродажная поддержка.  Например, в библиотеку DLL для драйвера монитора можно внести изменения для поддержки монитора другого типа, которого еще не существовало на момент поставки приложения.  
  
-   Поддержка многоязычных программ.  Программы, написанные на разных языках программирования, могут вызывать ту же самую функцию библиотеки DLL, если в этих программах соблюдаются единые соглашения по вызовам функций.  Между программой и функцией библиотеки DLL должна быть обеспечена совместимость по следующим направлениям: определить последовательность передачи аргументов функции в стек, а также определить, какая часть отвечает за очистку стека — функция или приложение, а также какие аргументы передаются в регистры.  
  
-   Механизм расширения классов библиотеки MFC.  На основе существующих классов MFC можно создавать производные классы и помещать их в библиотеку DLL расширения MFC для использования в приложениях MFC.  
  
-   Упрощение создания международных версий приложений.  Создание международных версий приложений намного упрощается, если строковые ресурсы поместить в библиотеку DLL.  Можно разместить строковые ресурсы каждой языковой версии вашего приложения в отдельную библиотеку ресурсов, чтобы разные языковые версии загружали соответствующие ресурсы.  
  
 Потенциальный недостаток использования библиотек DLL состоит в том, что приложение не является самодостаточным: его выполнение определяется наличием того или иного библиотечного модуля DLL.  
  
## Выберите действие.  
  
-   [Экспорт из DLL](../build/exporting-from-a-dll.md)  
  
-   [Привязка исполняемого файла к библиотеке DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [Инициализацию DLL](../build/initializing-a-dll.md)  
  
## Дополнительные сведения  
  
-   [Общие сведения о библиотеках DLL, не являющихся MFC](../Topic/Non-MFC%20DLLs:%20Overview.md)  
  
-   [Обычные библиотеки DLL, статически компонуемые с MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Обычные библиотеки DLL, динамически компонуемые с MFC](../Topic/Regular%20DLLs%20Dynamically%20Linked%20to%20MFC.md)  
  
-   [Общие сведения о библиотеках \(DLL\) расширения](../build/extension-dlls-overview.md)  
  
## См. также  
 [DLL в Visual C\+\+](../build/dlls-in-visual-cpp.md)