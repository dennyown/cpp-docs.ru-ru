---
title: "Opening a Resource for Binary Editing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary data, editing"
  - "resources [Visual Studio], opening for binary editing"
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Opening a Resource for Binary Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Открытие ресурса классического приложения Windows для редактирования в двоичном редакторе  
  
1.  В окне [представления ресурсов](../windows/resource-view-window.md) выберите файл ресурсов, который необходимо изменить.  
  
    > [!NOTE]
    >  Если в проекте еще нет RC\-файла, см. раздел [Создание нового файла описания ресурсов](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Щелкните ресурс правой кнопкой мыши, а затем выберите в контекстном меню команду **Открыть двоичные данные**.  
  
    > [!NOTE]
    >  Если с помощью окна [представления ресурсов](../windows/resource-view-window.md) открыть ресурс, формат которого не распознается средой Visual Studio \(например, RCDATA или настраиваемый ресурс\), ресурс будет автоматически открыт в двоичном редакторе.  
  
### Открытие управляемого ресурса для редактирования в двоичном редакторе  
  
1.  В обозревателе решений выберите файл ресурсов, который необходимо изменить.  
  
2.  Щелкните ресурс правой кнопкой мыши, а затем выберите в контекстном меню команду **Открыть с помощью**.  
  
3.  В диалоговом окне **Открыть с помощью** выберите **Двоичный редактор**.  
  
    > [!NOTE]
    >  Для работы с файлами ресурсов в управляемых проектах можно использовать [редактор изображений](../mfc/image-editor-for-icons.md) и [двоичный редактор](../mfc/binary-editor.md). Все управляемые ресурсы, которые нужно редактировать, должны быть связанными ресурсами. Редакторы ресурсов Visual Studio не поддерживают редактирование внедренных ресурсов.  
  
    > [!NOTE]
    >  Сведения о добавлении ресурсов в управляемые проекты см. в разделе [Ресурсы приложений](../Topic/Resources%20in%20Desktop%20Apps.md)*Руководства разработчика .NET Framework*. Сведения о том, как вручную добавлять файлы ресурсов в проекты управляемого кода, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделах [Пошаговое руководство. Локализация Windows Forms](http://msdn.microsoft.com/ru-ru/9a96220d-a19b-4de0-9f48-01e5d82679e5) и [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 ![Двоичный редактор](../Image/vcBinaryEditor2.gif "vcBinaryEditor2")  
Двоичные данные диалогового окна в двоичном редакторе  
  
 Только некоторые значение ASCII могут быть представлены в двоичном редакторе \(в диапазоне от 0x20 до 0x7E\). Дополнительные символы отображаются в виде точек в разделе "Значение ASCII" \(на правой панели двоичного редактора\). "Печатным" символам соответствуют значения ASCII в диапазоне от 32 до 126.  
  
> [!NOTE]
>  Если с помощью двоичного редактора необходимо отредактировать ресурс, который открыт в другом редакторе, необходимо сначала закрыть другой редактор.  
  
 **Требования**  
  
 Нет  
  
## См. также  
 [Binary Editor](../mfc/binary-editor.md)