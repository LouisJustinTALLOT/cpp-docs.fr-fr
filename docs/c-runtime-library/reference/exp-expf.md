---
title: exp, expf, expl
ms.date: 04/05/2018
api_name:
- expf
- expl
- exp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: 380f3e861b3ae1ba2f57aa781c32829771612b9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941639"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Calcule la valeur exponentielle.

## <a name="syntax"></a>Syntaxe

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante pour exponentiate le logarithme népérien de base *e* par.

## <a name="return-value"></a>Valeur de retour

Les fonctions **exp** retournent la valeur exponentielle du paramètre à virgule flottante, *x*, en cas de réussite. Autrement dit, le résultat est *e*<sup>*x*</sup>, où *e* est la base du logarithme népérien. En cas de dépassement de capacité, la fonction retourne INF (infini) et en négatif, **exp** retourne 0.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± NaN quiet, indéterminé|Aucun|_DOMAIN|
|± Infini|INVALID|_DOMAIN|
|x ≥ 7,097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7,083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

La fonction **exp** a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). Consultez [_set_SSE2_enable](set-sse2-enable.md) pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent.

## <a name="remarks"></a>Notes

C++autorise la surcharge, donc vous pouvez appeler des surcharges de **exp** qui acceptent un argument **float** ou **long double** . Dans un programme C, **exp** prend toujours et retourne une valeur **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C requis|En-tête C++ requis|
|--------------|---------------------|---|
|**exp**, **expf**, **expl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
