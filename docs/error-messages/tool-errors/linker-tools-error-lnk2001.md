---
title: "Ошибка средств компоновщика LNK2001 | Документы Microsoft"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51f78f436d0e19779d0ebca499a559a60d12bcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2001"></a>Ошибка средств компоновщика LNK2001
неразрешенный внешний символ "*символ*»  
  
Скомпилированный код делает ссылку или вызов *символ*, однако этот символ не определен ни в одном из библиотеки или объектные файлы, указанные в компоновщик.  
  
Это сообщение об ошибке сопровождается неустранимой ошибки [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Необходимо исправить ошибки все LNK2001 и ошибки LNK2019 для устранения ошибки LNK1120.  
  
## <a name="possible-causes"></a>Возможные причины  
  
Существует множество способов, чтобы получить эту ошибку, но все они требуют ссылку на функцию или переменную, компоновщик не может *устранить*, или найти определение. Компилятор может указать, когда символ не *объявлен*, но не при не *определенные*, так как определение может находиться в другом файле исходного кода или библиотеки. Если символ имеется ссылка, но не определена, компоновщик создает ошибку.  
  
### <a name="coding-issues"></a>Проблем кодирования  
  
Эта ошибка может вызываться несоответствующие варианта в исходный код или определения модуля (DEF) файла. Например, если имя переменной `var1` в C++ один исходный файл и получить доступ к его как `VAR1` в другом, возникает эта ошибка. Чтобы устранить эту проблему, используйте постоянно написания и регистр имен.  
  
Эта ошибка может быть вызвана в проект, использующий [встраивания функции](../../error-messages/tool-errors/function-inlining-problems.md) при определении функции в исходном файле, а не в файле заголовка. Встроенных функций не будут отображаться за пределами исходного файла, который определяет их. Чтобы устранить эту проблему, определите встроенных функций в заголовках которых они объявлены.  
  
Эта ошибка может возникать при вызове функции C из программы на C++ без использования `extern "C"` объявление функции C. Компилятор использует другой символ внутренние соглашения об именовании для кода C и C++, а имя внутреннего символа, которое ищет компоновщик при разрешении символы. Чтобы устранить эту проблему, используйте `extern "C"` оболочки для всех объявлений функции C, используемые в коде C++ и предписывает компилятору использовать внутренние соглашения об именовании C для этих символов. Параметры компилятора [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) и [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) заставляют компилятор компилировать файлы как C++ или C, соответственно, независимо от расширения имени файла. Эти параметры могут привести к имена Внутренняя функция отличается от ожидаемого.  
  
Эта ошибка может быть вызвано попытка ссылки на функции или данные, которые не имеют внешнюю компоновку. В C++ встроенные функции и `const` данных имеют внутреннюю компоновку, если явно не указаны как `extern`. Чтобы устранить эту проблему, используйте явную `extern` называют объявления на символы за пределами определяющей исходного файла.  
  
Эта ошибка может быть вызвана [отсутствует тело функции или переменная](../../error-messages/tool-errors/missing-function-body-or-variable.md) определения. Эта ошибка проявляется в тех случаях, когда объявлена, но не определил, переменные, функции или классы в коде. Компилятор должен только прототип функции или `extern` объявление переменной для создания объектного файла без ошибок, но компоновщик не может разрешить вызов функции или ссылки на переменные, так как нет места кода или переменной функции зарезервировано. Чтобы устранить эту проблему, убедитесь, что все функции и переменной полностью определен в исходном файле или в библиотеке, включенных в ссылке.  
  
Эта ошибка может быть вызвана вызов функции, который использует типы параметров и возвращаемого или соглашения о вызовах, которые не соответствуют его атрибутам в определении функции. В C++ файлы объектов [Декорирование имен](../../error-messages/tool-errors/name-decoration.md) включает соглашение о вызовах, область действия класса или пространства имен и типы параметров и возвращаемого функции в окончательное дополненное имя функции, которая используется как символ для сопоставления, если вызовы разрешаются функции из других объектных файлов. Чтобы устранить эту проблему, убедитесь, что объявление, определение и вызовы все функции использовать теми же областями, типы и соглашения о вызовах.  
  
Эта ошибка может возникать в коде C++ при включают прототип функции в определении класса, но не [включают реализация](../../error-messages/tool-errors/missing-function-body-or-variable.md) функции и затем вызывает его. Чтобы устранить эту проблему, не забудьте предоставить определение для всех вызывается объявленных членов класса.  
  
Эта ошибка может быть вызвано быть попытка вызова чистой виртуальной функции от абстрактного базового класса. Чистой виртуальной функции не имеет базового класса реализации. Чтобы устранить эту проблему, убедитесь, что все виртуальные функции вызывается реализованы.  
  
Эта ошибка может вызываться используется переменная, объявленная внутри функции ([локальной переменной](../../error-messages/tool-errors/automatic-function-scope-variables.md)) за пределами видимости данной функции. Чтобы устранить эту проблему, удалите ссылку на переменную, которая не находится в области или переместить переменную в области более высокого уровня.  
  
Эта ошибка может возникать при построении окончательной версии проекта ATL, формирующего сообщение, код запуска CRT не требуется. Чтобы устранить эту проблему, выполните одно из следующих значений  
  
-   Удалите `_ATL_MIN_CRT` из списка препроцессор определяет, чтобы разрешить включение кода запуска CRT. В разделе [свойств «Общие» (проект)](../../ide/general-property-page-project.md) для получения дополнительной информации.  
  
-   Если это возможно удалите вызовы функций CRT, требующие код запуска CRT. Вместо этого используйте эквиваленты для Win32. Например, использовать `lstrcmp` вместо `strcmp`. Известные функции, требующие код запуска CRT приведены некоторые строки и функции с плавающей запятой.  
  
### <a name="compilation-and-link-issues"></a>Проблемы компиляции и ссылки  
  
Эта ошибка может возникать, если в проекте отсутствует ссылка на библиотеку (. LIB) или объекта (. Файл OBJ). Чтобы устранить эту проблему, добавьте ссылку на библиотеку, необходимую или объектный файл в проект. Дополнительные сведения см. в разделе [LIB-файлы в качестве входных данных компоновщика](../../build/reference/dot-lib-files-as-linker-input.md).  
  
Эта ошибка может возникать, если вы используете [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) или [/Zl](../../build/reference/zl-omit-default-library-name.md) параметры. При указании этих параметров библиотеки, содержащие необходимый код не связаны в проект, если включены явно. Чтобы устранить эту проблему, явным образом включите все библиотеки, используемой в командную строку компоновки. Появление много отсутствующие имена функций CRT и стандартной библиотеке при использовании этих параметров, явно включите файлы CRT и стандартной библиотеки DLL или библиотеки в ссылке.  

Если компиляция выполняется с помощью **/CLR** , то может быть отсутствует ссылка на .cctor. Чтобы устранить эту проблему, в разделе [Инициализация смешанных сборок](../../dotnet/initialization-of-mixed-assemblies.md) для получения дополнительной информации.  
  
Эта ошибка может возникать при связывании библиотеками в режиме выпуска при построении отладочной версии приложения. Аналогичным образом при использовании параметров **/MTd** или **/MDd** или определить `_DEBUG` и свяжите версию библиотеки, следует ожидать, что многие потенциальные неразрешенных внешних элементов, помимо других проблем. Связывание построения в режиме выпуска с отладочными библиотеками, также вызывает подобных проблем. Чтобы устранить эту проблему, убедитесь, что использовать отладочные библиотеки в отладочных построениях, и библиотеки розничной торговли в вашей окончательных сборок.  
  
Эта ошибка может возникать, если ваш код ссылается на символ из одной версии библиотек, но указать другую версию библиотеки в компоновщик. Как правило нельзя смешивать файлов объектов или библиотек, которые построены для разных версий компилятора. Библиотеки, входящие в новой версии может содержать символы, которые не удается найти в библиотеках предыдущих версий и наоборот. Чтобы устранить эту проблему, построение всех объектных файлов и библиотек, с той же версии компилятора перед их связи друг с другом.  
  
-  Средства &#124; Параметры &#124; Проекты &#124; Диалоговое окно каталоги VC ++, при выборе файлов библиотек позволяет изменить порядок поиска библиотеки. Папка "компоновщик" в диалоговом окне страницы свойств проекта может также содержать пути, которые могут быть устаревшими.  
  
-  Такая проблема может возникнуть при установке нового SDK (возможно, чтобы новое место), а порядок поиска не обновляется, чтобы он указывал на новое место. Как правило, необходимо указать путь для нового SDK директорий перед расположение по умолчанию Visual C++. Кроме того проект, содержащий встроенные пути, по-прежнему может указывать на старые пути, которые допустимы, но истек срок для новых функций, встроенных новой версией, которая устанавливается в другом месте.  
  
-   Если построение из командной строки и создали собственные переменные среды, проверьте, пути к средства, библиотеки и заголовочные файлы перейти к согласованность версий. Дополнительные сведения см. в разделе [набор переменных пути и среды для сборок командной строки](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
  
В настоящее время отсутствует стандарт для [об именовании C++](../../error-messages/tool-errors/name-decoration.md) между поставщиками компиляторов и даже между различными версиями одного компилятора. Таким образом при связывании объектных файлов с помощью других компиляторов может не создавать различные схемы именования, таким образом, вызвать ошибку LNK2001.  
  
[Смешивание встроенной и не являющиеся встроенными компиляции параметры](../../error-messages/tool-errors/function-inlining-problems.md) в различных модулях может вызвать ошибку LNK2001. Если библиотека C++ создается с функциональная возможность встраивания включена (**/Ob1** или **/Ob2**), но в соответствующем файле заголовка, описывающем функции встраивания отключена (не `inline` ключевое слово), ошибки имеет место. Чтобы устранить эту проблему, необходимо определить функции `inline` в файле заголовка можно включить в других исходных файлах.  
  
Если вы используете `#pragma inline_depth` компилятора директив, убедитесь, что у вас есть [значение 2 или более](../../error-messages/tool-errors/function-inlining-problems.md)и убедитесь, что также используют [/Ob1](../../build/reference/ob-inline-function-expansion.md) или [/Ob2](../../build/reference/ob-inline-function-expansion.md) параметр компилятора.  
  
Эта ошибка может возникать, если связь не указан параметр/NOENTRY при создании Библиотеку ресурсов. Чтобы устранить эту проблему, добавьте параметр/NOENTRY команде link.  
  
Эта ошибка может возникать при использовании неправильный параметр/SUBSYSTEM или/Entry параметры в своем проекте. Например, если вы пишете консольное приложение и указываете/SUBSYSTEM: Windows, неразрешенная внешняя ошибка создается для `WinMain`. Чтобы устранить эту проблему, убедитесь, что соответствует параметры для данного типа проектов. Дополнительные сведения об этих параметрах и точки входа см. в разделе [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) и [/Entry](../../build/reference/entry-entry-point-symbol.md) параметры компоновщика.  
  
### <a name="exported-symbol-issues"></a>Экспортированному символу проблемы  
  
Эта ошибка возникает, если экспорт в DEF-файл не найден. Возможно, не существует, неверно указан или использует внутреннее имя C++. DEF-файла не принимают внутренние имена. Чтобы устранить эту проблему, удалите ненужные экспорты и используйте `extern "C"` объявления для экспортируемых символах.  
  
## <a name="what-is-an-unresolved-external-symbol"></a>Что такое неразрешенный внешний символ  
  
Объект *символ* — это имя функции или глобальной переменной используется системой скомпилированного объекта файла или библиотеки. Символ — *определенные* в объектном файле где хранилища, выделенного для глобальной переменной или функции, где размещается скомпилированный код тела функции. *Внешний символ* — это символ, который *упоминаемого*, то есть, или вызывается в одном объектном файле, однако в другом файле библиотеки или объекта. *Экспортировать символ* , сделанный общедоступным файл объекта или библиотеки, которая определяет его. Компоновщик должен *устранить*, или найти соответствующее определение для каждого внешнего символа ссылаются объектный файл, если она связана с приложением или DLL. Компоновщик создает ошибку при невозможности разрешить внешнего символа путем нахождения соответствия экспортированному символу во всех связанных файлов.    
  
## <a name="use-the-decorated-name-to-find-the-error"></a>Использовать декорированное имя для поиска ошибок
  
Используйте компилятор и компоновщик C++ [Декорирование имен](../../error-messages/tool-errors/name-decoration.md), также известных как *искажение имени*, для кодирования дополнительных сведений о типа переменной или типа возвращаемого значения, типы параметров, область и вызова метода соглашение о функции с именем символа. Это внутреннее имя является именем символа ищет компоновщик для разрешения внешних символов.  
  
Из-за дополнительных сведений становится частью имени символа, если объявление функции или переменной точно соответствует определению функции или переменной могут занимать ошибка связи. Это может произойти, даже при использовании того же файла заголовка в вызывающий код и код, определяющий, при использовании флаги компилятора при компиляции исходных файлов. Например, эта ошибка может возникнуть при компиляции кода для использования `__vectorcall` соглашение о вызовах, но ссылки на библиотеку, которая ожидает клиентам вызывать его, используя значение по умолчанию `__cdecl` или `__fastcall` соглашение о вызовах. В этом случае символы не совпадают, так как различаются эти соглашения о вызовах   
  
Чтобы определить причину возникновения такой ошибки, сообщение об ошибке компоновщика показано как «понятное имя,» имя, используемое в исходный код и внутреннее имя (в скобках) для неразрешенный внешний символ. Не нужно знать, как перевести внутреннее имя, чтобы иметь возможность сравнить его с другим декорированные имена. Можно использовать средства командной строки, включенных с помощью компилятора для сравнения ожидаемый символ имя и имя фактического символа:  

-   [/EXPORTS](../../build/reference/dash-exports.md) и [/SYMBOLS](../../build/reference/symbols.md) возможностей средства командной строки программы DUMPBIN помогут определить, какие символы определены в файлах .dll и объекта или библиотеки. Это можно использовать, чтобы убедиться, что экспортированные декорированные имена совпадают, декорированные имена компоновщик ищет.  
  
В некоторых случаях Компоновщик сообщает только о декорированное имя символа. Программа UNDNAME командной строки можно использовать для получения недекорированной форме декорированного имени.  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
  
Дополнительные сведения о возможных причинах проблем и решений для LNK2001 см. в разделе вопросу переполнения стека [возможности ошибка неопределенной ссылки или неразрешенного внешнего символа и как ее исправить?](http://stackoverflow.com/q/12573816/2002113).  

