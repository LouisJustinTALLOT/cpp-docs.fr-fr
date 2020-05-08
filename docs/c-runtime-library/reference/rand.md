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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8f2a4d00310671e8ba80055e38e479e348562ac2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919525"
---
# <a name="rand"></a>rand

Génère un nombre Pseudo-aléatoire à l’aide d’un algorithme bien connu et entièrement reproductible. Une version plus sécurisée par programmation de cette fonction est disponible. consultez [rand_s](rand-s.md). Les nombres générés par **Rand** ne sont pas sécurisés par chiffrement. Pour plus de génération de nombres aléatoires sécurisés par chiffrement, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque standard C++ dans des [ \<>aléatoires ](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Valeur de retour

**Rand** retourne un nombre Pseudo-aléatoire, comme décrit ci-dessus. Aucun retour d'erreur.

## <a name="remarks"></a>Notes 

La fonction **Rand** retourne un entier Pseudo-aléatoire compris entre 0 et **RAND_MAX** (32767). Utilisez la fonction [srand](srand.md) pour amorcer le générateur de nombres pseudo-aléatoires avant d’appeler **Rand**.

La fonction **Rand** génère une séquence connue et ne convient pas pour une utilisation en tant que fonction de chiffrement. Pour plus de génération de nombres aléatoires sécurisés par chiffrement, utilisez [rand_s](rand-s.md) ou les fonctions déclarées dans la bibliothèque standard C++ dans des [ \<>aléatoires ](../../standard-library/random.md). Pour plus d’informations sur les problèmes avec **Rand** et \<sur la façon dont les> aléatoires corrigent ces lacunes, consultez cette vidéo intitulée [Rand, jugé dangereux](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
