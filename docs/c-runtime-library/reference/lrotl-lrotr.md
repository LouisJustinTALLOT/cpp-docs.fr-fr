---
title: _lrotl, _lrotr
ms.date: 04/04/2018
api_name:
- _lrotl
- _lrotr
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
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: ea78aeb8829a80abae345b4e9e6ac3a7bbaddf8b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953029"
---
# <a name="_lrotl-_lrotr"></a>_lrotl, _lrotr

Fait pivoter les bits vers la gauche ( **_lrotl**) ou vers la droite ( **_lrotr**).

## <a name="syntax"></a>Syntaxe

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur à faire pivoter.

*shift*<br/>
Nombre de bits de décalage à appliquer à *value*.

## <a name="return-value"></a>Valeur de retour

Les deux fonctions retournent la valeur soumise à un décalage circulaire. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Les fonctions **_lrotl** et **_lrotr** font pivoter la *valeur* par *décalage* bits. **_lrotl** fait pivoter la valeur restante, vers des bits plus significatifs. **_lrotr** fait pivoter la valeur vers la droite, vers les bits moins significatifs. Les deux fonctions enveloppent les bits ayant fait l’objet d’une rotation d’un bout à l’autre de *value*.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_lrotl**, **_lrotr**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl, _rotl64, _rotr, _rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
