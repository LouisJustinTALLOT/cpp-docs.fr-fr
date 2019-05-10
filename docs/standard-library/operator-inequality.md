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
ms.openlocfilehash: e29088b64b46e3aa907f4a09ec131c6f9b68a74b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220499"
---
# <a name="operator"></a>!=, opérateur

> [!NOTE]
> Cette rubrique se trouve dans le Microsoft C++ documentation comme exemple non fonctionnel de conteneurs utilisés dans le C++ bibliothèque Standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

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

[\<sample container>](../standard-library/sample-container.md)<br/>
