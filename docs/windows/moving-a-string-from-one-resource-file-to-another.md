---
title: "Перемещение строки из одного файла ресурсов в другой | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files, moving strings
- string editing, moving strings between resources
- String editor, moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecb999052aa23d173a6a4113007cbd8452510e5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="moving-a-string-from-one-resource-file-to-another"></a>Перемещение строки из одного файла ресурса в другой
### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Перемещение строки из одного файла скрипта ресурсов в другой  
  
1.  Откройте таблицы строк в обоих RC-файлах. (Дополнительные сведения см. в разделе [Просмотр ресурсов в файле скрипта ресурсов за пределами проекта](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)  
  
    > [!NOTE]
    >  Если в проекте еще нет RC-файла, см. раздел [Создание нового файла описания ресурсов](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Щелкните правой кнопкой мыши строку, необходимо переместить и выберите **Вырезать** в контекстном меню.  
  
3.  Поместите курсор в целевом **редактора строк** окна.  
  
4.  В RC-файле, к которому нужно вставить строку, щелкните правой кнопкой мыши и выберите **вставить** в контекстном меню.  
  
    > [!NOTE]
    >  Если **идентификатор** или **значение** перемещенной строки конфликтует с существующим **идентификатор** или **значение** в файле назначения, либо **Идентификатор** или **значение** перемещенной строки изменений. Если существует строка с тем же **идентификатор**, **идентификатор** перемещенной строки изменений. Если существует строка с тем же **значение**, **значение** перемещенной строки изменений.  
  
 Сведения о добавлении ресурсов в управляемые проекты (предназначенные общеязыковая среда выполнения), см. в разделе [ресурсы в классических приложениях](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework.* . Сведения о том, как вручную добавлять файлы ресурсов в проекты управляемого кода, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделах [Пошаговое руководство. Локализация Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) и [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6);  
  
 **Требования**  
  
 Win32  
  
## <a name="see-also"></a>См. также  
 [Редактор строк](../windows/string-editor.md)   
 [Файлы ресурсов](../windows/resource-files-visual-studio.md)   
 [Настройка макетов окон](/visualstudio/ide/customizing-window-layouts-in-visual-studio)   

