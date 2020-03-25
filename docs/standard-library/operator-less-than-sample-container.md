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
ms.openlocfilehash: 6ef43fb762c4da71062fc846048f21c0112bfafc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215265"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge d' **opérateur <** pour comparer deux objets du [conteneur](../standard-library/sample-container-class.md)de modèle de classe.

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

[\<sample container>](../standard-library/sample-container.md)\
[début](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)
