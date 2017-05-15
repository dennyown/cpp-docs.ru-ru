---
title: "Сокеты Windows. Использование класса CAsyncSocket | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAsyncSocket - класс, модель программирования"
  - "SOCKET - дескриптор"
  - "сокеты [C++], асинхронная операция"
  - "сокеты [C++], преобразование между строками Юникода и MBCS"
  - "Сокеты Windows [C++], асинхронный"
  - "Сокеты Windows [C++], преобразование строк Юникода и MBCS"
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Сокеты Windows. Использование класса CAsyncSocket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

В этой статье описывается, как использовать класс [CAsyncSocket](../Topic/CAsyncSocket%20Class.md).  Обратите внимание, что этот класс инкапсулирует API Windows SSL на очень низкого уровня.  `CAsyncSocket` для использования программистами, знающие сетевого подробно, но хочет воспользоваться удобствами обратных вызовов для уведомления событий сети.  На основе этого допущении, этот раздел содержит только базовую инструкцию.  Возможно, следует рассмотреть использование `CAsyncSocket` при необходимости простота Windows sockets работать с несколькими сетевыми протоколами в приложении MFC, но не требуется пожертвовать гибкость.  Можно также заполнение, можно получить более высокую эффективность, программировать сообщения самостоятельно более непосредственно, чем можно с помощью более общей модели альтернативной класса `CSocket`.  
  
 `CAsyncSocket` документировано в *справочнике по MFC*.  C Visual C\+\+ также предоставляет спецификацию Windows SSL, расположенная в [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Данные остаются вам.  C Visual C\+\+ не предоставляет пример приложения для `CAsyncSocket`.  
  
 Если изменяются не знающий о связях системы и не требуется простое решение следует использовать класс [CSocket](../mfc/reference/csocket-class.md) с объектом `CArchive`.  Дополнительные сведения см. в разделе [Windows SSL. С помощью сокетов с архивами](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Этот раздел охватывает:  
  
-   Создание и использование объекта `CAsyncSocket`.  
  
-   [Ваши обязанности с CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Создание и использование объекта CAsyncSocket  
  
#### Использовать CAsyncSocket  
  
1.  Создает объект [CAsyncSocket](../Topic/CAsyncSocket%20Class.md) и использование объекта для создания основной дескриптор **SOCKET**.  
  
     Создание шаблона соответствует сокетов MFC двухшагового построения.  
  
     Примеры.  
  
     [!CODE [NVC_MFCSimpleSocket#3](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#3)]  
  
     – или –  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/CPP/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     Первый конструктор с создает объект `CAsyncSocket` в стеке.  Второй конструктор создает `CAsyncSocket` в куче.  Первый вызов [Создать](../Topic/CAsyncSocket::Create.md) выше используются параметры по умолчанию для создания сокет потока.  Второй вызов метода **Создать** создает сокет датаграмм с указанным портом и адреса. \(Можно использовать любой версии **Создать** с любым методом построения\).  
  
     Параметры в **Создать**:  
  
    -   «Порт»: короткое целое число.  
  
         Для сокета сервера необходимо указать порт.  Для сокета клиента обычно принять значение по умолчанию для этого параметра, который позволяет выбрать Windows порт SSL.  
  
    -   Тип сокета. **SOCK\_STREAM** \(по умолчанию\) или **SOCK\_DGRAM**.  
  
    -   Сокет «адрес», например «ftp.microsoft.com» или «128.56.22.8».  
  
         Это ваш адрес \(IP\) протокол IP в сети.  Возможно, всегда будет зависеть от значения по умолчанию для данного параметра.  
  
     Термин «порт» и «адрес сокета» рассматриваются в разделе [Windows SSL. Порты и адреса сокета](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Если клиент сокет подключите объект сокета сокета сервера, используя [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md).  
  
     – или –  
  
     Если сервер сокет, задайте сокет, чтобы начать ожидать \(с [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)\) для попытки подключения от клиента.  При получении запроса подключения, примите его с помощью [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md).  
  
     После принятия подключения можно выполнять такие задачи, как проверка пароли.  
  
    > [!NOTE]
    >  Функцию\-член **Принять** принимает ссылку на новый, пустой объект `CSocket` в качестве параметра.  Необходимо построить этот объект перед вызовом **Принять**.  Если этот объект сокета выходит за пределы области, закроет подключение.  Не вызывайте метод **Создать** для нового объекта сокета.  Пример см. в статье [Windows SSL. Последовательность операций](../Topic/Windows%20Sockets:%20Sequence%20of%20Operations.md).  
  
3.  Проделайте сообщения с другими сокетами путем вызова функции\-члены объекта `CAsyncSocket`, содержащие функции API Windows SSL.  
  
     В разделе Windows sockets спецификацию и [CAsyncSocket](../Topic/CAsyncSocket%20Class.md) в *справочнике по MFC*.  
  
4.  Удалите объект `CAsyncSocket`.  
  
     При создании объекта сокета в стеке, его при вызове деструктора, функция выходит за пределы области действия.  При создании объекта сокета в куче, с помощью оператора **новый**, то ответственность за использование оператора **удалить** для удаления объекта.  
  
     Деструктор функции\-члена [Закрыть](../Topic/CAsyncSocket::Close.md) объекта, прежде чем удалить объект.  
  
 Пример этой последовательности в коде \(фактически для объекта `CSocket` \) см. в разделе [Windows SSL. Последовательность операций](../Topic/Windows%20Sockets:%20Sequence%20of%20Operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Ваши обязанности с CAsyncSocket  
 При создании объекта класса [CAsyncSocket](../Topic/CAsyncSocket%20Class.md), содержащий дескриптор объекта **SOCKET** Windows и операции, на этом дескрипторе.  При использовании `CAsyncSocket` необходимо работать со всеми проблемами можно смотреть на при использовании API напрямую.  Примеры.  
  
-   «Блокировки» сценарии.  
  
-   Различия в порядка байтов отправя и время между компьютерами.  
  
-   Преобразование между юникод и строками многобайтовой кодировки \(MBCS\).  
  
 Для определения этих терминов и дополнительные сведения см. в разделах [Windows SSL. Блокировка](../Topic/Windows%20Sockets:%20Blocking.md), [Windows SSL. Порядок байтов](../mfc/windows-sockets-byte-ordering.md), [Windows SSL. Преобразования строк](../mfc/windows-sockets-converting-strings.md).  
  
 Несмотря на эти вопросы, класс **CAsycnSocket** самый лучший вариант для, если приложению требуется всей гибкости и элемент управления можно получить.  Если нет, необходимо рассмотреть возможность использования класса `CSocket` вместо.  `CSocket` скрывает много компонентов пользователя: он нагнетает сообщения Windows во время заблокированных вызовов и обеспечивает доступ к `CArchive`, управляющий различия в и преобразование строк порядка байтов автоматически.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Windows SSL. Фон](../mfc/windows-sockets-background.md)  
  
-   [Windows SSL. Сокеты потока](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows SSL. Сокеты датаграмм](../mfc/windows-sockets-datagram-sockets.md)  
  
## См. также  
 [Сокеты Windows в MFC](../mfc/windows-sockets-in-mfc.md)