---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703088"
---
# <a name="isnan-isnan-isnanf"></a>isnan, _isnan, _isnanf

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

En C, le **isnan** macro et **_isnan** et **_isnanf** fonctions retournent une valeur différente de zéro si l’argument *x* est une valeur NAN ; sinon ils retourne 0.

En C++, le **isnan** fonction de modèle retourne **true** si l’argument *x* est une valeur NaN ; sinon, elle retourne **false**.

## <a name="remarks"></a>Notes

Car une valeur NaN n’est pas considéré comme étant égale à toute autre valeur NaN, vous devez utiliser une de ces fonctions ou les macros pour détecter une. Une valeur NaN est générée lorsque le résultat d’une opération à virgule flottante ne peut pas être représenté au format de virgule flottante IEEE-754 pour le type spécifié. Pour plus d’informations sur la façon dont une valeur NaN est représentée pour la sortie, consultez [printf](printf-printf-l-wprintf-wprintf-l.md).

Lors de la compilation en C++, le **isnan** macro n’est pas définie et un **isnan** fonction avec modèle est définie à la place. Il se comporte de la même façon que la macro, mais retourne une valeur de type **bool** au lieu d’un entier.

Le **_isnan** et **_isnanf** fonctions sont spécifiques à Microsoft. Le **_isnanf** fonction est uniquement disponible lors de la compilation pour x64.

## <a name="requirements"></a>Spécifications

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
