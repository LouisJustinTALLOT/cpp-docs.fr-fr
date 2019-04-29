---
title: Fichiers générés par l'Assistant Fournisseur
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: a9a706463326249135a55bc907cb8a664a3ca808
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282960"
---
# <a name="provider-wizard-generated-files"></a>Fichiers générés par l'Assistant Fournisseur

Le **Assistant fournisseur OLE DB ATL** génère les fichiers suivants. Les rubriques suivantes utilisent le nom court *personnalisé*, mais les noms de fichiers exacte varient selon le choix effectué lors de la création du fournisseur.

|Nom de fichier|Description|
|---------------|-----------------|
|*Custom*RS.cpp|Contient l’application d’assistance `Execute` (méthode) et le mappage de colonnes du fournisseur.|
|*Custom*DS.h|Implémente l’objet de source de données. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de source de données.|
|*Custom*RS.h|Implémente les objets command et rowset. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés d’ensemble de lignes et commande.|
|*Custom*Sess.h|Implémente l’objet de session. Ce fichier d’en-tête contient le mappage des propriétés pour les propriétés de la session.|
|*Custom*.rgs|Contient les objets inscrits générés par le **Assistant fournisseur OLE DB**.|

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
