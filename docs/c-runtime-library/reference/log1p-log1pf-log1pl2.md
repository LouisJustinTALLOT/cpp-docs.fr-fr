---
title: log1p, log1pf, log1pl2
ms.date: 04/05/2018
api_name:
- log1p
- log1pf
- log1pl
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
ms.openlocfilehash: aad6675a832e1715c505026fe11ffe77f1f6d275
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953218"
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

*x*<br/>
Argument à virgule flottante.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne le logarithme naturel (base-*e*) de (*x* + 1).

Sinon, peut retourner l’une des valeurs suivantes :

|Entrée|Résultat|Exception SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Nombres dénormalisés|Identique à l’entrée|UNDERFLOW||
|±0|Identique à l’entrée|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|±SNaN|Identique à l’entrée|INVALID||
|± QNaN, indéfini|Identique à l’entrée|||

La valeur **errno** est définie sur ERANGE si *x* =-1. La valeur **errno** est définie sur **EDOM** si *x* <-1.

## <a name="remarks"></a>Notes

Les fonctions **log1p** peuvent être plus précises que l' `log(x + 1)` utilisation de lorsque *x* est proche de 0.

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **log1p** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **log1p** accepte et retourne toujours un **double**.

Si *x* est un nombre naturel, cette fonction retourne le logarithme de la factorielle de (*x* -1).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
