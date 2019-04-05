---
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 11/04/2016
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
ms.openlocfilehash: 333d9f2b23fb90388af8395945256956c9222ab9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041336"
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Section spécifique à Microsoft**

Nombres le nombre d’espace de début zéros à droite dans un 16, 32 ou entier 64 bits.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Paramètres

*par défaut*<br/>
[in] Le 16, 32 ou entier non signé 64 bits pour rechercher des zéros non significatifs.

## <a name="return-value"></a>Valeur de retour

Le nombre de zéros d’en-tête dans le `value` paramètre. Si `value` est égal à zéro, la valeur de retour est la taille de l’opérande d’entrée (16, 32 ou 64). Si le bit de poids de `value` est 1, la valeur de retour est égale à zéro.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__lzcnt16`|AMD : Manipulation de bits avancés (ABM)<br /><br /> Intel : Haswell|
|`__lzcnt`|AMD : Manipulation de bits avancés (ABM)<br /><br /> Intel : Haswell|
|`__lzcnt64`|AMD : Avancées Bit Manipulation (ABM) en mode 64 bits.<br /><br /> Intel : Haswell|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Chacune de ces fonctions intrinsèques génère la `lzcnt` instruction.  La taille de la valeur que la `lzcnt` instruction retourne est identique à la taille de son argument.  En mode 32 bits il n’existe aucune registres 64 bits à usage général, par conséquent, ne 64 bits `lzcnt`.

Pour déterminer la prise en charge matérielle pour le `lzcnt` appel le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 5 de `CPUInfo[2] (ECX)`. Ce bit sera égale à 1 si l’instruction est pris en charge et 0 dans le cas contraire. Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `lzcnt` instruction, les résultats sont imprévisibles.

Sur les processeurs Intel ne prenant pas en charge la `lzcnt` obtenir des instructions, l’octet d’encodage instruction est exécutée en tant que `bsr` (bit analyse inverse). Si la portabilité du code pose problème, envisagez d’utiliser le `_BitScanReverse` intrinsèque à la place. Pour plus d’informations, consultez [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

## <a name="example"></a>Exemple

```
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

**FIN de la section spécifique à Microsoft**

Certaines parties de ce contenu sont Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)
