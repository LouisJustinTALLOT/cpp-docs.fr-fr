---
title: isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 907b26f4e1824d7ef5c7c1a36b4e4d8ccb74c978
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220715"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered

Détermine la relation de classement entre deux valeurs à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
Valeurs à virgule flottante à comparer.

## <a name="return-value"></a>Valeur de retour

Dans toutes les comparaisons, les infinis du même signe sont considérées comme égales. L’infini négatif est inférieur à toute valeur finie ou infini positif. L’infini positif est supérieur à toute valeur finie ou infini négatif. Les zéros sont égaux quel que soit le signe. Les valeurs NaN ne sont pas inférieures, égales ou supérieures à toute valeur, y compris une autre valeur NaN.

Quand aucun argument n’est un NaN, les macros de classement **isgreater**, **isgreaterequal**, **Ile**et **islessequal** retournent une valeur différente de zéro si la relation de classement spécifiée entre *x* et *y* contient la valeur true. Ces macros retournent 0 si l’un des arguments ou les deux sont des valeurs NaN ou si la relation de classement est false. Les formulaires de fonction se comportent de la même façon, mais retournent **`true`** ou **`false`** .

La macro **islessgreater** retourne une valeur différente de zéro si *x* et *y* ne sont pas des valeurs NaN et si *x* est inférieur à ou supérieur à *y*. Elle retourne 0 si l’un ou l’autre des arguments ou les deux sont des valeurs NaN ou si les valeurs sont égales. Le formulaire de fonction se comporte de la même façon, mais retourne **`true`** ou **`false`** .

La macro **isunordered** retourne une valeur différente de zéro si *x*, *y*ou les deux sont des valeurs NaN. Sinon, retourne 0. Le formulaire de fonction se comporte de la même façon, mais retourne **`true`** ou **`false`** .

## <a name="remarks"></a>Notes

Ces opérations de comparaison sont implémentées en tant que macros lorsqu’elles sont compilées en tant que C, et en tant que fonctions de modèle Inline lorsqu’elles sont compilées en C++.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **île**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<math.h> ou \<cmath> |

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
