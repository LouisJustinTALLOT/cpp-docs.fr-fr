---
title: log1p, log1pf, log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341808"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Calcule le logarithme népérien de 1 plus la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument à virgule flottante.

## <a name="return-value"></a>Valeur de retour

En cas de succès, renvoie le journal naturel (base-*e)* de *(x* - 1).

Sinon, peut retourner l’une des valeurs suivantes :

|Entrée|Résultats|Exception SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Nombres dénormalisés|Comme dans l’entrée|UNDERFLOW||
|0|Comme dans l’entrée|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NaN|NON VALIDE|EDOM|
|-inf|NaN|NON VALIDE|EDOM|
|SNaN|Comme dans l’entrée|NON VALIDE||
|QNaN, indéfini|Comme dans l’entrée|||

La valeur **errno** est réglée à ERANGE si *x* -1. La valeur **errno** est réglée à **EDOM** si *x* < -1.

## <a name="remarks"></a>Notes

Les fonctions **log1p** peuvent être `log(x + 1)` plus précises que l’utilisation lorsque *x* est près de 0.

Étant donné que le CMD permet la surcharge, vous pouvez appeler des surcharges de **log1p** qui prennent et retournent **flotteur** et **de longs** **types doubles.** Dans un programme C, **log1p** prend toujours et renvoie un **double**.

Si *x* est un nombre naturel, cette fonction renvoie le logarithme du factoriel de (*x* - 1).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
