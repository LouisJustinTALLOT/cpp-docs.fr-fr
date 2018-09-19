---
title: Amélioration du fournisseur Simple en lecture seule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28a92f6193053baca80ca078bddc0de862f50279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036447"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Amélioration du fournisseur simple accessible en lecture seule

Cette section montre comment améliorer la [fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) créé dans la section précédente. `IRowsetLocateImpl` Crée une implémentation pour le `IRowsetLocate` interface et ajoute la prise en charge des signets pour vous.  
  
Lorsque vous avez un fournisseur opérationnel, vous souhaiterez peut-être améliorer pour rendre la mise à jour du fournisseur, gérer des transactions ou améliorer les performances de l’algorithme de l’extraction de lignes. La plupart des améliorations du fournisseur impliquent l’ajout d’une interface à un objet COM existant.  
  
L’exemple dans les rubriques suivantes améliore le mécanisme d’extraction de lignes en ajoutant le `IRowsetLocate` à l’interface `CAgentRowset`. Les rubriques vous montrent à :  
  
- [Faites en sorte que RMyProviderRowset hérite de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
- [Déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Voir aussi  

[Création d’un fournisseur simple accessible en lecture seule](../../data/oledb/creating-a-simple-read-only-provider.md)