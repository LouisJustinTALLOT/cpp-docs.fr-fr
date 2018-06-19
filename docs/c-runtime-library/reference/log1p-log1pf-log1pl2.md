---
title: log1p, log1pf, log1pl2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- log1p
- log1pf
- log1pl
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 650fb8f7567b4f2f3b0b9032397c2b54a99013dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402746"
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

En cas de réussite, retourne le naturel (base -*e*) dans le journal de (*x* + 1).

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
|±QNaN, indéterminée|Identique à l’entrée|||

Le **errno** a la valeur ERANGE si *x* = -1. Le **errno** a la valeur **EDOM** si *x* < -1.

## <a name="remarks"></a>Notes

Le **log1p** les fonctions peuvent être plus précises que l’utilisation de `log(x + 1)` lorsque *x* est proche de 0.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **log1p** qui acceptent et retournent **float** et **long** **double** types. Dans un programme C, **log1p** accepte et retourne toujours un **double**.

Si *x* est un nombre, cette fonction retourne le logarithme d’obtenir la factorielle (*x* - 1).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
