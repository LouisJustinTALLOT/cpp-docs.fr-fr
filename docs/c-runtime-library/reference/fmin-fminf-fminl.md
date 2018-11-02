---
title: fmin, fminf, fminl
ms.date: 04/05/2018
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: f73853e18bd5d7f699cd2c3109fe5fb830859bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464361"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Détermine la plus petite de deux valeurs spécifiées.

## <a name="syntax"></a>Syntaxe

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur à comparer.

*y*<br/>
Deuxième valeur à comparer.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne le plus petit de *x* ou *y*.

|Entrée|Résultat|
|-----------|------------|
|*x* est NaN|*y*|
|*y* est NaN|*x*|
|*x* et *y* sont des valeurs NaN|NaN|

La fonction ne provoque pas [_matherr](matherr.md) pour être appelé, provoquer des exceptions à virgule flottante, ou de modifier la valeur de **errno**.

## <a name="remarks"></a>Notes

Sachant que C++ autorise la surcharge, vous pouvez appeler des surcharges de **Fmax** qui acceptent et retournent **float** et **long** **double** types. Dans un programme C, **Fmax** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**Fmax**, **fminf**, **fminl**|C : \<math.h><br />C++ : \<math.h> ou \<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
