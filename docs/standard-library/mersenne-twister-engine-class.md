---
title: "Класс mersenne_twister_engine | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15294f0372a21c3ce8efe1626c30d1a3d6db23be
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="mersennetwisterengine-class"></a>Класс mersenne_twister_engine
Создает высококачественную последовательность случайных целых чисел на основе алгоритма "Вихрь Мерсенна".  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class UIntType,   
    size_t W, size_t N, size_t M, size_t R,  
    UIntType A, size_t U, UIntType D, size_t S,  
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>  
class mersenne_twister_engine;  
```  
  
#### <a name="parameters"></a>Параметры  
 `UIntType`  
 Беззнаковый целочисленный тип результата. Возможные типы см. в разделе [\<random>](../standard-library/random.md).  
  
 `W`  
 **Размер слова**. Размер каждого слова последовательности состояния в битах. **Предварительные условия**: `2u < W ≤ numeric_limits<UIntType>::digits`  
  
 `N`  
 **Размер состояния**. Количество элементов (значений) в последовательности состояний.  
  
 `M`  
 **Размер сдвига**. Число элементов, которые пропускаются при каждом повороте. **Предварительные условия**: `0 < M ≤ N`  
  
 `R`  
 **Биты маски**. **Предварительные условия**: `R ≤ W`  
  
 `A`  
 **Маска XOR**. **Предварительные условия:** `A ≤ (1u<<W) - 1u`  
  
 `U`, `S`, `T`, `L`  
 **Параметры сдвига при смешивании**. Используются как значения сдвига во время шифрования (смешивания). Предусловие: `U,S,T,L ≤ W`  
  
 `D`, `B`, `C`  
 **Параметры битовой маски смешивания**. Используются как значения битовой маски во время шифрования (смешивания). Предусловие: `D,B,C ≤ (1u<<W) - 1u`  
  
 `F`  
 **Множитель инициализации**. Используется для инициализации последовательности. Предусловие: `F ≤ (1u<<W) - 1u`  
  
## <a name="members"></a>Члены  
  
||||  
|-|-|-|  
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|  
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|  
  
 `default_seed` — это член-константа, определенный как `5489u` и используемый как значение по умолчанию для параметра `mersenne_twister_engine::seed` и конструктор с одним значением.  
  
 Дополнительные сведения о членах механизма см. в разделе [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Примечания  
 Этот класс шаблона описывает механизм случайных чисел, который возвращает значения в замкнутом интервале [`0`, `2`<sup>W</sup> - `1`]. Он содержит большое `W * (N - 1) + R`-разрядное целое значение. Класс извлекает `W` разрядов из этого значения. Когда использованы все разряды, большое значение перемешивается за счет сдвига и смешивания разрядов для получения нового набора разрядов. Состояние механизма — это `N` последних `W`-разрядных значений, если функция `operator()` вызывалась минимум `N` раз. В противном случае — `M` `W`-разрядных значений и `N - M` последних значений начального значения.  
  
 Генератор перемешивает большое значение, используя генерализованный регистр сдвига, заданный значениями сдвига `N` и `M`, значением поворота `R` и условной XOR-маской `A`. Кроме того, разряды регистра сдвига шифруются в соответствии с матрицей, заданной значениями `U`, `D`, `S`, `B`, `T`, `C` и `L`.  
  
 Аргумент шаблона `UIntType` должен быть достаточно большим, чтобы хранить значения до `2`<sup>W</sup> - `1`. Значения других аргументов шаблона должны удовлетворять следующим требованиям: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.  
  
 Хотя можно создать генератор на основе этого механизма напрямую, рекомендуется использовать один из следующих предварительно заданных определений типов.  
  
 `mt19937`: 32-разрядный механизм типа "Вихрь Мерсенна" (Матсумото и Нишимура, 1998).  
  
```  
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,   
    31, 0x9908b0df,   
    11, 0xffffffff,   
    7, 0x9d2c5680,   
    15, 0xefc60000,   
    18, 1812433253> mt19937;  
```  
  
 `mt19937_64`: 64-разрядный механизм типа "Вихрь Мерсенна" (Матсумото и Нишимура, 2000).  
  
```  
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,   
    31, 0xb5026f5aa96619e9ULL,   
    29, 0x5555555555555555ULL,   
    17, 0x71d67fffeda60000ULL,   
    37, 0xfff7eee000000000ULL,   
    43, 6364136223846793005ULL> mt19937_64;  
```  
  
 Дополнительные сведения об алгоритме "Вихрь Мерсенна" см. в статье Википедии [Вихрь Мерсенна](http://go.microsoft.com/fwlink/p/?linkid=402356).  
  
## <a name="example"></a>Пример  
 Пример кода см. в разделе [\<random>](../standard-library/random.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<random>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [\<random>](../standard-library/random.md)

