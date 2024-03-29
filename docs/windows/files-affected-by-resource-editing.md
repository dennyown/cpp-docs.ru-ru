---
title: "Файлы, на которые влияет редактирование ресурсов | Документы Microsoft"
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
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b3a5f8c8351d7056409b0e6182862213c51381a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="files-affected-by-resource-editing"></a>Файлы, на которые влияет редактирование ресурсов
Во время сеанса редактирования ресурсов среда Visual Studio работает с файлами, приведенными в следующей таблице.  
  
|Имя файла|Описание:|  
|---------------|-----------------|  
|Resource.h|Файл заголовка, создаваемый средой разработки. Содержит определения символов.|  
|Filename.aps|Двоичная версия текущего файла описания ресурсов. Используется для ускорения загрузки.<br /><br /> Редакторы ресурсов не читают RC-файлы и файлы resource.h непосредственно. Компилятор ресурсов компилирует их в APS-файлы, используемые редакторами ресурсов. Этот файл представляет собой этап компиляции и содержит только символьные данные. Как и при обычном процессе компиляции, данные, не являющиеся символьными (например комментарии), удаляются во время компиляции. Каждый раз, когда APS-файл теряет синхронность с RC-файлом, RC-файл создается заново (например, при выполнении команды «Сохранить» редактор ресурсов перезаписывает RC-файл и файл resource.h). Любые изменения в самих ресурсах останутся включенными в RC-файл, но комментарии всегда теряются после перезаписи RC-файла. Сведения о сохранении комментариев см. в разделе [Включение ресурсов во время компиляции](../windows/how-to-include-resources-at-compile-time.md).|  
|RC|Файл описания ресурсов, содержащий скрипт для ресурсов в текущем проекте. Этот файл перезаписывается APS-файлом при каждом сохранении.|  
  

  
## <a name="requirements"></a>Требования  
 Win32  
  
## <a name="see-also"></a>См. также  
 [Файлы ресурсов](../windows/resource-files-visual-studio.md)