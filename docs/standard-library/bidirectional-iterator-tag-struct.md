---
title: bidirectional_iterator_tag, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: bab2664fcb552a72baa032d719cf6b0141ffe525
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456635"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag, struct

Classe qui fournit un type de retour pour `iterator_category` une fonction qui représente un itérateur bidirectionnel.

## <a name="syntax"></a>Syntaxe

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Notes

Les classes de balise de catégorie sont utilisées comme balises de compilation pour la sélection de l’algorithme. La fonction de modèle doit rechercher la catégorie la plus spécifique de son argument d’itérateur, pour pouvoir utiliser l’algorithme le plus efficace au moment de la compilation. Pour chaque itérateur de type `Iterator`, `iterator_traits`< `Iterator`>:: **iterator_category** doit être défini comme étant la balise de catégorie la plus spécifique qui décrit le comportement de l’itérateur.

Le type est identique à **iterator** \< **ITER**>:: **iterator_category** lorsque `Iter` décrit un objet pouvant servir d’itérateur bidirectionnel.

## <a name="example"></a>Exemple

Consultez [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) pour obtenir un exemple d’utilisation de `bidirectional_iterator_tag`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[forward_iterator_tag, struct](../standard-library/forward-iterator-tag-struct.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
