---
title: "Общие сведения о программировании на C++ в Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Общие сведения о программировании на C++ в Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ можно использовать для создания самых разнообразных программ, выполняемых на ПК Windows \(x86, x64 или ARM\), на сервере Windows, в облаке или на Xbox. Грамотно сконструированные программы C\+\+ быстры, эффективны, энергоэкономичны и могут в полной мере использовать преимущества мультиядерных и многоядерных устройств, общие вычислительные ресурсы графических процессоров \(GPGPU\) и другие преимущества современного оборудования.  
  
 Visual C\+\+ позволяет разрабатывать приложения Windows ряда общих категорий. Эти категории имеют различные модели программирования \(или модели приложений\), а значит, используют различные библиотеки и API, которые обеспечивают доступ к платформе и предоставляют пользовательский интерфейс.  
  
-   [Универсальные приложения Windows](#BK_WindowsUniversal) Третья категория приложений Windows впервые появилась в Windows 8 и продолжает поддерживаться в Windows 10. К таким приложениям, которые часто называют просто "приложениями Windows", относятся настольные и мобильные приложения, предназначенные для различных устройств. Подобные приложения можно писать на C\+\+\/ CX, диалекте языка C\+\+, который поддерживает разработку в среде выполнения Windows, или на стандартном языке C\+\+ с использованием COM и библиотеки среды выполнения Windows \(WRL\). Изначально такие приложения предназначались для отображения на весь экран, однако в Windows 10 появилась возможность запускать подобные приложения как окно на рабочем столе. Приложения рассчитаны на управление с помощью сенсорного экрана, однако в его отсутствие, а также если пользователи предпочитают пользоваться мышью, поддерживают также управление с помощью мыши. Эти приложения распространяются через магазин Windows, в связи с чем получили название "приложений для магазина Windows".  
  
-   [Приложения и игры для настольного компьютера, сервера и облака](#BK_Native). В эту категорию входят приложения для настольных компьютеров Windows. Они используют API Win32, поэтому их также называют приложениями Win32. До выхода Windows 8 к этой категории относились все приложения Windows. Для реализации пользовательского интерфейса в приложениях этой категории может использоваться MFC, а взаимодействия с компонентами Windows \(которые обычно являются объектами COM\) — ATL.  
  
     К этой категории относятся также приложения, компоненты и библиотеки, написанные на стандартном языке C\+\+.  
  
     В эту категорию также входит применение C\+\+ для основных компонентов и вычислительного кода в контексте программирования серверных и облачных приложений. Иногда для повышения производительности на языке C\+\+ пишется ресурсоемкий код в основной части серверного или облачного приложения. Такой код можно скомпилировать в файл DLL и реализовать через C\# или Visual Basic.  
  
-   **Приложения .NET Framework**. Большинство приложений .NET Framework пишется на языке C\# или Visual Basic, но может использоваться и C\+\+\/CLI \(параметр компилятора \/CLR в Visual C\+\+\). Мы рекомендуем использовать C\+\+\/CLI для разработки минимального уровня взаимодействия в рамках более крупного приложения, которое включает управляемый и машинный код.  
  
##  <a name="BK_WindowsUniversal"></a> Универсальные приложения Windows  
 Windows 10 позволяет запускать приложения как на настольных компьютерах, так и на любых устройствах Windows 10, включая планшеты и мобильные телефоны. Теперь приложения способны запускаться не только на весь экран, но и как окна на рабочем столе. Такие приложения будут также работать на Xbox и дальнейших устройствах.  Эти два типа приложений программируются не так, как настольные приложения Win32. Такие приложения Windows запускаются в среде выполнения Windows, которая предоставляет элементы пользовательского интерфейса, необходимые службы для этих приложений, а также интерфейс для различных поддерживаемых устройств. Приложения компилируются в машинный код и обладают пользовательским интерфейсом XAML или используют DirectX. Компоненты [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] можно также писать на машинном коде, доступном для других приложений Windows, в том числе написанных на языках C\#, Visual Basic или JavaScript. Дополнительные сведения см. в разделах [Создание первого приложения для Магазина Windows на C\+\+](http://go.microsoft.com/fwlink/?LinkID=534976), [Создание первой игры для Магазина Windows с поддержкой DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656) и [Создание компонентов среды выполнения Windows в C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=244658).  
  
 Примеры для универсальной платформы Windows см. в разделе [примеров универсальных приложений для Windows на сайте GitHub](https://github.com/Microsoft/Windows-universal-samples).  
  
 Инструкции по переносу проекта на базе Windows 8.1 в Windows 10 см. в статье [Перенос на универсальную платформу Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). При наличии существующих классических библиотек Win32 и кода, который нужно интегрировать в приложение UWP, см. раздел [Практическое руководство. Использование существующего кода C\+\+ в приложении универсальной платформы Windows](../Topic/How%20to:%20Use%20Existing%20C++%20Code%20in%20a%20Universal%20Windows%20Platform%20App.md).  
  
 Универсальные приложения, игры и компоненты Windows также можно создавать без применения [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../Token/cppwrt_short_md.md)]\); в качестве альтернативы можно использовать [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\). Дополнительные сведения см. в разделе [Библиотека шаблонов C\+\+ среды выполнения Windows \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] позволяет разрабатывать универсальные приложения Windows, которые работают и на компьютерах, и на мобильных устройствах Windows 10. В [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] можно также разрабатывать приложения для Windows 8.1 и Windows Phone 8.1, но для этого необходимо установить на компьютер Visual Studio 2013 и настроить проект на использование набора инструментов **Visual Studio 2013 \(v120\)**. Чтобы настроить этот параметр в проекте, откройте свойства проекта и в разделе **Общие** установите для свойства **Набор инструментов платформы** значение **Visual Studio 2013 \(v120\)**.  
  
 Установив в программе установки Visual Studio средства Phone 8.0, можно также работать с Windows Phone 8.0.  
  
 В Windows 10 была представлена новая концепция под названием "Контракты API", которая заменила существовавшую ранее практику разработки под конкретные версии Windows. Вместо этого можно выбрать необходимые для приложения контракты API, и оно будет запускаться на любом устройстве Windows, которое поддерживает эти контракты. Контракт API — это набор стабильных API, которые предоставляют доступ к ресурсам платформы или устройства. Контракты API могут быть включены в систему проектов в виде ссылок. При добавлении ссылки на определенный пакет SDK расширения в проекте Visual Studio программа добавляет соответствующие контракты API.  
  
 Дополнительные сведения об этих концепциях см. в [руководстве по универсальным приложениям Windows](http://go.microsoft.com/fwlink/?LinkId=534605).  
  
##  <a name="BK_Win32"></a> Приложения и игры для настольного компьютера, сервера и облака  
 В облаке можно создавать сборки машинного кода Azure на языке C\+\+ и обращаться к ним из веб\-ролей, созданных в C\#. Дополнительные сведения см. в описании [пакета Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416).  
  
 Основы создания клиентских приложений Windows для настольного компьютера см. в разделах [Developing Windows Applications in C\+\+](http://msdn.microsoft.com/vstudio//hh304489) \(Разработка приложений для Windows на языке C\+\+\) и [Introduction to Windows Programming in C\+\+](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx) \(Введение в программирование для Windows на языке C\+\+\).  
  
 В Windows 10 с помощью Visual C\+\+ можно создавать различные типы программ:  
  
-   Приложения и служебные программы для командной строки. Дополнительные сведения см. в разделе [Консольные приложения](../Topic/Console%20Applications%20in%20Visual%20C++.md).  
  
-   Игры DirectX, выполняемые на ПК или Xbox. Дополнительные сведения см. в [центре разработчика DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).  
  
-   Потребительские приложения со сложным графическим интерфейсом пользователя. Дополнительную информацию см. в статье [Hilo: разработка приложений C\+\+ для Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417).  
  
-   Корпоративные приложения и бизнес\-приложения, выполняемые в среде .NET Framework или используемые для связи между приложениями .NET Framework и приложениями или компонентами, состоящими из машинного кода. Для получения дополнительной информации см. [программирование .NET с использованием C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
-   Клиенты базы данных SQL, которые выполняются на машинном коде. Дополнительные сведения см. в разделе [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419).  
  
-   Надстройки для приложений Microsoft Office. Дополнительные сведения см. в разделе [Создание надстройки C\+\+ для Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420).  
  
-   Драйверы устройств. Дополнительные сведения см. в разделе [Windows Driver Kit \(WDK\)](http://go.microsoft.com/fwlink/p/?LinkId=256421) \(Комплект разработки драйверов для Windows \(WDK\)\).  
  
-   службы Windows; Для получения дополнительной информации см. [Introduction to Windows Service Applications](../Topic/Introduction%20to%20Windows%20Service%20Applications.md).  
  
 С помощью Visual C\+\+ практически любые высокопроизводительные функции для Win32 можно упаковать в файлы DLL или COM DLL, пригодные дл использования в приложениях C\+\+ или в приложениях, написанных на других языках \(например, C\# или Visual Basic\). Дополнительные сведения о DLL для Win32 см. в разделе [DLL в Visual C\+\+](../build/dlls-in-visual-cpp.md). Дополнительные сведения о разработке COM в разделе [Component Object Model \(COM\)](http://msdn.microsoft.com/ru-ru/375d29a7-a1f3-4bd8-8621-bad7a049b2aa).  
  
## SDK и файлы заголовков  
 Visual C\+\+ включает стандартные библиотеки C и C\+\+, библиотеку стандартных шаблонов \(STL\) и другие библиотеки Microsoft. Папки включения, содержащие файлы заголовков для этих библиотек, находятся либо в каталоге установки Visual Studio в папке \\VC\\, либо, если речь идет о библиотеке времени выполнения C \(CRT\), в папке установки пакета Windows SDK, например, Kits\\10 Windows в папке Program Files для пакета SDK Windows 10.  Библиотеки Microsoft:  
  
-   Microsoft Foundation Classes \(MFC\): объектно\-ориентированная платформа для создания традиционных программ Windows \(в частности, корпоративных приложений\), со сложным пользовательским интерфейсом, включающим кнопки, поля списков, древовидные структуры и другие элементы управления. Дополнительные сведения см. в разделе [Приложения MFC для рабочего стола](../mfc/mfc-desktop-applications.md).  
  
-   Active Template Library \(ATL\): многофункциональная вспомогательная библиотека для создания компонентов COM. Для получения дополнительной информации см. [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).  
  
-   C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\): библиотека, предоставляющая возможность выполнять высокопроизводительные вычислительные задачи общего характера в графическом процессоре. Для получения дополнительной информации см. [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).  
  
-   Среда выполнения с параллелизмом: библиотека, упрощающая параллельное и асинхронное программирование для мультиядерных и многоядерных устройств. Для получения дополнительной информации см. [Среда выполнения с параллелизмом](../parallel/concrt/concurrency-runtime.md).  
  
 Для многих сценариев программирования Windows также требуется пакет Windows SDK, в который входят файлы заголовков, обеспечивающие доступ к компонентам операционной системы Windows. По умолчанию все выпуски [!INCLUDE[vs_dev14](../mfc/includes/vs_dev14_md.md)] устанавливают Windows SDK, позволяющий разрабатывать универсальные приложения Windows. При разработке универсальных приложений Windows для Windows 10 необходима версия SDK Windows для Windows 10. Сведения о пакете SDK для Windows 10 см. в описании [пакета SDK для Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=534603). \(Дополнительные сведения о пакетах Windows SDK для более ранних версий ОС Windows см. в разделе [Overview of the Windows SDK](../Topic/Overview%20of%20the%20Windows%20SDK.md).\)  
  
 Другие платформы, например Xbox и Azure, обладают собственными пакетами SDK, которые вам, возможно, потребуется установить. Дополнительные сведения см. в Центре разработчика DirectX и в Центре разработчика Azure.  
  
## Средства разработки  
 Visual Studio включает многофункциональный отладчик для машинного кода, средства статического анализа, графические средства отладки, полнофункциональный редактор кода, поддержку модульных тестов, а также множество других средств и служебных программ. Дополнительные сведения см. в статьях [Разработка приложений в Visual Studio](http://msdn.microsoft.com/ru-ru/97490c1b-a247-41fb-8f2c-bc4c201eff68) и [Интегрированная среда разработки и средства разработки](../Topic/IDE%20and%20Tools%20for%20Visual%20C++%20Development.md).  
  
## Связанные статьи  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|Родительский раздел для содержимого библиотеки MSDN о C\+\+.|