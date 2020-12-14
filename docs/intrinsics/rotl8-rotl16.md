---
description: 'En savoir plus sur : _rotl8, _rotl16'
title: _rotl8, _rotl16
ms.date: 09/02/2019
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 71ef10bb6af750fc08955fbdf82975b1ed32fa94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211906"
---
# <a name="_rotl8-_rotl16"></a>_rotl8, _rotl16

**Spécifique à Microsoft**

Faire pivoter les valeurs d'entrée vers la gauche pour le bit le plus significatif (MSB) d'un nombre spécifié de positions de bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
   unsigned short value,
   unsigned char shift
);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
dans Valeur à faire pivoter.

*majuscule*\
dans Nombre de bits à faire pivoter.

## <a name="return-value"></a>Valeur retournée

Valeur ayant fait l'objet d'une rotation.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_rotl8`|x86, ARM, x64, ARM64|
|`_rotl16`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Contrairement à une opération de décalage vers la gauche, lors de l’exécution d’une rotation vers la gauche, les bits de poids fort qui se trouvent en dehors de l’extrémité supérieure sont déplacés dans les positions de bits les moins significatives.

## <a name="example"></a>Exemple

```cpp
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
