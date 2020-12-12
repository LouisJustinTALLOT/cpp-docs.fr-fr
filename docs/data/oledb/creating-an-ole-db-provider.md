---
description: 'En savoir plus sur : création d’un fournisseur de OLE DB'
title: Création d'un fournisseur OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 69dc9311a79f2739636633b2d268343a92d2dac9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287799"
---
# <a name="creating-an-ole-db-provider"></a>Création d'un fournisseur OLE DB

La méthode recommandée pour créer un fournisseur de OLE DB consiste à utiliser les assistants pour créer un projet ATL COM et un fournisseur, puis à modifier les fichiers à l’aide des modèles de OLE DB. Lorsque vous personnalisez votre fournisseur, vous pouvez commenter les propriétés indésirables et ajouter des interfaces facultatives.

Les étapes de base sont les suivantes :

1. Utilisez l' **Assistant Projet ATL** pour créer les fichiers projet de base et l' **Assistant fournisseur OLEDB ATL** pour créer le fournisseur (sélectionnez **fournisseur OLEDB ATL** dans le   >  dossier **Visual C++**  >  **ATL** installé dans **Ajouter un nouvel élément**).

   > [!NOTE]
   > Le projet doit inclure la prise en charge de MFC avant l’ajout d’un **fournisseur OLEDB ATL**.

1. Modifiez le code de la `Execute` méthode dans [CCustomRowset (Customers. h)](cmyproviderrowset-myproviderrs-h.md). Pour obtenir un exemple, consultez [lecture de chaînes dans un fournisseur OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

1. Modifiez les mappages des propriétés dans [CustomDS. h](cmyprovidersource-myproviderds-h.md), [CustomSess. h](cmyprovidersession-myprovidersess-h.md)et [Customers. h](cmyproviderrowset-myproviderrs-h.md). L’Assistant crée des mappages de propriétés qui contiennent toutes les propriétés qu’un fournisseur peut implémenter. Parcourez les mappages de propriétés et supprimez ou commentez les propriétés que votre fournisseur n’a pas besoin de prendre en charge.

1. Mettez à jour le PROVIDER_COLUMN_MAP, qui se trouve dans [CCustomRowset (Customers. h)](cmyproviderrowset-myproviderrs-h.md). Pour obtenir un exemple, consultez [stockage de chaînes dans le fournisseur OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).

1. Lorsque vous êtes prêt à tester votre fournisseur, vous pouvez le tester en tentant de trouver le fournisseur dans une énumération de fournisseur. Pour obtenir des exemples de code de test qui recherche un fournisseur dans une énumération, consultez les exemples [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) et [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) ou l’exemple dans [implémentation d’un consommateur simple](../../data/oledb/implementing-a-simple-consumer.md).

1. Ajoutez toutes les interfaces supplémentaires de votre choix. Pour obtenir un exemple, consultez [amélioration du fournisseur de Read-Only simple](../../data/oledb/enhancing-the-simple-read-only-provider.md).

   > [!NOTE]
   > Par défaut, les Assistants génèrent du code qui est OLE DB conforme au niveau 0. Pour vous assurer que votre application reste conforme au niveau 0, ne supprimez pas les interfaces générées par l’Assistant à partir du code.

## <a name="see-also"></a>Voir aussi

[Exemple CatDB : Explorateur de schéma de source de données](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Exemple DBViewer : Explorateur de bases de données](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
