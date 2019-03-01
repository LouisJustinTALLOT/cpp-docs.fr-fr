---
title: rand
ms.date: 1/02/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 868c6239ac1b86dfc9ac72cc8cc83d1ba3002b4a
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210417"
---
# <a name="rand"></a>rand

Génère un nombre pseudo-aléatoire en utilisant un algorithme connu et reproductible entièrement. Une version plus par programmation sécurisée de cette fonction est disponible ; consultez [rand_s](rand-s.md). Générer des numéros **rand** ne sont pas sécurisés par chiffrement. Pour plus d’informations sécurisées par chiffrement la génération de nombres aléatoires, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque Standard C++ [ \<aléatoire >](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Valeur de retour

**RAND** retourne un nombre pseudo-aléatoire, comme décrit ci-dessus. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **rand** fonction retourne un entier pseudo-aléatoire compris dans la plage 0 à **RAND_MAX** (32 767). Utilisez le [srand](srand.md) (fonction) pour amorcer le Générateur de nombres pseudo-aléatoires avant d’appeler **rand**.

Le **rand** fonction génère une séquence connue et n’est pas appropriée pour une utilisation comme une fonction de chiffrement. Pour plus d’informations sécurisées par chiffrement la génération de nombres aléatoires, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque Standard C++ [ \<aléatoire >](../../standard-library/random.md). Pour savoir quel est le problème avec **rand** et comment \<aléatoire > aborde ces problèmes, consultez cette vidéo intitulée [rand considérés comme dangereux](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

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
