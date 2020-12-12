---
description: 'En savoir plus sur : création du fournisseur'
title: Création du fournisseur
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 2b5a00f0a873575d9fe7b2b177bb34a6c74e193e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305429"
---
# <a name="creating-the-provider"></a>Création du fournisseur

::: moniker range="msvc-160"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Pour créer un fournisseur OLE DB avec l’Assistant Fournisseur OLE DB ATL

1. Cliquez avec le bouton droit sur le projet.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.

1. Dans la boîte de dialogue **Ajouter une classe** sous **Installé** > **Visual C++** > **ATL**, sélectionnez l’icône du **Fournisseur OLE DB ATL**, puis cliquez sur **Ouvrir**.

1. Dans l’**Assistant fournisseur OLE DB ATL**, entrez un nom court pour le fournisseur dans la zone **Nom court**. Les rubriques suivantes utilisent le nom court *Personnalisé*, mais vous pouvez utiliser un autre nom. Les autres zones de nom se remplissent en fonction du nom que vous entrez.

1. Si nécessaire, modifiez les autres zones de nom. Outre les noms d’objet et de fichier, vous pouvez modifier les éléments suivants :

   - **Coclass**: nom utilisé par com pour créer le fournisseur.

   - **ProgID**: identificateur programmatique, qui est une chaîne de texte qui peut être utilisée à la place d’un GUID.

   - **Version**: utilisé avec le ProgID et la coclasse pour générer un ID programmatique dépendant de la version.

1. Cliquez sur **Terminer**.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
