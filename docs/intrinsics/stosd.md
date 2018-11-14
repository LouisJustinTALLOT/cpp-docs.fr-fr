---
title: __stosd
ms.date: 11/04/2016
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c32c439af5544eb561f776381cb1afa98337efcb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328836"
---
# <a name="stosd"></a>__stosd

**Section spécifique à Microsoft**

Génère une instruction de chaîne de magasin (`rep stosd`).

## <a name="syntax"></a>Syntaxe

```
void __stosd(
   unsigned long* Dest,
   unsigned long Data,
   size_t Count
);
```

#### <a name="parameters"></a>Paramètres

*dest*<br/>
[out] La destination de l’opération.

*Données*<br/>
[in] Les données à stocker.

*Nombre*<br/>
[in] La longueur du bloc de mots doubles à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__stosd`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le résultat est que le mot double `Data` est écrit dans un bloc de `Count` mots doubles à l’emplacement de la mémoire vers laquelle pointe `Dest`.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)