---
title: imaxabs | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- imaxabs
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
- imaxabs
dev_langs:
- C++
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc756c4516ec5770fff6d46799740f3458fc112d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
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

Le **imaxabs** fonction retourne la valeur absolue de l’argument. Aucun retour d'erreur.

> [!NOTE]
> Étant donné que la plage d’entiers négatifs qui peuvent être représentées à l’aide de **intmax_t** est supérieure à la plage d’entiers positifs qui peuvent être représentés, il est possible de fournir un argument à **imaxabs** qui ne peut pas être converti. Si la valeur absolue de l’argument ne peut pas être représentée par la valeur de retour de type, le comportement de **imaxabs** n’est pas défini.

## <a name="requirements"></a>Spécifications

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
