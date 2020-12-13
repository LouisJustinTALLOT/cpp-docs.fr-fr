---
description: 'En savoir plus sur : principes de conception pour les interfaces de collection et d’énumérateur'
title: Conception des interfaces de collection et d’énumérateur (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: effd2cce775ef926befc89bb6b72a976d85bdf23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148003"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principes de conception pour les interfaces de collection et d’énumérateur

Il existe différents principes de conception sous-jacents à chaque type d’interface :

- Une interface de collection fournit un accès *aléatoire* à un élément *unique* de la collection via la `Item` méthode, elle permet aux clients de découvrir le nombre d’éléments dans la collection via la `Count` propriété, et permet souvent aux clients d’ajouter et de supprimer des éléments.

- Une interface d’énumérateur fournit un accès en *série* à *plusieurs* éléments d’une collection, elle n’autorise pas le client à découvrir le nombre d’éléments présents dans la collection (jusqu’à ce que l’énumérateur arrête le retour d’éléments) et n’offre aucun moyen d’ajouter ou de supprimer des éléments.

Chaque type d’interface joue un rôle différent dans la fourniture de l’accès aux éléments d’une collection.

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)
