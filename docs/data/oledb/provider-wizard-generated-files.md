---
title: Fichiers générés par l’Assistant fournisseur | Microsoft Docs
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
ms.openlocfilehash: 26e20e0417e2253158930a8d3d055171fe767001
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108402"
---
# <a name="provider-wizard-generated-files"></a>Fichiers générés par l'Assistant Fournisseur

L’Assistant fournisseur OLE DB ATL génère les fichiers suivants. Les rubriques suivantes utilisent le nom court « MyProvider », mais les noms de fichiers exacte varient selon le choix effectué lors de la création du fournisseur.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|MyProviderRS.cpp|Contient l’application d’assistance `Execute` (méthode) et le mappage de colonnes du fournisseur.|  
|MyProviderDS.h|Implémente l’objet de source de données. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de source de données.|  
|MyProviderRS.h|Implémente les objets command et rowset. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés d’ensemble de lignes et commande.|  
|MyProviderSess.h|Implémente l’objet de session. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de la session.|  
|MyProvider.rgs|Contient les objets inscrits générés par l’Assistant fournisseur OLE DB.|  
  
## <a name="see-also"></a>Voir aussi  

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)