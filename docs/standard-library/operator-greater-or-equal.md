---
title: operator&gt;=
ms.date: 11/04/2016
f1_keywords:
- operator>=
- std::>=
- std.operator>=
- '>='
- std.>=
- std::operator>=
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator >=
- operator>=
ms.assetid: 14fbebf5-8b75-4afa-a51b-3112d31c07cf
ms.openlocfilehash: 6eb8db25f5f30a978de197d699acf28bf8bea116
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447961"
---
# <a name="operatorgt"></a>operator&gt;=

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge **operator>=** pour comparer deux objets de la classe de modèle [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator>=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne `!(left < right)`.

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)
