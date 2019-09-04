---
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
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221357"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Section spécifique à Microsoft**

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

*value*\
dans Entier non signé 16, 32 ou 64 bits pour lequel nous souhaitons obtenir le nombre de remplissages.

## <a name="return-value"></a>Valeur de retour

Nombre de `1` bits dans le paramètre de *valeur* .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__popcnt16`|Manipulation de bits avancée|
|`__popcnt`|Manipulation de bits avancée|
|`__popcnt64`|Manipulation de bits avancée en mode 64 bits.|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Chacun des intrinsèques génère l' `popcnt` instruction. En mode 32 bits, il n’existe aucun registre à usage général de 64 bits, donc 64 `popcnt` bits n’est pas pris en charge.

Pour déterminer la prise en charge `popcnt` matérielle de l’instruction `__cpuid` , appelez `InfoType=0x00000001` l’intrinsèque avec et vérifiez `CPUInfo[2] (ECX)`le bit 23 de. Ce bit est égal à 1 si l’instruction est prise en charge et 0 dans le cas contraire. Si vous exécutez du code qui utilise ces fonctions intrinsèques sur du matériel qui `popcnt` ne prend pas en charge l’instruction, les résultats sont imprévisibles.

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

**FIN de la section spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
