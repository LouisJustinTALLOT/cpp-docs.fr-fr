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
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703436"
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
Les valeurs à virgule flottante à comparer.

## <a name="return-value"></a>Valeur de retour

Dans toutes les comparaisons, les valeurs infinies du même signe sont considérés comme égaux. Infini négatif est inférieure à toute valeur finie ou l’infini positif. Infini positif est supérieure à toute valeur finie ou l’infini négatif. Zéros non significatifs sont égales, quel que soit la connexion. Valeurs NaN ne sont pas inférieure, égale ou supérieure à n’importe quelle valeur, y compris une autre valeur NaN.

Lorsque aucun de ces arguments est une valeur NaN, les macros de classement **isgreater**, **isgreaterequal**, **isless**, et **islessequal** retourner un zéro valeur si la relation de tri spécifiée entre *x* et *y* contienne la valeur true. Ces macros retournent 0 si les deux arguments sont des valeurs NaN ou si la relation de tri a la valeur false. Les formulaires de fonction se comportent de la même façon, mais retourner **true** ou **false**.

Le **islessgreater** macro retourne une valeur différente de zéro si les deux *x* et *y* ne sont pas des valeurs NaN, et *x* est soit inférieure ou supérieure à *y*. Elle retourne 0 si les deux arguments sont des valeurs NaN, ou si les valeurs sont égales. Le formulaire de la fonction se comporte de la même façon, mais retourne **true** ou **false**.

Le **isunordered** macro retourne une valeur différente de zéro si *x*, *y*, ou les deux sont des valeurs NaN. Sinon, elle retourne 0. Le formulaire de la fonction se comporte de la même façon, mais retourne **true** ou **false**.

## <a name="remarks"></a>Notes

Ces opérations de comparaison sont implémentées en tant que macros lors de la compilation en C et en tant que fonctions de modèle inline lors de la compilation en C++.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isless**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<math.h> ou \<cmath> |

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
