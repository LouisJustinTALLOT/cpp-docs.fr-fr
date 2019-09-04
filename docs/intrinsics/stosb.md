---
title: __stosb
ms.date: 09/02/2019
f1_keywords:
- __stosb
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
ms.openlocfilehash: edf74da4c8b5aa97e542d89f55b3ed8411db9bac
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221214"
---
# <a name="__stosb"></a>__stosb

**Section spécifique à Microsoft**

Génère une instruction de chaîne de`rep stosb`magasin ().

## <a name="syntax"></a>Syntaxe

```C
void __stosb(
   unsigned char* Destination,
   unsigned char Data,
   size_t Count
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Destination de l’opération.

*Métadonnée*\
dans Données à stocker.

*Saut*\
dans Longueur du bloc d’octets à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__stosb`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Le résultat est que les *données* caractères sont écrites dans un bloc de *nombre* d’octets dans la chaîne de *destination* .

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```C
// stosb.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosb)

int main()
{
    unsigned char c = 0x40; /* '@' character */
    unsigned char s[] = "*********************************";

    printf_s("%s\n", s);
    __stosb((unsigned char*)s+1, c, 6);
    printf_s("%s\n", s);

}
```

```Output
*********************************
*@@@@@@**************************
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
