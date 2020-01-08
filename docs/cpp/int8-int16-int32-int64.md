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
ms.openlocfilehash: 4e793f23581f7dc62a39fcd8c5c504fb5a2ccbc9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301468"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8, __int16, __int32, __int64

**Section spécifique à Microsoft**

Prise en charge des fonctionnalités Microsoft C/C++ pour les types d'entiers dimensionnés. Vous pouvez déclarer des variables de type entier 8, 16, 32 ou 64 bits à l’aide du spécificateur de type **__int**<em>n</em> , où *n* est 8, 16, 32 ou 64.

L'exemple suivant déclare une variable pour chacun de ces types d'entiers dimensionnés :

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les types **__int8**, **__int16**et **__int32** sont des synonymes des types ANSI qui ont la même taille et sont utiles pour écrire du code portable qui se comporte de manière identique sur plusieurs plateformes. Le type de données **__int8** est synonyme du type **char**, **__int16** est synonyme du type **short**et **__int32** est synonyme du type **int**. Le type de **__int64** est synonyme de type **long**long.

Pour la compatibilité avec les versions précédentes, **_int8**, **_int16**, **_int32**et **_int64** sont des synonymes de **__int8**, **__int16**, **__int32**et **__int64** , sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

L’exemple suivant montre qu’un paramètre __int*XX* sera promu en **int**:

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

**Fin de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types intégrés](../cpp/fundamental-types-cpp.md)<br/>
[Plages de types de données](../cpp/data-type-ranges.md)<br/>
