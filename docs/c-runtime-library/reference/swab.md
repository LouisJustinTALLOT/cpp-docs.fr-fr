---
title: _swab
ms.date: 11/04/2016
api_name:
- _swab
- stdlib/_swab
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: b0faba55c42023f4d66adae68de6be2c1ab009a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946286"
---
# <a name="_swab"></a>_swab

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

*src*<br/>
Données à copier et échanger.

*dest*<br/>
Emplacement de stockage des données échangées.

*n*<br/>
Nombre d’octets à copier et échanger.

## <a name="return-value"></a>Valeur de retour

La fonction **écouvillon** ne retourne pas de valeur. La fonction définit **errno** sur **EINVAL** si le pointeur *src* ou *dest* a la valeur null ou si *n* est inférieur à zéro et que le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ce code de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Si *n* est pair, la fonction **_swab** copie *n* octets de *src*, échange chaque paire d’octets adjacents et stocke le résultat à la *destination*. Si *n* est impair, **_swab** copie et permute les *n*premiers octets de *src*, et l’octet final n’est pas copié. La fonction **_swab** est généralement utilisée pour préparer des données binaires pour le transfert vers un ordinateur qui utilise un ordre d’octet différent.

## <a name="requirements"></a>Configuration requise

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
