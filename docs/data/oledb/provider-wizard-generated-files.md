---
title: Fichiers générés par l’Assistant fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: a9bc7c85dccdfe095412450d5020fc8a6b42d516
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076969"
---
# <a name="provider-wizard-generated-files"></a>Fichiers générés par l'Assistant Fournisseur

L’Assistant fournisseur OLE DB ATL génère les fichiers suivants. Les rubriques suivantes utilisent le nom court *personnalisé*, mais les noms de fichiers exacte varient selon le choix effectué lors de la création du fournisseur.

|Nom de fichier|Description|
|---------------|-----------------|
|*Custom*RS.cpp|Contient l’application d’assistance `Execute` (méthode) et le mappage de colonnes du fournisseur.|
|*Custom*DS.h|Implémente l’objet de source de données. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de source de données.|
|*Custom*RS.h|Implémente les objets command et rowset. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés d’ensemble de lignes et commande.|
|*Custom*Sess.h|Implémente l’objet de session. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de la session.|
|*Custom*.rgs|Contient les objets inscrits générés par l’Assistant fournisseur OLE DB.|

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)