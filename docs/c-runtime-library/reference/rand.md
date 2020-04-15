---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 944c512d0102b459afc2924ef7515311e46cd43c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338164"
---
# <a name="rand"></a>rand

Génère un numéro de pseudorandom en utilisant un algorithme bien connu et entièrement reproductible. Une version plus programmatiquement sécurisée de cette fonction est disponible; voir [rand_s](rand-s.md). Les chiffres générés par **le rand** ne sont pas cryptographiquement sécurisés. Pour une génération de nombres aléatoires plus cryptographiquement sécurisée, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la Bibliothèque standard de CMD au [ \<hasard>. ](../../standard-library/random.md)

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Valeur de retour

**rand** retourne un nombre de pseudorandom, comme décrit ci-dessus. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

La fonction **rand** retourne un intégrer pseudorandom dans la gamme 0 à **RAND_MAX** (32767). Utilisez la fonction [srand](srand.md) pour semer le générateur pseudorandom-numéro avant d’appeler **rand**.

La fonction **rand** génère une séquence bien connue et n’est pas appropriée pour une utilisation comme fonction cryptographique. Pour une génération de nombres aléatoires plus cryptographiquement sécurisée, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la Bibliothèque standard de CMD au [ \<hasard>. ](../../standard-library/random.md) Pour plus d’informations **rand** sur ce \<qui ne va pas avec rand et comment> aléatoires répond à ces lacunes, voir cette vidéo intitulée [rand Considéré nuisible](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**Rand**|\<stdlib.h>|

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

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
