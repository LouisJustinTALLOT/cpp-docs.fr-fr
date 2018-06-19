---
title: _swab | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeedb217466262d8643a851b5f93cb9ac26fb0a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408439"
---
# <a name="swab"></a>_swab

Échange des octets.

## <a name="syntax"></a>Syntaxe

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Paramètres

*src* copiés et remplacez des données.

*dest* emplacement de stockage pour les données échangées.

*n* nombre d’octets à copier et échangés.

## <a name="return-value"></a>Valeur de retour

Le **swab** fonction ne retourne pas de valeur. La fonction définit **errno** à **EINVAL** si le *src* ou *dest* pointeur est null ou *n* est inférieure à zéro et le paramètre non valide de gestionnaire est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ce code de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Si *n* est pair, le **_swab** fonction copies *n* octets à partir de *src*permute chaque paire d’octets adjacents et stocke le résultat à *dest*. Si *n* est impair, **_swab** copie et remplace le premier *n*-1 octets de *src*, et le dernier octet n’est pas copié. Le **_swab** fonction est généralement utilisée pour préparer les données binaires pour le transfert vers un ordinateur qui utilise un ordre d’octets différents.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_swab**|C : \<stdlib.h> C++ : \<cstdlib> ou \<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
