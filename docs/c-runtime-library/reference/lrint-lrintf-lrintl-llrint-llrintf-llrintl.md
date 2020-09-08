---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
description: Informations de référence sur l’API pour lrint (), lrintf (), lrintl (), llrint (), llrintf () et llrintl (); qui arrondit la valeur à virgule flottante spécifiée à la valeur intégrale la plus proche, en utilisant le mode d’arrondi et la direction actuels.
ms.date: 9/1/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: f208c183400aac7a110bb6fd87398d4377fe8f06
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555018"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Arrondit la valeur à virgule flottante spécifiée à la valeur intégrale la plus proche, en utilisant le mode et la direction de l’arrondi actuels.

## <a name="syntax"></a>Syntaxe

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);

#define lrint(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à arrondir.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne la valeur intégrale arrondie de *x*.

|Problème|Renvoie|
|-----------|------------|
|*x* est en dehors de la plage du type de retour<br /><br /> *x* = ± ∞<br /><br /> *x* = Nan|Déclenche **FE_INVALID** et retourne zéro (0).|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **lrint** et **llrint** qui acceptent **`float`** les **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **lrint** et **llrint** prennent toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `llrint()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Si *x* ne représente pas l’équivalent à virgule flottante d’une valeur intégrale, ces fonctions déclenchent **FE_INEXACT**.

**Spécifique à Microsoft**: lorsque le résultat est en dehors de la plage du type de retour, ou lorsque le paramètre est une valeur NaN ou l’infini, la valeur de retour est définie par l’implémentation. Le compilateur Microsoft retourne zéro (0).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|
|**lrint** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)
