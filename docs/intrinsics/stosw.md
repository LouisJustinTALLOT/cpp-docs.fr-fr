---
description: 'En savoir plus sur : __stosw'
title: __stosw
ms.date: 09/02/2019
f1_keywords:
- __stosw
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
ms.openlocfilehash: 2995276fb255858d6c3dd9f438487726e75fdf1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143687"
---
# <a name="__stosw"></a>__stosw

**Spécifique à Microsoft**

Génère une instruction de chaîne de magasin ( `rep stosw` ).

## <a name="syntax"></a>Syntaxe

```C
void __stosw(
   unsigned short* Destination,
   unsigned short Data,
   size_t Count
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Destination de l’opération.

*Données*\
dans Données à stocker.

*Saut*\
dans Longueur du bloc de mots à écrire.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__stosw`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Le résultat est que le mot *Data* est écrit dans un bloc de mots *Count* dans la chaîne de *destination* .

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```C
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
