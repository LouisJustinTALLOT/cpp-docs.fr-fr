---
description: 'En savoir plus sur : Operator &gt; ( &lt; conteneur d’exemples &gt; )'
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
ms.openlocfilehash: 4a8282b3cac493bbf0c2bcb24b8db44df45168f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114960"
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;sample container&gt;)

> [!NOTE]
> Cette rubrique se trouve dans la documentation de Microsoft C++ comme un exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../standard-library/stl-containers.md).

Surcharge d' **opérateur>** pour comparer deux objets du [conteneur](../standard-library/sample-container-class.md)de modèle de classe.

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
