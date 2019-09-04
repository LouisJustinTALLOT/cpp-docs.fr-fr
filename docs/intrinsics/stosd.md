---
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c46bb124390ff23d79361c66530493c48faf3f0a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219982"
---
# <a name="__stosd"></a>__stosd

**Section spécifique à Microsoft**

Génère une instruction de chaîne de`rep stosd`magasin ().

## <a name="syntax"></a>Syntaxe

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Destination de l’opération.

*Métadonnée*\
dans Données à stocker.

*Saut*\
dans Longueur du bloc de mots doubles à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__stosd`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Le résultat est que les *données* de mot double sont écrites dans un bloc de *nombre* de mots doubles à l’emplacement de mémoire vers lequel pointe la *destination*.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemples

```C
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

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
