---
title: Conception de Collection et les Interfaces d’énumérateur (ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05649cce0e80af6f54327545cef7b663d69babf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354917"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principes de conception pour la collecte et les Interfaces d’énumérateur
Il existe des principes de conception de chaque type d’interface :  
  
-   Une interface de collection fournit *aléatoires* l’accès à un *unique* élément dans la collection via la **élément** (méthode), il permet aux clients de découvrir le nombre d’éléments figurant dans la collection via le **nombre** propriété, et souvent permet aux clients d’ajouter et supprimer des éléments.  
  
-   Une interface d’énumérateur fournit *série* l’accès à *plusieurs* les éléments d’une collection, il n’autorise pas le client découvrir le nombre d’éléments figurant dans la collection (jusqu'à ce que l’énumérateur cesse de retour éléments), et il ne fournit aucun moyen d’Ajout ou suppression d’éléments.  
  
 Chaque type d’interface joue un rôle différent en fournissant l’accès aux éléments dans une collection.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)

