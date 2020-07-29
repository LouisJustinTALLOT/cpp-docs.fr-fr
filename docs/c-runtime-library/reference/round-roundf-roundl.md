---
title: round, roundf, roundl
ms.date: 4/2/2020
api_name:
- round
- roundl
- roundf
- _o_round
- _o_roundf
- _o_roundl
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- roundf
- roundl
- round
helpviewer_keywords:
- roundl function
- round function
- roundf function
ms.assetid: 6be90877-193c-4b80-a32b-c3eca33f9c6f
ms.openlocfilehash: ed7f8457373466e442d7998cee0a14389de4321e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226175"
---
# <a name="round-roundf-roundl"></a>round, roundf, roundl

Arrondit une valeur à virgule flottante à l’entier le plus proche.

## <a name="syntax"></a>Syntaxe

```C
double round(
   double x
);
float round(
   float x
);  // C++ only
long double round(
   long double x
);  // C++ only
float roundf(
   float x
);
long double roundl(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à arrondir.

## <a name="return-value"></a>Valeur de retour

Les fonctions **Round** retournent une valeur à virgule flottante qui représente l’entier le plus proche de *x*. Les valeurs médianes sont arrondies en s’éloignant de zéro, indépendamment du paramètre du mode d’arrondi à virgule flottante. Aucun retour d'erreur.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges d’une **séquence** qui acceptent et retournent des **`float`** **`long double`** valeurs et. Dans un programme C, **Round** prend toujours et retourne un **`double`** .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**Round**, **roundf,**, **arrondi**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_round.c
// Build with: cl /W3 /Tc crt_round.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("round(%f) is %.0f\n", x, round(x));
   printf("round(%f) is %.0f\n", -x, round(-x));
   printf("roundf(%f) is %.0f\n", y, roundf(y));
   printf("roundf(%f) is %.0f\n", -y, roundf(-y));
   printf("roundl(%Lf) is %.0Lf\n", z, roundl(z));
   printf("roundl(%Lf) is %.0Lf\n", -z, roundl(-z));
}
```

```Output
round(2.499999) is 2
round(-2.499999) is -2
roundf(2.800000) is 3
roundf(-2.800000) is -3
roundl(2.500000) is 3
roundl(-2.500000) is -3
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
