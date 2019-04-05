---
title: Création d'un fournisseur OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 3e46e87b0d5d538a0f9fd7e231debfef3fa95210
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036112"
---
# <a name="creating-an-ole-db-provider"></a>Création d'un fournisseur OLE DB

La méthode recommandée pour créer un fournisseur OLE DB consiste à utiliser les Assistants pour créer un projet ATL COM et un fournisseur, puis modifier les fichiers en utilisant les modèles OLE DB. Quand vous personnalisez votre fournisseur, vous pouvez commenter les propriétés indésirables et ajouter des interfaces facultatives.

Les étapes de base sont les suivantes :

1. Utilisez le **Assistant Projet ATL** pour créer les fichiers de projet de base et la **Assistant de fournisseur OLEDB ATL** pour créer le fournisseur (sélectionnez **fournisseur de ATL OLEDB** à partir de la **Installé** > **Visual C++** > **ATL** dossier **ajouter un nouvel élément**).

   > [!NOTE]
   > Le projet doit inclure la prise en charge MFC avant d’ajouter un **fournisseur d’OLEDB ATL**.

1. Modifier le code dans le `Execute` méthode dans [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Pour obtenir un exemple, consultez [lecture de chaînes dans le fournisseur OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

1. Modifier la propriété est mappée dans [CustomDS.h](cmyprovidersource-myproviderds-h.md), [CustomSess.h](cmyprovidersession-myprovidersess-h.md), et [CustomRS.h](cmyproviderrowset-myproviderrs-h.md). L’Assistant crée des mappages de propriété qui contiennent toutes les propriétés qu’un fournisseur peut implémenter. Parcourez les mappages de propriété et supprimez ou commentez les propriétés de votre fournisseur n’a pas besoin pour prendre en charge.

1. Mettre à jour PROVIDER_COLUMN_MAP, qui se trouve dans [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Pour obtenir un exemple, consultez [stockage de chaînes dans le fournisseur OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).

1. Lorsque vous êtes prêt à tester votre fournisseur, vous pouvez le tester en essayant de trouver le fournisseur dans une énumération de fournisseur. Pour obtenir des exemples de code de test qui recherche un fournisseur dans une énumération, consultez le [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) et [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) ou l’exemple fourni dans [implémentation d’un consommateur Simple](../../data/oledb/implementing-a-simple-consumer.md).

1. Ajouter toutes les interfaces que vous souhaitez. Pour obtenir un exemple, consultez [amélioration le fournisseur Simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md).

   > [!NOTE]
   > Par défaut, les Assistants génèrent un code OLE DB conforme au niveau 0. Pour vous assurer que votre application reste conforme au niveau 0, ne supprimez pas les interfaces générées par l’Assistant à partir du code.

## <a name="see-also"></a>Voir aussi

[CatDB, exemple : Explorateur de schémas de base de données](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Exemple DBViewer : Navigateur de la base de données](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
