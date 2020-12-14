---
description: 'En savoir plus sur : isFinite,, _finite, _finitef'
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: ef0747c88d62445c1cbd31f5c7afe6a651f50880
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263112"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite, _finite, _finitef

Détermine si une valeur à virgule flottante est finie.

## <a name="syntax"></a>Syntaxe

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur retournée

La `isfinite` macro et les `_finite` `_finitef` fonctions et retournent une valeur différente de zéro si *x* est une valeur finie normale ou subordonnée normale. Elles retournent 0 si l’argument est infini ou NaN. La fonction de modèle inline C++ `isfinite` se comporte de la même façon, mais retourne **`true`** ou **`false`** .

## <a name="remarks"></a>Notes

`isfinite` est une macro qui est compilée en tant que C, et une fonction de modèle Inline lorsqu’elle est compilée en C++. Les `_finite` `_finitef` fonctions et sont spécifiques à Microsoft. La fonction `_finitef` n’est disponible que quand elle est compilée pour les plateformes x86, ARM ou ARM64.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> ou \<math.h>|\<float.h>, \<math.h>, \<cfloat> ou \<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> ou \<cmath>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf,](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
