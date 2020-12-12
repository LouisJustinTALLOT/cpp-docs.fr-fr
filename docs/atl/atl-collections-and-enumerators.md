---
description: 'En savoir plus sur : Collections et énumérateurs ATL'
title: Collections et énumérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 92e9ab3df52219812d72ae5cb811f57a3ecf4fad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166003"
---
# <a name="atl-collections-and-enumerators"></a>Collections et énumérateurs ATL

Un `collection` est un objet com qui fournit une interface qui permet d’accéder à un groupe d’éléments de données (données brutes ou autres objets). Une interface qui suit les normes pour fournir l’accès à un groupe d’objets est connue sous le nom d' *interface de collection*.

Au minimum, les interfaces de collection doivent fournir une `Count` propriété qui retourne le nombre d’éléments dans la collection, une `Item` propriété qui retourne un élément de la collection en fonction d’un index et une `_NewEnum` propriété qui retourne un énumérateur pour la collection. Éventuellement, les interfaces de collection peuvent fournir `Add` des `Remove` méthodes et pour autoriser l’insertion ou la suppression d’éléments dans la collection, et une `Clear` méthode pour supprimer tous les éléments.

Un `enumerator` est un objet com qui fournit une interface pour itérer au sein des éléments d’une collection. Les interfaces d’énumérateur fournissent un accès en série aux éléments d’une collection à l’aide de quatre méthodes requises : `Next` ,, `Skip` `Reset` et `Clone` .

Vous pouvez en savoir plus sur les interfaces d’énumérateur en lisant le contenu de référence, par exemple l’interface [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

## <a name="in-this-section"></a>Dans cette section

[Collections ATL et classes Enumerator](../atl/atl-collection-and-enumerator-classes.md)<br/>
Décrit brièvement et fournit des liens vers les classes ATL qui vous aideront à implémenter des collections et des énumérateurs.

[Principes de conception pour les interfaces de collection et d’énumérateur](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Présente les différents principes de conception sous-jacents à chaque type d’interface.

[Implémentation d’une collection Library-Based standard C++](../atl/implementing-an-stl-based-collection.md)<br/>
Exemple étendu qui vous guide tout au long de l’implémentation d’une collection C++ standard basée sur la bibliothèque.

## <a name="related-sections"></a>Sections connexes

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

[Exemple ATLCollections](../overview/visual-cpp-samples.md)<br/>
Exemple qui illustre l’utilisation de `ICollectionOnSTLImpl` et de `CComEnumOnSTL` , et l’implémentation de classes de stratégie de copie personnalisées.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
