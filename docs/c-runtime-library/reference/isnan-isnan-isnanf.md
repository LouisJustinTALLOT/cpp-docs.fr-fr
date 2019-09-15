---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953763"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Teste si une valeur à virgule flottante n’est pas un nombre (NAN).

## <a name="syntax"></a>Syntaxe

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur de retour

En C, la macro **IsNaN** et les fonctions **_isnan** et **isnanf** retournent une valeur différente de zéro si l’argument *x* est une valeur NaN ; Sinon, elles retournent 0.

Dans C++, la fonction de modèle **IsNaN** retourne la **valeur true** si l’argument *x* est une valeur NaN ; Sinon, elle retourne **false**.

## <a name="remarks"></a>Notes

Comme une valeur NaN n’est pas comparée à une autre valeur NaN, vous devez utiliser l’une de ces fonctions ou macros pour en détecter une. Une valeur NaN est générée quand le résultat d’une opération à virgule flottante ne peut pas être représenté dans un format à virgule flottante IEEE-754 pour le type spécifié. Pour plus d’informations sur la façon dont une valeur NaN est représentée pour la sortie, consultez [printf](printf-printf-l-wprintf-wprintf-l.md).

Quand elle est C++compilée en tant que, la macro **IsNaN** n’est pas définie et une fonction de modèle **IsNaN** est définie à la place. Il se comporte de la même façon que la macro, mais retourne une valeur de type **bool** au lieu d’un entier.

Les fonctions **_isnan** et **isnanf** sont spécifiques à Microsoft. La fonction **isnanf** est disponible uniquement quand elle est compilée pour x64.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<math.h> ou \<cmath>|
|**_isnan**|\<float.h>|\<float.h> ou \<cfloat>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
