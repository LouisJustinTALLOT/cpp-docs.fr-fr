---
title: Collections et énumérateurs ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537d7e8b7264beddc68805ab8b8dec2ce7883859
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356776"
---
# <a name="atl-collections-and-enumerators"></a>Collections et énumérateurs ATL
A `collection` est un objet COM qui fournit une interface qui autorise l’accès à un groupe d’éléments de données (données brutes ou autres objets). Interface qui respecte les normes pour fournir l’accès à un groupe d’objets est appelé un *interface de collection*.  
  
 Au minimum, les interfaces de collection doivent fournir un **nombre** propriété qui retourne le nombre d’éléments dans la collection, une **élément** propriété qui retourne un élément de la collection basée sur un index et un `_NewEnum` propriété qui retourne un énumérateur pour la collection. Le cas échéant, peuvent fournir les interfaces de collection **ajouter** et **supprimer** méthodes afin de permettre des éléments à insérer ou supprimer de la collection et un **clair** à supprimer (méthode) tous les éléments.  
  
 Un `enumerator` est un objet COM qui fournit une interface pour l’itération au sein des éléments dans une collection. Interfaces d’énumérateur fournissent un accès série aux éléments d’une collection via quatre méthodes : `Next`, **ignorer**, **réinitialiser**, et `Clone`.  
  
 Vous pouvez en savoir plus sur l’énumérateur (interfaces) en lecture sur le type (mais entièrement imaginaire) [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx) interface.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Collections ATL et classes d’énumérateurs](../atl/atl-collection-and-enumerator-classes.md)  
 Décrit brièvement et fournit des liens vers les classes ATL qui vous aidera à implémentent des collections et énumérateurs.  
  
 [Principes de conception pour les interfaces d’énumérateurs et de collections](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Présente les principes de conception derrière chaque type d’interface.  
  
 [Implémentation d’une collection basée sur la bibliothèque standard C++](../atl/implementing-an-stl-based-collection.md)  
 Exemple étendu qui vous guide tout au long de l’implémentation d’un regroupement basé sur la bibliothèque C++ Standard.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).  
  
 [ATLCollections, exemple](../visual-cpp-samples.md)  
 Un exemple qui illustre l’utilisation de `ICollectionOnSTLImpl` et `CComEnumOnSTL`et l’implémentation de classes de stratégies de copie personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)

