---
title: operator&gt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
ms.openlocfilehash: e7da0250dc647d2d519b9c3d105fb942717c7a4c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449744"
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge **operator>** pour comparer deux objets de la classe de modèle [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator*gt;(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valeur de retour

Retourne `right < left`.

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)
