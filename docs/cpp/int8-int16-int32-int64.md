---
title: __int8, __int16, __int32, __int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 7888a282fffbaa2a23783c3875e02838fd0b1826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227398"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8, __int16, __int32, __int64

**Spécifique à Microsoft**

Prise en charge des fonctionnalités Microsoft C/C++ pour les types d'entiers dimensionnés. Vous pouvez déclarer des variables de type entier 8, 16, 32 ou 64 bits à l’aide du **`__intN`** spécificateur de type, où ***`N`*** est 8, 16, 32 ou 64.

L'exemple suivant déclare une variable pour chacun de ces types d'entiers dimensionnés :

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les types **`__int8`** , **`__int16`** et **`__int32`** sont des synonymes des types ANSI qui ont la même taille, et sont utiles pour écrire du code portable qui se comporte de manière identique sur plusieurs plateformes. Le **`__int8`** type de données est synonyme de type **`char`** , **`__int16`** est synonyme de type **`short`** et **`__int32`** est synonyme de type **`int`** . Le **`__int64`** type est synonyme de type **`long long`** .

Pour la compatibilité avec les versions antérieures, **`_int8`** ,, **`_int16`** **`_int32`** et **`_int64`** sont des synonymes de **`__int8`** , **`__int16`** , et, **`__int32`** **`__int64`** sauf si l’option de compilateur [ `/Za` \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

L’exemple suivant montre qu’un `__intN` paramètre sera promu **`int`** :

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types intégrés](../cpp/fundamental-types-cpp.md)<br/>
[Plages de types de données](../cpp/data-type-ranges.md)<br/>
