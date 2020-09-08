---
title: log2, log2f, log2l
description: Informations de référence sur les API pour log2, log2f, et log2l ; qui détermine le logarithme binaire (base 2) de la valeur spécifiée.
ms.date: 9/1/2020
api_name:
- log2
- log2l
- log2f
- _o_log2
- _o_log2f
- _o_log2l
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 37319560891dbd64030495750aaf347d9dedd7e7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555356"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Détermine le logarithme (base 2) binaire de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);

#define log2(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur dont le logarithme base 2 doit être déterminé.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne la valeur retournée log2 *x*.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|Erreur de domaine|NaN|
|Erreur de pôle|-HUGE_VAL, -HUGE_VALF ou -HUGE_VALL|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Si *x* est un entier, cette fonction retourne essentiellement l’index de base zéro du bit le plus significatif 1 de *x*.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**log2**, **log2f,**, **log2l**|\<math.h>|\<cmath>|
|**log2** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
