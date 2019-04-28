---
title: pow, powf, powl
ms.date: 04/05/2018
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: edf6116413caba52f9311f03bdfcc1d87e68a011
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232232"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Calcule *x* élevé à la puissance de *y*.

## <a name="syntax"></a>Syntaxe

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Base.

*y*<br/>
Exposant.

## <a name="return-value"></a>Valeur de retour

Retourne la valeur de *x*<sup>*y*</sup>. Aucun message d’erreur n’est imprimé en cas de dépassement de capacité positif ou négatif.

|Valeurs de x et y|Valeur de retour de pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 et *y* == 0.0|1|
|*x* == 0.0 et *y* == 0.0|1|
|*x* == 0.0 et *y* < 0|INF|

## <a name="remarks"></a>Notes

**Pow** ne reconnaît pas les valeurs à virgule flottante intégrales supérieures à 2<sup>64</sup> (par exemple, 1.0E100).

**Pow** a une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Pour obtenir des informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

Sachant que C++ autorise la surcharge, vous pouvez appeler une des diverses surcharges de **pow**. Dans un programme C, **pow** accepte toujours deux **double** valeurs et retourne un **double** valeur.

La surcharge `pow(int, int)` n’est plus disponible. Si vous utilisez cette surcharge, le compilateur peut émettre [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Pour éviter ce problème, effectuez un cast le premier paramètre de **double**, **float**, ou **long** **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-|-|-|
|**pow**, **powf**, **powl**|\<math.h>|\<math.h> ou \<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
