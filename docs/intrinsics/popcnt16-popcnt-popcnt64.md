---
description: 'En savoir plus sur les éléments suivants : __popcnt16, __popcnt __popcnt64'
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: cb95ff09d589cfd9a9cfc438d0334cf68f073825
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257522"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Spécifique à Microsoft**

Compte le nombre de `1` bits (nombre de remplissage) dans un entier non signé 16, 32 ou 64 bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
dans Entier non signé 16, 32 ou 64 bits pour lequel nous souhaitons obtenir le nombre de remplissages.

## <a name="return-value"></a>Valeur retournée

Nombre de `1` bits dans le paramètre de *valeur* .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__popcnt16`|Manipulation de bits avancée|
|`__popcnt`|Manipulation de bits avancée|
|`__popcnt64`|Manipulation de bits avancée en mode 64 bits.|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Chacun des intrinsèques génère l' `popcnt` instruction. En mode 32 bits, il n’existe aucun registre à usage général de 64 bits, donc 64 bits `popcnt` n’est pas pris en charge.

Pour déterminer la prise en charge matérielle de l' `popcnt` instruction, appelez l' `__cpuid` intrinsèque avec `InfoType=0x00000001` et vérifiez le bit 23 de `CPUInfo[2] (ECX)` . Ce bit est égal à 1 si l’instruction est prise en charge et 0 dans le cas contraire. Si vous exécutez du code qui utilise ces fonctions intrinsèques sur du matériel qui ne prend pas en charge l' `popcnt` instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```cpp
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**FIN spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
