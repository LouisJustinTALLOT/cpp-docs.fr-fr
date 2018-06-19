---
title: Fichiers générés par l’Assistant fournisseur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac23f06bf1ae697ecd627d493aa5902219488138
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106006"
---
# <a name="provider-wizard-generated-files"></a>Fichiers générés par l'Assistant Fournisseur
L’Assistant fournisseur OLE DB ATL génère les fichiers suivants. Les rubriques suivantes utilisent le nom court « MyProvider », mais les noms de fichiers exacts varient selon le choix effectué lors de la création du fournisseur.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|MyProviderRS.cpp|Contient l’application d’assistance de la commande `Execute` (méthode) et le mappage de colonnes du fournisseur.|  
|MyProviderDS.h|Implémente l’objet de source de données. Ce fichier d’en-tête contient le mappage de propriété pour les propriétés de source de données.|  
|MyProviderRS.h|Implémente les objets command et rowset. Ce fichier d’en-tête contient le mappage de propriété pour les propriétés d’ensemble de lignes et commande.|  
|MyProviderSess.h|Implémente l’objet de session. Ce fichier d’en-tête contient le mappage de propriété pour les propriétés de la session.|  
|MyProvider.rgs|Contient les objets inscrits générés par l’Assistant fournisseur OLE DB.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)