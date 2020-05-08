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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 6f3eb1bd791e645407b09a99a8c8e96025ca47e3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912229"
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

*x*<br/>
Valeur dont le gamma doit être trouvé.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur gamma de *x*.

Une erreur de plage peut se produire si l’amplitude de *x* est trop grande ou trop petite pour le type de données. Une erreur de domaine ou une erreur de plage peut se produire si *x* <= 0.

|Problème|Renvoie|
|-----------|------------|
|x = ± 0|± INFINI|
|x = entier négatif|NaN|
|x =-infini|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Erreur de domaine|NaN|
|Erreur de pôle|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|
|Erreur de plage avec dépassement|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|
|erreur de plage avec dépassement de capacité négatif|valeur correcte après arrondi|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes 

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **tgamma** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **tgamma** accepte et retourne toujours un **double**.

Si x est un nombre naturel, cette fonction retourne la factorielle de (x-1).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
