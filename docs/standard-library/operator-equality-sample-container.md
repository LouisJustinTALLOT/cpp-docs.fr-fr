---
description: 'En savoir plus sur : Operator = = ( &lt; conteneur d’exemple &gt; )'
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
ms.openlocfilehash: b2fb296feb76536c28dd45e631af8071efa16939
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337981"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans la documentation de Microsoft C++ comme un exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge `operator==` pour comparer deux objets du [conteneur](../standard-library/sample-container-class.md)de modèle de classe.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne la fin de la `left.` [taille](../standard-library/container-class-size.md) de `== right.size && equal(left.` [début](../standard-library/container-class-begin.md) `, left.` [](../standard-library/container-class-end.md) `, right.begin)` .

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)
