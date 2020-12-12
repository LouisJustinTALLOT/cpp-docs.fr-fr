---
description: En savoir plus sur les fichiers de Wizard-Generated fournisseur
title: Fichiers générés par l'Assistant Fournisseur
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 95c9641f10acef4a55b8de15752eb125e75d874a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316893"
---
# <a name="provider-wizard-generated-files"></a>Fichiers générés par l'Assistant Fournisseur

::: moniker range="msvc-160"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

L’**Assistant fournisseur OLE DB ATL** génère les fichiers suivants. Les rubriques suivantes utilisent le nom court *Custom*, mais les noms du fichier exacts dépendent de votre choix lors de la création du fournisseur.

|Nom de fichier|Description|
|---------------|-----------------|
|*Custom* RS.cpp|Contient la méthode `Execute` de l’assistance de commande et le mappage de colonnes du fournisseur.|
|*Custom* DS.h|Implémente l’objet source de données. Ce fichier d’en-tête contient le mappage des propriétés de la source de données.|
|*Custom* RS.h|Implémente les objets commande et ensemble de lignes. Ce fichier d’en-tête contient le mappage des propriétés des propriétés de l’ensemble de lignes et de commande.|
|*Custom* Sess.h|Implémente l’objet de session. Ce fichier d’en-tête contient le mappage des propriétés des propriétés de session.|
|*Custom*.rgs|Contient les objets inscrits générés par l’**Assistant Fournisseur OLE DB**.|

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
