---
title: "ODBC. Библиотека курсоров ODBC | Microsoft Docs"
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
  - "библиотека курсоров ODBC"
  - "библиотека курсоров ODBC, снимки"
  - "курсоры, библиотека курсоров ODBC"
  - "драйверы ODBC уровня 1"
  - "библиотека курсоров ODBC [ODBC]"
  - "драйверы ODBC, поддержка курсора"
  - "драйверы ODBC, Уровень 1"
  - "ODBC, отметка времени"
  - "позиционированные обновления"
  - "позиционированные курсоры"
  - "снимки, поддержка (ODBC)"
  - "статические курсоры"
  - "отметки времени, столбцы отметки времени (ODBC)"
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ODBC. Библиотека курсоров ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

В этом разделе описывается библиотека курсоров ODBC, а также способ ее использования.  Дополнительные сведения см. в следующих разделах:  
  
-   [Библиотека курсоров и драйверы первого уровня ODBC](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Позиционированные обновления и столбцы временных меток](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Использование библиотеки курсоров](#_core_using_the_cursor_library)  
  
 Библиотека курсоров представляет собой библиотеку динамической компоновки \(DLL\), которая располагается между диспетчером драйвера ODBC и самим драйвером.  В условиях ODBC драйвер поддерживает отслеживание курсором его позиции в наборе записей.  Курсор отмечает позицию в наборе записей, к которой была выполнена прокрутка, т.е. текущую запись.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Библиотека курсоров и драйверы первого уровня ODBC  
 Библиотека курсоров ODBC предоставляет драйверам первого уровня некоторые новые возможности.  
  
-   Прямая и обратная прокрутка.  Для драйверов второго уровня не требуется библиотека курсоров, поскольку они самостоятельно могут выполнять прокрутку.  
  
-   Поддержка моментальных снимков.  Библиотека курсоров управляет буфером, содержащим записи моментальных снимков.  Этот буфер отражает удаления и изменения записей, выполненные одним пользователем в программе, однако, не отражает добавления, удаления или изменения, внесенные другими пользователями.  Поэтому моментальные снимки соответствуют только буферу библиотеки курсоров.  Также буфер не отражает добавления пользователя, если не была вызвана функция **Обновление**.  Динамические подмножества данных не используют библиотеки курсоров.  
  
 Библиотека курсоров предоставляет моментальные снимки \(статические курсоры\), даже если обычно они не поддерживаются используемым драйвером.  Если используемый драйвер поддерживает статические курсоры, загрузка библиотеки курсоров для поддержки моментальных снимков не требуется.  При использовании библиотеки курсоров можно применять только моментальные снимки и наборы записей последовательного доступа.  Если драйвер поддерживает динамические подмножества данных \(курсоры KEYSET\_DRIVEN\) для их использования не нужно обращаться к библиотеке курсоров.  Чтобы воспользоваться моментальными снимками и динамическими подмножествами данных, их необходимо вводить в два разных объекта \(подключения\) `CDatabase` в случае, если драйвер их не поддерживает.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Позиционированные обновления и столбцы временных меток  
  
> [!NOTE]
>  Источники данных ODBC доступны с помощью классов ODBC MFC, как описано в данном разделе, или с помощью классов DAO MFC.  
  
> [!NOTE]
>  Данный раздел не относится к случаю, когда драйвер ODBC поддерживает **SQLSetPos**, используемый MFC \(если он доступен\).  
  
 Большинство драйверов первого уровня не поддерживают позиционированные обновления.  Такие драйверы основываются на библиотеке курсоров, чтобы скопировать возможности драйверов второго уровня в этом отношении.  Библиотека курсоров имитирует поддержку позиционированного обновления, выполняя поисковое обновление на неизменных полях.  
  
 В некоторых случаях набор записей может содержать столбец временных меток подобно одному из неизменных полей.  При использовании наборов записей MFC с таблицами, содержащими столбцы временных меток, возникают две проблемы.  
  
 Первая касается обновляемых моментальных снимков в таблицах, содержащих столбцы временных меток.  Если таблица, к которой привязан моментальный снимок, содержит столбец временных меток, необходимо после вызова функций **Правка** и **Обновить** вызвать **Обновление**.  В противном случае изменение этой записи в дальнейшем может оказаться невозможным.  При вызове **Правка**, а затем **Обновить** запись заносится в источник данных, и столбец временных меток обновляется.  Если не вызвать **Обновление**, значение временной метки для записи в моментальном снимке больше не будет совпадать с соответствующей временной меткой в источнике данных.  При повторном обновлении источник данных может запретить обновление в результате несовпадения.  
  
 Вторая проблема касается ограничений класса [CTime](../Topic/CTime%20Class.md) при использовании с функцией `RFX_Date` для передачи сведений о дате и времени в таблицу или из нее.  В результате обработки объекта `CTime` при передаче данных некоторые служебные данные могут накладываться в форме промежуточной обработки.  Для некоторых приложений диапазон дат объектов `CTime` может иметь многочисленные ограничения.   Вместо объекта `CTime` новая версия функции `RFX_Date` применяет параметр ODBC **TIMESTAMP\_STRUCT**.  Дополнительные сведения см. в `RFX_Date` разделе [Макросы и глобальные элементы](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md) в *Справочнике по MFC*.  
  
##  <a name="_core_using_the_cursor_library"></a> Использование библиотеки курсоров  
 При подключении к источнику данных с помощью вызова [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) или [CDatabase::Open](../Topic/CDatabase::Open.md) можно уточнить, нужно ли использовать для источника данных библиотеку курсоров.  Если в источнике данных создаются моментальные снимки, для параметра **CDatabase::useCursorLib** в `dwOptions` необходимо указывать значение `OpenEx` или значение **TRUE** для параметра **bUseCursorLib** в функции **Открыть** \(по умолчанию используется значение **TRUE**\).  Если драйвер ODBC поддерживает динамические подмножества данных, для их открытия в источнике данных не рекомендуется использовать библиотеку курсоров \(поскольку она скрывает некоторые функциональные возможности драйвера, необходимые для динамического подмножества данных\).  В этом случае не указывайте **CDatabase::useCursorLib** в `OpenEx` или укажите значение **FALSE** для параметра **bUseCursorLib** в функции **Открыть**.  
  
## См. также  
 [Основы ODBC](../../data/odbc/odbc-basics.md)