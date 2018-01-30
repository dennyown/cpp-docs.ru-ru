---
title: "Элементы управления MFC ActiveX: Использование шрифтов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs: C++
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a788285aed8e8b7483e13c954ee193aca69d1100
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-fonts"></a>Элементы управления MFC ActiveX: использование шрифтов
Если элемент управления ActiveX отображается текст, можно разрешить управления пользователю изменять внешний вид текста, изменив свойства шрифта. Свойства шрифта реализуются как объекты шрифта и может принимать одно из двух типов: стандартных или пользовательских. Стандартные свойства шрифта являются свойствами preimplemented шрифта, которые можно добавить с помощью мастера добавления свойства. Пользовательские свойства шрифта не являются preimplemented и разработчик элемента управления определяет поведение и использование этого свойства.  
  
 В этой статье рассматриваются следующие темы:  
  
-   [С помощью свойства Stock Font](#_core_using_the_stock_font_property)  
  
-   [С помощью свойств пользовательского шрифта в элементе управления](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a>С помощью стандартных Font-свойство  
 Стандартные свойства шрифта preimplemented классом [COleControl](../mfc/reference/colecontrol-class.md). Кроме того стандартная страница свойств шрифта доступна, чтобы пользователи могли изменять различные атрибуты объекта шрифта, например его имя, размер и стиль.  
  
 Доступ к объекту через шрифта [GetFont](../mfc/reference/colecontrol-class.md#getfont), [SetFont](../mfc/reference/colecontrol-class.md#setfont), и [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) функции `COleControl`. Элемент управления пользователя будет доступ к объекту шрифта через `GetFont` и `SetFont` функций так же, как любые другие свойства Get и Set. Если требуется доступ к объекту шрифт из внутри элемента управления, используйте `InternalGetFont` функции.  
  
 Как было сказано в [элементы управления MFC ActiveX: свойства](../mfc/mfc-activex-controls-properties.md), добавление стандартных свойств упрощается благодаря [мастер добавления свойств](../ide/names-add-property-wizard.md). Выберите свойство Font и мастер добавления свойств автоматически вставляет биржевых запись шрифта в карту диспетчеризации элемента управления.  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Чтобы добавить свойство Font с помощью мастера добавления свойства  
  
1.  Загрузите проект элемента управления.  
  
2.  В представлении класса разверните узел библиотеки элемента управления.  
  
3.  Щелкните правой кнопкой мыши узел интерфейса для элемента управления (второй узел узла библиотеки), чтобы открыть контекстное меню.  
  
4.  В контекстном меню щелкните **добавить** и нажмите кнопку **добавить свойство**.  
  
     Откроется мастер добавления свойств.  
  
5.  В **имя свойства** щелкните **шрифта**.  
  
6.  Нажмите кнопку **Готово**.  
  
 Мастер добавления свойств добавляет следующий карту диспетчеризации элемента управления, расположенных в файле реализации класса элемента управления:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 Кроме того мастер добавления свойств добавляет следующую строку в элемент управления. IDL-файла:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 Стандартное свойство Caption является примером свойство text, которое может отображаться биржевых данных свойства шрифта. Добавление в элемент управления stock капитализации использует шагов, аналогичных используемым акции свойства шрифта.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Чтобы добавить стандартное свойство заголовка, с помощью мастера добавления свойства  
  
1.  Загрузите проект элемента управления.  
  
2.  В представлении класса разверните узел библиотеки элемента управления.  
  
3.  Щелкните правой кнопкой мыши узел интерфейса для элемента управления (второй узел узла библиотеки), чтобы открыть контекстное меню.  
  
4.  В контекстном меню щелкните **добавить** и нажмите кнопку **добавить свойство**.  
  
     Откроется мастер добавления свойств.  
  
5.  В **имя свойства** щелкните **заголовок**.  
  
6.  Нажмите кнопку **Готово**.  
  
 Мастер добавления свойств добавляет следующий карту диспетчеризации элемента управления, расположенных в файле реализации класса элемента управления:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a>Изменение функции OnDraw  
 Реализация по умолчанию `OnDraw` использует Windows системный шрифт для всего текста, отображаемого в элементе управления. Это означает, что необходимо изменить `OnDraw` кода, выбрав объект шрифта в контекст устройства. Чтобы сделать это, вызовите [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) и передать контекст устройства для элемента управления, как показано в следующем примере:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 После `OnDraw` функция была изменена, чтобы использовать объект шрифта, текст в элементе управления отображается с характеристиками из свойство Font элемента управления.  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a>С помощью свойств пользовательского шрифта в элементе управления  
 Помимо свойство Font элемент управления ActiveX может иметь пользовательские свойства шрифта. Для добавления пользовательского шрифта свойства необходимо выполнить следующее:  
  
-   Используйте мастер добавления свойств для реализации настраиваемого свойства шрифта.  
  
-   [Обработка уведомлений шрифта](#_core_processing_font_notifications).  
  
-   [Реализация нового интерфейса уведомлений шрифта](#_core_implementing_a_new_font_notification_interface).  
  
###  <a name="_core_implementing_a_custom_font_property"></a>Реализация свойства пользовательского шрифта  
 Для реализации настраиваемого свойства шрифта, используйте мастер добавления свойств для добавления свойства и затем внести некоторые изменения в код. В следующих разделах описаны способы добавления пользовательского `HeadingFont` свойства пример элемента управления.  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Добавление пользовательского свойства шрифта с помощью мастера добавления свойства  
  
1.  Загрузите проект элемента управления.  
  
2.  В представлении класса разверните узел библиотеки элемента управления.  
  
3.  Щелкните правой кнопкой мыши узел интерфейса для элемента управления (второй узел узла библиотеки), чтобы открыть контекстное меню.  
  
4.  В контекстном меню щелкните **добавить** и нажмите кнопку **добавить свойство**.  
  
     Откроется мастер добавления свойств.  
  
5.  В **имя свойства** введите имя для свойства. В этом примере используется **HeadingFont**.  
  
6.  В поле **Тип реализации**выберите **Методы Get/Set**.  
  
7.  В **тип свойства** выберите **IDispatch\***  для типа свойства.  
  
8.  Нажмите кнопку **Готово**.  
  
 Мастер добавления свойств создает код, чтобы добавить `HeadingFont` настраиваемого свойства `CSampleCtrl` класса и ОБРАЗЦА. IDL-файл. Поскольку `HeadingFont` является типом свойства Get и Set, мастер добавления свойств изменяет `CSampleCtrl` карту диспетчеризации класса для включения `DISP_PROPERTY_EX_ID` [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) запись макроса:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 `DISP_PROPERTY_EX` Связывает макрос `HeadingFont` имя свойства с соответствующими `CSampleCtrl` класс методов Get и Set, `GetHeadingFont` и `SetHeadingFont`. Тип значения свойства также указан; в этом случае **VT_FONT**.  
  
 Мастер добавления свойств также добавляет объявления в файле заголовка элемента управления (. (H) для `GetHeadingFont` и `SetHeadingFont` функции и добавляет их шаблонов функций в файле реализации элемента управления (. CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 Наконец мастер добавления свойств изменяет элемент управления. IDL-файл, добавив запись для `HeadingFont` свойства:  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>Изменения в коде элемента управления  
 Теперь, когда вы добавили `HeadingFont` свойство элемента управления, необходимо внести некоторые изменения в файлы заголовка и реализации элемента управления для полной поддержки нового свойства.  
  
 В файле заголовка элемента управления (. (H), добавьте следующее объявление переменной защищенного члена:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 В файле реализации элемента управления (. CPP), выполните следующие действия:  
  
-   Инициализация `m_fontHeading` в конструктор элемента управления.  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   Объявите статическую **FONTDESC** структуру, содержащую атрибуты по умолчанию шрифта.  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   В элементе управления `DoPropExchange` члена функции, добавьте вызов `PX_Font` функции. Это обеспечивает инициализацию и сохраняемости для пользовательского свойства шрифта.  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   Готово к реализации элемента управления `GetHeadingFont` функции-члена.  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   Готово к реализации элемента управления `SetHeadingFont` функции-члена.  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   Изменить элемент управления `OnDraw` функции-члена для определения переменной для хранения ранее выбранный шрифт.  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   Изменить элемент управления `OnDraw` выберите пользовательского шрифта в контексте устройства, добавив следующие строки там, где шрифт будет использоваться функция-член.  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   Изменить элемент управления `OnDraw` функции-члена для выбора предыдущего шрифта обратно в контексте устройства, добавив следующую строку после начала использования шрифта.  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 После реализации пользовательского свойства шрифта стандартные свойства шрифтов должны быть реализованы, предоставляя пользователям элемента управления для изменения текущего шрифта элемента управления. Чтобы добавить идентификатор страницы свойств для стандартной страницы свойств шрифта, вставьте следующую строку после `BEGIN_PROPPAGEIDS` макрос:  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 Вы также должны увеличить параметр счетчика макроса `BEGIN_PROPPAGEIDS` на один. Это показано в следующей строке:  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 После внесения этих изменений необходимо перестройте весь проект, чтобы включить дополнительные функциональные возможности.  
  
###  <a name="_core_processing_font_notifications"></a>Обработка уведомлений шрифта  
 В большинстве случаев необходимо знать при характеристики шрифта объекта были изменены. Каждый объект шрифта способен предоставлять уведомления при изменении его путем вызова функции-члена **IFontNotification** реализуют интерфейс `COleControl`.  
  
 Если элемент управления использует свойство Font, его уведомления обрабатываются `OnFontChanged` функции-члена `COleControl`. При добавлении свойства пользовательский шрифт, можно предоставить им использовать ту же реализацию. В примере выше это сделать, указав &**m_xFontNotification** при инициализации **m_fontHeading** переменной-члена.  
  
 ![Реализация интерфейсов нескольких объектов шрифта](../mfc/media/vc373q1.gif "vc373q1")  
Реализация интерфейсов нескольких объектов шрифта  
  
 Сплошные линии на приведенном выше рисунке Показать, что оба объекта шрифта с помощью того же реализации **IFontNotification**. Это может вызвать проблемы, если требуется различать изменить шрифт.  
  
 Для различения уведомления объект шрифта элемента управления можно создать отдельные реализации **IFontNotification** интерфейса для каждого объекта шрифта в элементе управления. Этот метод позволяет оптимизировать код отрисовки путем обновления только строку или строки, в которых используется шрифт недавно измененные. В следующих разделах описаны шаги, необходимые для реализации интерфейсов отдельные уведомления для второго свойства шрифта. Второе свойство шрифта считается `HeadingFont` свойство, которое было добавлено в предыдущем разделе.  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a>Реализация нового интерфейса уведомлений шрифта  
 Чтобы различать уведомления несколько шрифтов, новый интерфейс уведомлений должен быть реализован для каждого шрифта, используемого в элементе управления. В следующих разделах описаны способы реализации новый интерфейс уведомлений шрифта путем изменения файлов заголовка и реализации элемента управления.  
  
### <a name="additions-to-the-header-file"></a>Добавление в файл заголовка  
 В файле заголовка элемента управления (. (H), добавьте следующие строки к объявлению класса:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 При этом создается реализация `IPropertyNotifySink` интерфейс с именем `HeadingFontNotify`. Этот новый интерфейс содержит метод с именем `OnChanged`.  
  
### <a name="additions-to-the-implementation-file"></a>Добавление в файл реализации  
 В коде, который инициализирует шрифт заголовка (в конструктор элемента управления), измените `&m_xFontNotification` для `&m_xHeadingFontNotify`. Затем добавьте следующий код:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 `AddRef` И `Release` методы в `IPropertyNotifySink` интерфейс отслеживания объекта счетчик ссылок для объекта элемента управления ActiveX. Когда элемент управления получает доступ к указатель интерфейса, элемент управления вызывает `AddRef` для увеличения значения счетчика ссылок. По окончании элемента управления с указателем вызывает `Release`, в так же, как **GlobalFree** может вызываться для освобождения блока глобальной памяти. Когда счетчик ссылок для этого интерфейса становится равным нулю, может быть освобожден реализацию интерфейса. В этом примере `QueryInterface` функция возвращает указатель на `IPropertyNotifySink` интерфейс для определенного объекта. Эта функция позволяет запрашивать объект, чтобы определить, какие интерфейсы он поддерживает элемент управления ActiveX.  
  
 После внесения этих изменений в проект, перестройте проект и использовать контейнер для тестирования интерфейса. Сведения о том, как получить доступ к Контейнеру для тестирования, см. в разделе [Тестирование свойств и событий в Контейнере для тестирования](../mfc/testing-properties-and-events-with-test-container.md) .  
  
## <a name="see-also"></a>См. также  
 [Элементы управления ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Элементы управления ActiveX MFC: Использование изображений в элементе управления ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [Элементы ActiveX в MFC. Использование стандартных страниц свойств](../mfc/mfc-activex-controls-using-stock-property-pages.md)
