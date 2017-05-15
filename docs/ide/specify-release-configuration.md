---
title: "Задание конфигурационных параметров выпуска, мастер создания проекта из существующих файлов кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.importwiz.releasesettings"
dev_langs: 
  - "C++"
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Задание конфигурационных параметров выпуска, мастер создания проекта из существующих файлов кода
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Эта страница мастера создания проекта из существующих файлов кода используется для задания конфигурационных параметров выпуска проекта.  
  
## Список задач  
 [Практическое руководство. Создание проекта C\+\+ из существующего кода](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## Список элементов пользовательского интерфейса  
 **Аналогично отладочной конфигурации**  
 Указывает, что мастер будет создавать параметры конфигурации выпуска проекта аналогично параметрам конфигурации отладки проекта.  По умолчанию этот параметр включен.  Остальные параметры на данной странице неактивны до тех пор, пока на них установлен флажок.  
  
 **Командная строка построения**  
 Определяет командную строку для построения нового проекта.  Введите имя компилятора вместе с необходимыми ключами и аргументами, которые необходимо использовать для построения нового проекта.  Данный параметр доступен, если на странице **Задать параметры проекта** выбран параметр **Использовать внешнюю систему построения**.  
  
 **Перестроить командную строку**  
 Определяет командную строку для повторного построения проекта.  Данный параметр доступен, если на странице **Задать параметры проекта** выбран параметр **Использовать внешнюю систему построения**.  
  
 **Очистить командную строку**  
 Определяет командную строку для удаления вспомогательных файлов, создаваемых инструментами построения для нового проекта.  Данный параметр доступен, если на странице **Задать параметры проекта** выбран параметр **Использовать внешнюю систему построения**.  
  
 **Вывод \(для отладки\)**  
 Указывает путь к каталогу размещения выходных файлов для конфигурации отладки нового проекта.  Данный параметр доступен, если на странице **Задать параметры проекта** выбран параметр **Использовать внешнюю систему построения**.  
  
 **Определения препроцессора \(\/D\)**  
 Определяет символы препроцессора для нового проекта.  Дополнительные сведения см. в разделе [Определения препроцессора \(\/D\)](../build/reference/d-preprocessor-definitions.md).  
  
 **Включить путь для поиска \(\/I\)**  
 Определяет пути к каталогам, добавляемым в список каталогов, в которых компилятор будет выполнять поиск для разрешения ссылок на файлы, переданных в директивы препроцессора в новом проекте.  Дополнительные сведения см. в разделе [\/I \(дополнительные каталоги включения\)](../build/reference/i-additional-include-directories.md).  
  
 **Принудительное включение файлов \(\/FI\)**  
 Определяет заголовочные файлы, которые должны обрабатываться при построении нового проекта.  Дополнительные сведения см. в разделе [\/FI \(имя принудительно включаемого файла\)](../Topic/-FI%20\(Name%20Forced%20Include%20File\).md).  
  
 **Пути для поиска сборки .NET \(\/AI\)**  
 Определяет пути к каталогам, в которых компилятор будет выполнять поиск для разрешения ссылок на сборки .NET, переданных в директивы препроцессора в новом проекте.  Дополнительные сведения см. в разделе [\/AI \(указание каталогов метаданных\)](../build/reference/ai-specify-metadata-directories.md).  
  
 **Принудительно использовать сборки .NET \(\/FU\)**  
 Определяет сборки .NET, которые должны обрабатываться при построении нового проекта.  Дополнительные сведения см. в разделе [\/FU \(именование файла с принудительно используемым атрибутом \#using\)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## См. также  
 [Указание параметров проекта, мастер создания проекта из существующих файлов кода](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)