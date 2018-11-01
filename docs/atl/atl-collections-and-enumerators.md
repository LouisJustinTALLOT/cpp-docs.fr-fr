---
title: Collections et énumérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 4949e8cff59a40b25c2015bf776d0844d29116a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617278"
---
# <a name="atl-collections-and-enumerators"></a>Collections et énumérateurs ATL

Un `collection` est un objet COM qui fournit une interface qui autorise l’accès à un groupe d’éléments de données (données brutes ou autres objets). Une interface qui suit les normes pour fournir l’accès à un groupe d’objets est appelé un *interface de collection*.

Au minimum, les interfaces de collection doivent fournir un `Count` propriété qui retourne le nombre d’éléments dans la collection, une `Item` propriété qui retourne un élément de la collection basée sur un index, et un `_NewEnum` propriété qui retourne un énumérateur de la collection. Si vous le souhaitez, peuvent fournir des interfaces de collection `Add` et `Remove` des méthodes qui permettent d’éléments à insérer ou supprimer de la collection et un `Clear` méthode pour supprimer tous les éléments.

Un `enumerator` est un objet COM qui fournit une interface pour itérer au sein des éléments dans une collection. Interfaces d’énumérateur fournissent un accès série aux éléments d’une collection par le biais de quatre méthodes : `Next`, `Skip`, `Reset`, et `Clone`.

Vous pouvez en savoir plus sur les interfaces d’énumérateur par lecture de contenu de référence comme [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) interface.

## <a name="in-this-section"></a>Dans cette section

[Collections ATL et classes d’énumérateurs](../atl/atl-collection-and-enumerator-classes.md)<br/>
Décrit brièvement et fournit des liens vers les classes ATL qui vous aidera à implémentent des collections et énumérateurs.

[Principes de conception pour les interfaces d’énumérateurs et de collections](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Décrit les principes de conception différent chaque type d’interface.

[Implémentation d’une collection basée sur la bibliothèque standard C++](../atl/implementing-an-stl-based-collection.md)<br/>
Un exemple d’étendue qui vous guide tout au long de l’implémentation d’une collection basée sur la bibliothèque C++ Standard.

## <a name="related-sections"></a>Rubriques connexes

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

[ATLCollections, exemple](../visual-cpp-samples.md)<br/>
Un exemple qui illustre l’utilisation de `ICollectionOnSTLImpl` et `CComEnumOnSTL`et l’implémentation de classes de stratégie de copie personnalisé.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)

