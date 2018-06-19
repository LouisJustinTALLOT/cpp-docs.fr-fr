---
title: rand | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rand
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
- rand
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5289b27ae0749d85b3e4ee60717212acc95536d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405703"
---
# <a name="rand"></a>rand

Génère un nombre pseudo-aléatoire en utilisant un algorithme bien connu et reproductible entièrement. Une version plus par programmation sécurisée de cette fonction est disponible ; consultez [rand_s](rand-s.md). Générer des numéros **rand** ne sont pas sécurisé par chiffrement. Pour plus d’informations sécurisés par chiffrement génération de nombres aléatoires, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque Standard C++ [ \<aléatoire >](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Valeur de retour

**RAND** retourne un nombre pseudo-aléatoire, tel que décrit ci-dessus. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **rand** fonction retourne un entier pseudo-aléatoire comprise entre 0 et **RAND_MAX** (32767). Utilisez le [srand](srand.md) fonction pour amorcer le Générateur de nombres pseudo-aléatoires avant d’appeler **rand**.

Le **rand** fonction génère une séquence connue et qu’il n’est pas appropriée pour une utilisation en tant qu’une fonction de chiffrement. Pour plus d’informations sécurisés par chiffrement génération de nombres aléatoires, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque Standard C++ [ \<aléatoire >](../../standard-library/random.md). Pour plus d’informations sur les problèmes avec **rand** et comment \<aléatoire > les traite, consultez [cette vidéo](http://go.microsoft.com/fwlink/?LinkId=397615).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
