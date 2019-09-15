---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 04/05/2018
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
ms.openlocfilehash: 72870c3548f0fd6972183b0c090708c6eddc591e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953122"
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

*x*<br/>
Valeur à arrondir.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur intégrale arrondie de *x*.

|Problème|Renvoie|
|-----------|------------|
|*x* est en dehors de la plage du type de retour<br /><br /> *x* = ±∞<br /><br /> *x* = Nan|Déclenche **FE_INVALID** et retourne zéro (0).|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **lrint** et **llrint** qui prennent des types **float** et **long** **double** . Dans un programme C, **lrint** et **llrint** prennent toujours un **double**.

Si *x* ne représente pas l’équivalent à virgule flottante d’une valeur intégrale, ces fonctions déclenchent **FE_INEXACT**.

**Spécifique à Microsoft**: Lorsque le résultat est en dehors de la plage du type de retour, ou lorsque le paramètre est une valeur NaN ou l’infini, la valeur de retour est définie par l’implémentation. Le compilateur Microsoft retourne zéro (0).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
