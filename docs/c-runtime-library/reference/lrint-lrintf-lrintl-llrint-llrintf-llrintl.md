---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
dev_langs:
- C++
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ace427267a45c87213f62276e1d7799f27db1cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401257"
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

En cas de réussite, retourne la valeur intégrale arrondie du *x*.

|Problème|Retourner|
|-----------|------------|
|*x* est en dehors de la plage du type de retour<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Déclenche **FE_INVALID** et renvoie zéro (0).|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **lrint** et **llrint** acceptant **float** et **long**  **Double** types. Dans un programme C, **lrint** et **llrint** ont toujours une **double**.

Si *x* ne représente pas l’équivalent à virgule flottante d’une valeur intégrale, ces fonctions de déclenchement **FE_INEXACT**.

**Section spécifique à Microsoft** : quand le résultat se situe hors de la plage du type de retour ou que le paramètre est une valeur NaN ou l’infini, la valeur de retour est définie par l’implémentation. Le compilateur Microsoft retourne zéro (0).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
