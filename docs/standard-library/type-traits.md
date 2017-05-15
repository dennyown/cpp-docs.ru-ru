---
title: "&lt;type_traits&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <type_traits>
dev_langs:
- C++
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
caps.latest.revision: 35
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86978cd4549f0672dac7cad0e4713380ea189c27
ms.openlocfilehash: ec13a255f456254f89ca84488d12fbf5ce0440b4
ms.contentlocale: ru-ru
ms.lasthandoff: 04/18/2017

---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;
Определяет шаблон, предоставляющий константы, которые содержат информацию о свойствах аргументов их типа или создают преобразованные типы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#include <type_traits>  
```  
  
## <a name="remarks"></a>Примечания  
 Классы и шаблоны в `<type_traits>` используются для поддержки определения, классификации и преобразования типов во время выполнения, а также для обнаружения связанных с типом ошибок и оптимизации универсального кода. Эти классы и шаблоны включают унарные признаки типов, которые описывают свойство типа, двоичные признаки типов, которые описывают связь между типами, и признаки преобразования, изменяющие свойство типа.  
  
 Для поддержки признаков типа определен вспомогательный класс `integral_constant`. Он имеет специализации шаблона `true_type` и `false_type`, формирующие базовые классы для предикатов типа. *Предикат типа* — это шаблон, принимающий один или несколько аргументов типа. Если предикат типа *имеет значение true*, он является открыто производным (явно или косвенно) от [true_type](../standard-library/type-traits-typedefs.md#true_type). Если значение предиката типа равно *false*, он является открыто производным (явно или косвенно) от [false_type](../standard-library/type-traits-typedefs.md#false_type).  
  
 *Модификатор типа* или *признак преобразования* — это шаблон, принимающий один или несколько аргументов шаблона и имеющий один член (`type`), который является синонимом для измененного типа.  
  
### <a name="alias-templates"></a>Шаблоны псевдонимов  
 Чтобы упростить выражения с признаками типов, предоставляются [шаблоны псевдонимов](../cpp/aliases-and-typedefs-cpp.md) для `typename some_trait<T>::type`, где "`some_trait`" — это имя класса шаблонов. Например, [add_const](../standard-library/add-const-class.md) имеет шаблон псевдонима для своего типа, `add_const_t`, определяемого следующим образом.  
  
```cpp  
template <class T>
using add_const_t = typename add_const<T>::type;
```  
  
|||||  
|-|-|-|-|  
|add_const_t|aligned_storage_t|make_signed_t|remove_pointer_t|  
|add_cv_t|aligned_union_t|make_unsigned_t|remove_reference_t|  
|add_lvalue_reference_t|common_type_t|remove_all_extents_t|remove_volatile_t|  
|add_pointer_t|conditional_t|remove_const_t|result_of_t|  
|add_rvalue_reference_t|decay_t|remove_cv_t|underlying_type_t|  
|add_volatile_t|enable_if_t|remove_extent_t||  
  
### <a name="classes"></a>Классы  
 Вспомогательный класс и определения типов  
  
|||  
|-|-|  
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Создает целочисленную константу из типа и значения.|  
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Содержит целочисленную константу со значением true.|  
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Содержит целочисленную константу со значением false.|  
  
 Категории основных типов  
  
|||  
|-|-|  
|[is_void](../standard-library/is-void-class.md)|Проверяет, является ли тип типом `void`.|  
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Проверяет, является ли тип типом `std::nullptr_t`.|  
|[is_integral](../standard-library/is-integral-class.md)|Проверяет, является ли тип целочисленным.|  
|[is_floating_point](../standard-library/is-floating-point-class.md)|Проверяет, является ли тип вещественным (с плавающей запятой).|  
|[is_array](../standard-library/is-array-class.md)|Проверяет, является ли тип массивом.|  
|[is_pointer](../standard-library/is-pointer-class.md)|Проверяет, является ли тип указателем.|  
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Проверяет, является ли тип ссылкой lvalue.|  
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Проверяет, является ли тип ссылкой rvalue.|  
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Проверяет, является ли тип указателем на объект-член.|  
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Проверяет, является ли тип указателем на функцию-член.|  
|[is_enum](../standard-library/is-enum-class.md)|Проверяет, является ли тип перечислением.|  
|[is_union](../standard-library/is-union-class.md)|Проверяет, является ли тип объединением.|  
|[is_class](../standard-library/is-class-class.md)|Проверяет, является ли тип классом.|  
|[is_function](../standard-library/is-function-class.md)|Проверяет, является ли тип типом функции.|  
  
 Категории составных типов  
  
|||  
|-|-|  
|[is_reference](../standard-library/is-reference-class.md)|Проверяет, является ли тип ссылкой.|  
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Проверяет, является ли тип арифметическим.|  
|[is_fundamental](../standard-library/is-fundamental-class.md)|Проверяет, является ли тип `void` или арифметическим типом.|  
|[is_object](../standard-library/is-object-class.md)|Проверяет, является ли тип типом объекта.|  
|[is_scalar](../standard-library/is-scalar-class.md)|Проверяет, является ли тип скалярным.|  
|[is_compound](../standard-library/is-compound-class.md)|Проверяет, является ли тип нескалярным.|  
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Проверяет, является ли тип указателем на член.|  
  
 Свойства типов  
  
|||  
|-|-|  
|[is_const](../standard-library/is-const-class.md)|Проверяет, является ли тип типом `const`.|  
|[is_volatile](../standard-library/is-volatile-class.md)|Проверяет, является ли тип типом `volatile`.|  
|[is_trivial](../standard-library/is-trivial-class.md)|Проверяет, является ли тип простейшим.|  
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Проверяет, является ли тип тривиально копируемым.|  
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Проверяет, является ли тип стандартным макетом.|  
|[is_pod](../standard-library/is-pod-class.md)|Проверяет, является ли тип типом POD.|  
|[is_literal_type](../standard-library/is-literal-type-class.md)|Проверяет, может ли тип быть переменной `constexpr` или использоваться в функции `constexpr`.|  
|[is_empty](../standard-library/is-empty-class.md)|Проверяет, является ли тип пустым классом.|  
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Проверяет, является ли тип полиморфным классом.|  
|[is_abstract](../standard-library/is-abstract-class.md)|Проверяет, является ли тип абстрактным классом.|  
|[is_final](../standard-library/is-final-class.md)|Проверяет, является ли тип типом класса, отмеченным `final`.|  
|[is_signed](../standard-library/is-signed-class.md)|Проверяет, является ли тип знаковым целочисленным типом.|  
|[is_unsigned](../standard-library/is-unsigned-class.md)|Проверяет, является ли тип беззнаковым целочисленным типом.|  
|[is_constructible](../standard-library/is-constructible-class.md)|Проверяет, можно ли сконструировать тип с использованием заданных типов аргументов.|  
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Проверяет, имеет ли тип конструктор по умолчанию.|  
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Проверяет, имеет ли тип конструктор копирования.|  
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Проверяет, имеет ли тип конструктор перемещения.|  
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Проверяет, можно ли первому типу назначить значение второго типа.|  
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Проверяет, можно ли типу назначить значение ссылки константы типа.|  
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Проверяет, можно ли типу назначить ссылку rvalue типа.|  
|[is_destructible](../standard-library/is-destructible-class.md)|Проверяет, можно ли уничтожить тип.|  
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Проверяет, использует ли тип нетривиальные операции, если создан с использованием заданных типов.|  
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Проверяет, использует ли тип нетривиальные операции, если создан конструктором по умолчанию.|  
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Проверяет, использует ли тип нетривиальные операции, если создан конструктором копирования.|  
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Проверяет, использует ли тип нетривиальные операции, если создан конструктором перемещения.|  
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Проверяет, можно ли типам присвоить значение и использует ли назначение нетривиальные операции.|  
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Проверяет, можно ли типам присвоить значение копирования и использует ли назначение нетривиальные операции.|  
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Проверяет, можно ли типам присвоить значение перемещения и использует ли назначение нетривиальные операции.|  
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Проверяет, является ли тип разрушаемым и использует ли деструктор нетривиальные операции.|  
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Проверяет, является ли тип конструируемым и известно ли, что он не выдает исключение, если создан с использованием заданных типов.|  
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Проверяет, является ли тип конструируемым по умолчанию и известно ли, что он не выдает исключение, если создан конструктором по умолчанию.|  
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Проверяет, можно ли создать тип с помощью конструктора копирования и известно ли, что конструктор копирования не создаст исключения.|  
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Проверяет, можно ли создать тип с помощью конструктора перемещения и известно ли, что конструктор перемещения не создаст исключения.|  
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Проверяет, является ли тип назначаемым с использованием определенного типа и известно ли, что назначение не создаст исключения.|  
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Проверяет, является ли тип назначаемым с использованием типа копирования и известно ли, что назначение не создаст исключения.|  
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Проверяет, является ли тип назначаемым с использованием типа перемещения и известно ли, что назначение не создаст исключения.|  
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Проверяет, является ли тип уничтожаемым и известно ли, что деструктор не создаст исключения.|  
|[has_virtual_destructor](http://msdn.microsoft.com/en-us/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|Проверяет, есть ли у типа виртуальный деструктор.|  
  
 Запросы свойств типов  
  
|||  
|-|-|  
|[alignment_of](../standard-library/alignment-of-class.md)|Получает выравнивание типа.|  
|[rank](../standard-library/rank-class.md)|Получает количество измерений массива.|  
|[extent](../standard-library/extent-class.md)|Получает количество элементов в заданном измерении массива.|  
  
 Связи типов  
  
|||  
|-|-|  
|[is_same](../standard-library/is-same-class.md)|Определяет, совпадают ли два типа.|  
|[is_base_of](../standard-library/is-base-of-class.md)|Проверяет, является ли один тип базовым для другого.|  
|[is_convertible](../standard-library/is-convertible-class.md)|Проверяет, можно ли преобразовать один тип в другой.|  
  
 Изменения const или volatile  
  
|||  
|-|-|  
|[add_const](../standard-library/add-const-class.md)|Создает тип `const` из типа.|  
|[add_volatile](../standard-library/add-volatile-class.md)|Создает тип `volatile` из типа.|  
|[add_cv](../standard-library/add-cv-class.md)|Создает тип `const``volatile` из типа.|  
|[remove_const](../standard-library/remove-const-class.md)|Создает отличный от const тип из типа.|  
|[remove_volatile](../standard-library/remove-volatile-class.md)|Создает отличный от volatile тип из типа.|  
|[remove_cv](../standard-library/remove-cv-class.md)|Создает отличный от const и volatile тип из типа.|  
  
 Изменения ссылок  
  
|||  
|-|-|  
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Создает ссылку на тип из типа.|  
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Создает ссылку rvalue на тип из типа|  
|[remove_reference](../standard-library/remove-reference-class.md)|Делает нессылочный тип из типа.|  
  
 Изменения знаков  
  
|||  
|-|-|  
|[make_signed](../standard-library/make-signed-class.md)|Создает тип, если знак присутствует, или наименьший знаковый тип, размер которого не меньше размера типа.|  
|[make_unsigned](../standard-library/make-unsigned-class.md)|Создает тип, если знак отсутствует, или наименьший беззнаковый тип, размер которого не меньше размера типа.|  
  
 Изменения массивов  
  
|||  
|-|-|  
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Создает отличный от массива тип из типа массива.|  
|[remove_extent](../standard-library/remove-extent-class.md)|Создает тип элемента из типа массива.|  
  
 Изменения указателей  
  
|||  
|-|-|  
|[add_pointer](../standard-library/add-pointer-class.md)|Создает указатель на тип из типа.|  
|[remove_pointer](../standard-library/remove-pointer-class.md)|Создает тип из указателя на тип.|  
  
 Другие преобразования  
  
|||  
|-|-|  
|[aligned_storage](../standard-library/aligned-storage-class.md)|Выделяет неинициализированную память для выровненного типа.|  
|[aligned_union](../standard-library/aligned-union-class.md)|Выделяет неинициализированную память для выровненного объединения с нетривиальным конструктором или деструктором.|  
|[common_type](../standard-library/common-type-class.md)|Создает общий тип для всех типов параметров пакета.|  
|[conditional](../standard-library/conditional-class.md)|Если условие имеет значение true, создает первый заданный тип; в противном случае — второй заданный тип.|  
|[decay](../standard-library/decay-class.md)|Создает тип в качестве передаваемого значения. Создает нессылочный, неконстантный или долговременный тип либо указатель на тип.|  
|[enable_if](../standard-library/enable-if-class.md)|Если условие имеет значение true, создает заданный тип; в противном случае — не создает тип.|  
|[result_of](../standard-library/result-of-class.md)|Определяет возвращаемый тип вызываемого типа, который принимает заданные типы аргументов.|  
|[underlying_type](../standard-library/underlying-type-class.md)|Создает базовый целочисленный тип для типа перечисления.|  
  
## <a name="see-also"></a>См. также  
 [\<functional>](../standard-library/functional.md)



