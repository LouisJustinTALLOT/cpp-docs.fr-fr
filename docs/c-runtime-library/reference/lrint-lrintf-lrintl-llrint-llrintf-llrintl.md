---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6283cffaa094af4484d48781b5bb92d0339d38d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341667"
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
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Valeur à arrondir.

## <a name="return-value"></a>Valeur de retour

En cas de succès, retourne la valeur intégrale arrondie de *x*.

|Problème|Renvoie|
|-----------|------------|
|*x* est en dehors de la plage du type de retour<br /><br /> *x* -<br /><br /> *x* NaN|Relance **FE_INVALID** et retourne zéro (0).|

## <a name="remarks"></a>Notes

Parce que le CMD permet la surcharge, vous pouvez appeler des surcharges de **lrint** et **de llrint** qui prennent **flotteur** et **de longs** **types doubles.** Dans un programme C, **lrint** et **llrint** toujours prendre un **double**.

Si *x* ne représente pas l’équivalent de point flottant d’une valeur intégrale, ces fonctions soulèvent **FE_INEXACT**.

**Microsoft spécifique**: Lorsque le résultat est en dehors de la plage du type de retour, ou lorsque le paramètre est un NaN ou une infinité, la valeur de retour est définie. Le compilateur Microsoft retourne zéro (0).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
