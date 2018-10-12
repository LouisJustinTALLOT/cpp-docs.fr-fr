---
title: __int8, __int16, __int32, __int64 | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b639e7a65bbe206d029a5ba28109170cb0f6a610
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163541"
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64

**Section spécifique à Microsoft**

Prise en charge des fonctionnalités Microsoft C/C++ pour les types d’entiers dimensionnés. Vous pouvez déclarer des 8, 16, 32 ou variables de type entier 64 bits à l’aide de la **__int**<em>n</em> spécificateur, de type où *n* est 8, 16, 32 ou 64.

L'exemple suivant déclare une variable pour chacun de ces types d'entiers dimensionnés :

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les types **__int8**, **__int16**, et **__int32** sont des synonymes des types ANSI qui ont la même taille et sont utiles pour écrire du code portable qui se comporte comme sur plusieurs plateformes. Le **__int8** type de données est synonyme du type **char**, **__int16** est synonyme du type **court**, et **__int32**  est synonyme du type **int**. Le **__int64** type est synonyme du type **longue**.

Pour assurer la compatibilité avec les versions précédentes, **_int8**, **_int16**, **_int32**, et **_int64** sont synonymes de **__int8** , **__int16**, **__int32**, et **__int64** , sauf si option du compilateur [/Za \(désactiver langue Extensions)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

## <a name="example"></a>Exemple

L’exemple suivant montre qu’un __int*xx* paramètre sera promu en **int**:

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types fondamentaux](../cpp/fundamental-types-cpp.md)<br/>
[Plages de types de données](../cpp/data-type-ranges.md)<br/>
