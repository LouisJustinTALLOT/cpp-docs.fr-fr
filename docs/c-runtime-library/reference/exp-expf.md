---
title: EXP, expf, expl | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- expf
- expl
- exp
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _expl
- expf
- expl
- exp
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9569eee475a80fc5c08c2ec1d099cf627c7b5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396217"
---
# <a name="exp-expf-expl"></a>EXP, expf, expl

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
La virgule flottante valeur Elever à la puissance la base du logarithme népérien *e* par.

## <a name="return-value"></a>Valeur de retour

Le **exp** fonctions retournent la valeur exponentielle du paramètre à virgule flottante, *x*, en cas de réussite. Autrement dit, le résultat est *e*<sup>*x*</sup>, où *e* est la base du logarithme népérien. De dépassement de capacité, la fonction retourne INF (infini) et de dépassement de capacité négatif, **exp** retourne 0.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± Valeur NaN silencieuse, indéterminé|Aucun|_DOMAIN|
|Nombre infini de ±|INVALID|_DOMAIN|
|x ≥ 7,097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7,083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

Le **exp** possède une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Consultez [_set_SSE2_enable](set-sse2-enable.md) pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent.

## <a name="remarks"></a>Notes

C++ autorise la surcharge, vous pouvez appeler des surcharges de **exp** qui prennent un **float** ou **long double** argument. Dans un programme C, **exp** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C requis|En-tête C++ requis|
|--------------|---------------------|---|
|**EXP**, **expf**, **expl**|\<math.h>|\<cmath> ou \<math.h>|

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
