---
title: '!=, opérateur'
ms.date: 11/04/2016
f1_keywords:
- std::!=
- '!='
- std::operator!=
- std.operator!=
- std.!=
- operator!=
helpviewer_keywords:
- '!= operator'
- operator!=
- operator !=
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
ms.openlocfilehash: 1214dd7d5034b80b14f8dd1422aa1a3b8a253023
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447647"
---
# <a name="operator"></a>!=, opérateur

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge `operator!=` pour comparer deux objets de la classe de modèle [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator!=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne `!(left == right)`.

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)
