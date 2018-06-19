---
title: isnan, _isnan, _isnanf | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baf92397087ebbac27c7fea8cf5f524b33736b19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401150"
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

En C, les **isnan** (macro) et le **_isnan** et **_isnanf** fonctions retournent une valeur différente de zéro si l’argument *x* est une valeur NAN ; sinon ils retourne 0.

En C++, le **isnan** modèle fonctions retournent **true** si l’argument *x* est une valeur NAN ; sinon, elles retournent **false**.

## <a name="remarks"></a>Notes

C **isnan** (macro) et le **_isnan** et **_isnanf** fonctions testent la valeur à virgule flottante *x*, retournant une valeur différente de zéro si *x* n’est pas une valeur de nombre (NAN). Une valeur NAN est générée quand le résultat d’une opération à virgule flottante ne peut pas être représenté dans un format à virgule flottante IEEE-754 pour le type spécifié. Pour plus d’informations sur la représentation d’une valeur NAN dans la sortie, consultez [printf](printf-printf-l-wprintf-wprintf-l.md).

Lors de la compilation en C++, le **isnan** macro n’est pas définie et un **isnan** fonction avec modèle est définie à la place. Elle retourne une valeur de type **bool** au lieu d’un entier.

Le **_isnan** et **_isnanf** fonctions sont spécifiques de Microsoft. Le **_isnanf** fonction est uniquement disponible lors de la compilation pour x64.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **_isnanf**|\<math.h>|\<math.h> ou \<cmath>|
|**_isnan**|\<float.h>|\<float.h> ou \<cfloat>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
