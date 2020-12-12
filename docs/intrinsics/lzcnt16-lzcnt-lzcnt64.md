---
description: 'En savoir plus sur les éléments suivants : __lzcnt16, __lzcnt __lzcnt64'
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: 75e2c105d05cfe4620f558a4f44c8ae8b9cd6f8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167732"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Spécifique à Microsoft**

Compte le nombre de zéros non significatifs dans un entier 16, 32 ou 64 bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
dans Entier non signé 16, 32 ou 64 bits à rechercher pour les zéros non significatifs.

## <a name="return-value"></a>Valeur retournée

Nombre de bits de début non significatif dans le `value` paramètre. Si `value` est égal à zéro, la valeur de retour est la taille de l’opérande d’entrée (16, 32 ou 64). Si le bit le plus significatif de `value` est un, la valeur de retour est zéro.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__lzcnt16`|AMD : manipulation avancée des bits (ABM)<br /><br /> Intel : Haswell|
|`__lzcnt`|AMD : manipulation avancée des bits (ABM)<br /><br /> Intel : Haswell|
|`__lzcnt64`|AMD : manipulation avancée des bits (ABM) en mode 64 bits.<br /><br /> Intel : Haswell|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Chacun des intrinsèques génère l' `lzcnt` instruction.  La taille de la valeur `lzcnt` retournée par l’instruction est identique à la taille de son argument.  En mode 32 bits, il n’existe aucun registre à usage général de 64 bits, donc le 64 bits `lzcnt` n’est pas pris en charge.

Pour déterminer la prise en charge matérielle de l' `lzcnt` instruction, appelez l' `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 5 de `CPUInfo[2] (ECX)` . Ce bit aura la valeur 1 si l’instruction est prise en charge, et 0 dans le cas contraire. Si vous exécutez du code qui utilise l’intrinsèque sur du matériel qui ne prend pas en charge l' `lzcnt` instruction, les résultats sont imprévisibles.

Sur les processeurs Intel qui ne prennent pas en charge l' `lzcnt` instruction, l’encodage d’octet d’instruction est exécuté en tant que `bsr` (bit Scan inverse). Si la portabilité du code est un problème, envisagez d’utiliser l’intrinsèque à la `_BitScanReverse` place. Pour plus d’informations, consultez [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

## <a name="example"></a>Exemple

```cpp
// Compile this test with: /EHsc
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
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**FIN spécifique à Microsoft**

Des parties de ce contenu sont protégées par Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
