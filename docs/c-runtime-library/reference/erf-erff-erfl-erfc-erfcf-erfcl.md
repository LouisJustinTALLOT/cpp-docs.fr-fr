---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 04/05/2018
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: 5723286add75a57844f177b9df5d86eb15080229
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450047"
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

*x*<br/>
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Le **erf** fonctions retournent le Gauss fonction d’erreur de *x*. Le **erfc** fonctions retournent de Gauss complémentaire la fonction d’erreur de *x*.

## <a name="remarks"></a>Notes

Le **erf** fonctions calculent la fonction d’erreur de Gauss de *x*, qui est définie comme :

![Fonction d’erreur de x](media/crt_erf_formula.PNG "CRT_erf_formula")

La fonction d’erreur de Gauss complémentaire est définie en tant que 1 - ERF. Le **erf** fonctions retournent une valeur dans la plage -1,0 à 1,0. Aucun retour d'erreur. Le **erfc** fonctions retournent une valeur dans la plage 0 à 2. Si *x* est trop grande pour **erfc**, le **errno** variable est définie sur **ERANGE**.

Sachant que C++ autorise la surcharge, vous pouvez appeler des surcharges de **erf** et **erfc** qui acceptent et retournent **float** et **long** **double** types. Dans un programme C, **erf** et **erfc** acceptent et retournent toujours un **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**ERF**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
