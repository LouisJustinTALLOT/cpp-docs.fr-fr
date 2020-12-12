---
description: 'En savoir plus sur : _rotr8, _rotr16'
title: _rotr8, _rotr16
ms.date: 09/02/2019
f1_keywords:
- _rotr16
- _rotr8
helpviewer_keywords:
- _rotr8 intrinsic
- _rotr16 intrinsic
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
ms.openlocfilehash: 95908956fe34b654c3602f27b495eb58a0b8f8c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307039"
---
# <a name="_rotr8-_rotr16"></a>_rotr8, _rotr16

**Spécifique à Microsoft**

Faire pivoter les valeurs d'entrée vers la droite pour le bit le moins significatif (LSB) d'un nombre spécifié de positions de bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _rotr8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotr16(
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
|`_rotr8`|x86, ARM, x64, ARM64|
|`_rotr16`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Contrairement à une opération de décalage vers la droite, lors de l’exécution d’une rotation vers la droite, les bits de poids faible qui se trouvent en dehors de la fin sont déplacés dans les positions de bit de poids fort.

## <a name="example"></a>Exemple

```cpp
// rotr.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotr8, _rotr16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,
                i, _rotr8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x right by %d bits "
             "gives 0x%x\n",
            s, nBit, _rotr16(s, nBit));
}
```

```Output
Rotating 0x41 right by 0 bits gives 0x41
Rotating 0x41 right by 1 bits gives 0xa0
Rotating 0x41 right by 2 bits gives 0x50
Rotating 0x41 right by 3 bits gives 0x28
Rotating 0x41 right by 4 bits gives 0x14
Rotating 0x41 right by 5 bits gives 0xa
Rotating 0x41 right by 6 bits gives 0x5
Rotating 0x41 right by 7 bits gives 0x82
Rotating unsigned short 0x12 right by 10 bits gives 0x480
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_rotl8, _rotl16](../intrinsics/rotl8-rotl16.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
