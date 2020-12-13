---
description: 'En savoir plus sur : isnormal'
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 3afae5196a7a6b2b149028ad347f95baa27b1544
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337761"
---
# <a name="isnormal"></a>isnormal

Détermine si une valeur à virgule flottante est une valeur normale.

## <a name="syntax"></a>Syntaxe

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur retournée

**isnormal** retourne une valeur différente de zéro ( **`true`** dans le code C++) si l’argument *x* n’est ni zéro, ni subnormal, infini ni Nan. Sinon, **isnormal** retourne 0 ( **`false`** dans le code C++).

## <a name="remarks"></a>Notes

**isnormal** est une macro qui est compilée en tant que C, et un modèle de fonction inline lorsqu’elle est compilée en C++.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> ou \<cmath>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf,](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
