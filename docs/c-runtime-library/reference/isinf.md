---
description: 'En savoir plus sur : isinf,'
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: f174855ddbb8cc43fd7338d4254c0f03bf53967d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332644"
---
# <a name="isinf"></a>isinf

Détermine si une valeur à virgule flottante est un infini.

## <a name="syntax"></a>Syntaxe

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur retournée

**isinf,** retourne une valeur différente de zéro ( **`true`** dans le code C++) si l’argument *x* est un infini positif ou négatif. **isinf,** retourne 0 ( **`false`** dans le code C++) si l’argument est fini ou Nan. Les valeurs à virgule flottante normale et subnormal sont considérées comme limitées.

## <a name="remarks"></a>Notes

**isinf,** est une macro qui est compilée en tant que C, et une fonction de modèle Inline lorsqu’elle est compilée en C++.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf,**|\<math.h>|\<math.h> ou \<cmath>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
