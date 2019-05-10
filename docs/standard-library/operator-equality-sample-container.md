---
title: operator== (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 9313df5d75efa043f2fb9df6090c125de75a2636
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220259"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans le Microsoft C++ documentation comme exemple non fonctionnel de conteneurs utilisés dans le C++ bibliothèque Standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge `operator==` pour comparer deux objets de la classe de modèle [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne `left.` [taille](../standard-library/container-class-size.md) ` == right.size && equal(left.` [commencer](../standard-library/container-class-begin.md)`, left.`[fin](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)<br/>
