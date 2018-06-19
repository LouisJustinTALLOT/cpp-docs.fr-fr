---
title: Amélioration du fournisseur en lecture seule Simple | Documents Microsoft
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
ms.openlocfilehash: 7c88714e4e1651839cdc5fd4b92d3c5222aa08d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100016"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Amélioration du fournisseur simple accessible en lecture seule
Cette section montre comment améliorer la [fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) créé dans la section précédente. `IRowsetLocateImpl` Crée une implémentation pour la `IRowsetLocate` de l’interface et ajoute la prise en charge des signets pour vous.  
  
 Lorsque vous avez un fournisseur opérationnel, vous souhaiterez peut-être améliorer pour rendre la mise à jour du fournisseur, gérer des transactions ou améliorer les performances de l’algorithme d’extraction de lignes. La plupart des améliorations du fournisseur impliquent l’ajout d’une interface à un objet COM existant.  
  
 L’exemple dans les rubriques suivantes améliore le mécanisme d’extraction de lignes en ajoutant le `IRowsetLocate` interface `CAgentRowset`. Les rubriques vous indiquent comment procéder pour :  
  
-   [Faites en sorte que RMyProviderRowset hérite de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un fournisseur simple accessible en lecture seule](../../data/oledb/creating-a-simple-read-only-provider.md)