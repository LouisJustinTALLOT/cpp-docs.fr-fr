---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347924"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Calcule la fonction d'erreur ou la fonction d'erreur complémentaire d'une valeur.

## <a name="syntax"></a>Syntaxe

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Les fonctions **erf** retournent la fonction d’erreur Gauss de *x*. Les fonctions **erfc** retournent la fonction d’erreur Gauss complémentaire de *x*.

## <a name="remarks"></a>Notes

Les fonctions **erf** calculent la fonction d’erreur Gauss de *x*, qui est définie comme:

![Fonction d'erreur de x](media/crt_erf_formula.PNG "Fonction d'erreur de x")

La fonction d’erreur Gauss complémentaire est définie comme 1 - erf(x). Les fonctions **erf** retournent une valeur dans la gamme -1.0 à 1.0. Aucun retour d'erreur. Les fonctions **erfc** retournent une valeur dans la gamme 0 à 2. Si *x* est trop grand pour **erfc**, la variable **errno** est réglée à **ERANGE**.

Étant donné que le CMD permet la surcharge, vous pouvez appeler des surcharges **d’erf** et **d’erfc** qui prennent et retournent **flotter** et **de longs** **types doubles.** Dans un programme C, **erf** et **erfc** toujours prendre et retourner un **double**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**erf**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
