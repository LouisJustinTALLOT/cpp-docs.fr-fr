---
title: imaxabs
ms.date: 04/05/2018
api_name:
- imaxabs
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
- imaxabs
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
ms.openlocfilehash: c1f20c4de2ff9070bae3bfaeb8ba2d97d87d2d4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954689"
---
# <a name="imaxabs"></a>imaxabs

Calcule la valeur absolue d’un entier de n’importe quelle taille.

## <a name="syntax"></a>Syntaxe

```C
intmax_t imaxabs(
   intmax_t n
);
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Valeur entière.

## <a name="return-value"></a>Valeur de retour

La fonction **imaxabs** retourne la valeur absolue de l’argument. Aucun retour d'erreur.

> [!NOTE]
> Étant donné que la plage d’entiers négatifs qui peuvent être représentés à l’aide de **intmax_t** est supérieure à la plage d’entiers positifs qui peuvent être représentés, il est possible de fournir un argument à **imaxabs** qui ne peut pas être converti. Si la valeur absolue de l’argument ne peut pas être représentée par le type de retour, le comportement de **imaxabs** n’est pas défini.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_imaxabs.c
// Build using: cl /W3 /Tc crt_imaxabs.c
// This example calls imaxabs to compute an
// absolute value, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x = LLONG_MIN + 2;

   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));
}
```

```Output
The absolute value of -9223372036854775806 is 9223372036854775806
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
