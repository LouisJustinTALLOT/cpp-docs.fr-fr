---
title: operator&lt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: e5e53f02da52837b29b6bca4b49662174d6392a1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220529"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans le Microsoft C++ documentation comme exemple non fonctionnel de conteneurs utilisés dans le C++ bibliothèque Standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge **operator<** pour comparer deux objets de la classe de modèle [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)<br/>
[begin](../standard-library/container-class-begin.md)<br/>
[end](../standard-library/container-class-end.md)