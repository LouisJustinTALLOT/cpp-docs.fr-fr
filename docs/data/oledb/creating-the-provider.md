---
title: Création du fournisseur
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707576"
---
# <a name="creating-the-provider"></a>Création du fournisseur

::: moniker range="vs-2019"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Pour créer un fournisseur OLE DB avec l’Assistant Fournisseur OLE DB ATL

1. Cliquez avec le bouton droit sur le projet.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.

1. Dans la boîte de dialogue **Ajouter une classe** sous **Installé** > **Visual C++** > **ATL**, sélectionnez l’icône du **Fournisseur OLE DB ATL**, puis cliquez sur **Ouvrir**.

1. Dans l’**Assistant fournisseur OLE DB ATL**, entrez un nom court pour le fournisseur dans la zone **Nom court**. Les rubriques suivantes utilisent le nom court *Personnalisé*, mais vous pouvez utiliser un autre nom. Les autres zones de nom se remplissent en fonction du nom que vous entrez.

1. Si nécessaire, modifiez les autres zones de nom. Outre les noms d’objet et de fichier, vous pouvez modifier les éléments suivants :

   - **Coclasse** : le nom utilisé par COM pour créer le fournisseur.

   - **ProgID** : l’identificateur programmatique. Il s’agit d’une chaîne de texte qui peut être utilisée en substitution d’un GUID.

   - **Version** : utilisée avec le ProgID et la coclasse pour générer un ID programmatique dépendant de la version.

1. Cliquez sur **Terminer**.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
