---
title: sqrt, sqrtf, sqrtl
ms.date: 4/2/2020
api_name:
- sqrtl
- sqrtf
- sqrt
- _o_sqrt
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: 364db84bc20f9f6cfafbdc53e1f2df6da70592df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355580"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt, sqrtf, sqrtl

Calcule la racine carrée.

## <a name="syntax"></a>Syntaxe

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Valeur à virgule flottante non négative

## <a name="remarks"></a>Notes

Étant donné que le CMD permet la surcharge, vous pouvez appeler des surcharges de **sqrt** qui prennent **flotteur** ou **de longs** **types doubles.** Dans un programme C, **sqrt** prend toujours et retourne **double.**

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="return-value"></a>Valeur de retour

Les fonctions **sqrt** retourner la racine carrée de *x*. Par défaut, si *x* est négatif, **sqrt renvoie** un NaN indéfini.

|Entrée|Exception SEH|**_matherr** Exception|
|-----------|-------------------|--------------------------|
|± QNAN,IND|Aucun|_DOMAIN|
|- ∞|Aucun|_DOMAIN|
|x<0|Aucun|_DOMAIN|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**sqrt**, **sqrtf**, **sqrtl**|\<math.h>|\<cmath>|

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>Voir aussi

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
