---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362506"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Détermine la fonction gamma de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Valeur dont le gamma doit être trouvé.

## <a name="return-value"></a>Valeur de retour

En cas de succès, retourne le gamma de *x*.

Une erreur de portée peut se produire si l’ampleur de *x* est trop grande ou trop petite pour le type de données. Une erreur de domaine ou une erreur de portée peut se produire si *x* <0.

|Problème|Renvoie|
|-----------|------------|
|x 0 euros|L’INFINI|
|x = entier négatif|NaN|
|x -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Erreur de domaine|NaN|
|Erreur de pôle|HUGE_VAL, HUGE_VALF ou HUGE_VALL|
|Erreur de plage avec dépassement|HUGE_VAL, HUGE_VALF ou HUGE_VALL|
|erreur de plage avec dépassement de capacité négatif|valeur correcte après arrondi|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Étant donné que le CMD permet la surcharge, vous pouvez appeler des surcharges de **tgamma** qui prennent et retournent **flotteur** et **de longs** **types doubles.** Dans un programme C, **tgamma** prend et renvoie toujours un **double**.

Si x est un nombre naturel, cette fonction retourne la factorielle de (x-1).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
