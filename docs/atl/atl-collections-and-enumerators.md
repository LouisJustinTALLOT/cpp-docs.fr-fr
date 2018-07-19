---
title: Collections et énumérateurs ATL | Microsoft Docs
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
ms.openlocfilehash: 9837b42148062bdd2c44855c129f085ca47cdec0
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848792"
---
# <a name="atl-collections-and-enumerators"></a>Collections et énumérateurs ATL
Un `collection` est un objet COM qui fournit une interface qui autorise l’accès à un groupe d’éléments de données (données brutes ou autres objets). Une interface qui suit les normes pour fournir l’accès à un groupe d’objets est appelé un *interface de collection*.  
  
 Au minimum, les interfaces de collection doivent fournir un `Count` propriété qui retourne le nombre d’éléments dans la collection, une `Item` propriété qui retourne un élément de la collection basée sur un index, et un `_NewEnum` propriété qui retourne un énumérateur de la collection. Si vous le souhaitez, peuvent fournir des interfaces de collection `Add` et `Remove` des méthodes qui permettent d’éléments à insérer ou supprimer de la collection et un `Clear` méthode pour supprimer tous les éléments.  
  
 Un `enumerator` est un objet COM qui fournit une interface pour itérer au sein des éléments dans une collection. Interfaces d’énumérateur fournissent un accès série aux éléments d’une collection par le biais de quatre méthodes : `Next`, `Skip`, `Reset`, et `Clone`.  
  
 Vous pouvez en savoir plus sur les interfaces d’énumérateur en lecture sur le type (mais entièrement imaginaire) [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx) interface.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Collections ATL et classes d’énumérateurs](../atl/atl-collection-and-enumerator-classes.md)  
 Décrit brièvement et fournit des liens vers les classes ATL qui vous aidera à implémentent des collections et énumérateurs.  
  
 [Principes de conception pour les interfaces d’énumérateurs et de collections](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Décrit les principes de conception différent chaque type d’interface.  
  
 [Implémentation d’une collection basée sur la bibliothèque standard C++](../atl/implementing-an-stl-based-collection.md)  
 Un exemple d’étendue qui vous guide tout au long de l’implémentation d’une collection basée sur la bibliothèque C++ Standard.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).  
  
 [ATLCollections, exemple](../visual-cpp-samples.md)  
 Un exemple qui illustre l’utilisation de `ICollectionOnSTLImpl` et `CComEnumOnSTL`et l’implémentation de classes de stratégie de copie personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)

