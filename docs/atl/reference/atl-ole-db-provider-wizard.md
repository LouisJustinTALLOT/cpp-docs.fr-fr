---
title: Assistant Fournisseur OLEDB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 43b8ed4507b004f1e78bc1b9dda64c44ff56e1d7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921137"
---
# <a name="atl-ole-db-provider-wizard"></a>Assistant Fournisseur OLEDB ATL

::: moniker range="msvc-160"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=msvc-150"

## <a name="remarks"></a>Notes

À partir de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrit ses composants COM sous **HKEY_CURRENT_USER** et non plus **HKEY_LOCAL_MACHINE** . Pour modifier ce comportement, définissez l’option **Inscrire le composant pour tous les utilisateurs** de l’Assistant ATL.

Le tableau suivant décrit les options de l’Assistant Fournisseur OLE DB ATL :

- **Nom court**

   Tapez le nom court du fournisseur à créer. Les autres champs de modification dans l’Assistant se rempliront automatiquement en fonction de ce que vous tapez ici. Vous pouvez modifier les autres champs de nom si vous le souhaitez.

- **Coclasse**

   Nom de la coclasse. Le nom du ProgID sera modifié pour correspondre à ce nom.

- **Avec attributs**

   Cette option spécifie si l’Assistant va créer des classes de fournisseur à l’aide d’attributs ou de déclarations de modèle. Lorsque vous sélectionnez cette option, l’Assistant utilise des attributs plutôt que des déclarations de modèle (il s’agit de l’option par défaut si vous avez créé un projet avec attributs). Lorsque vous désélectionnez cette option, l’Assistant utilise des déclarations de modèle plutôt que des attributs (il s’agit de l’option par défaut si vous avez créé un projet sans attributs).

   Si vous sélectionnez cette option lorsque vous avez créé un projet sans attributs, l’Assistant vous avertit que le projet sera converti en un projet avec attributs et vous demande si vous souhaitez continuer.

- **ProgID**

   Le progID, ou identificateur programmatique, est une chaîne de texte que votre application peut utiliser à la place d’un GUID. Le nom du ProgID est au format *NomProjet.NomCoclasse* .

- **Version**

   Numéro de version de votre fournisseur. La valeur par défaut est 1.

- **Classe DataSource**

   Nom de la classe data source, au format C *Nomcourt* Source.

- **DataSource .h file** (Fichier .h DataSource)

   Fichier d’en-tête de la classe data source. Vous pouvez modifier le nom de ce fichier ou sélectionner un fichier d’en-tête existant.

- **Session class** (Classe Session)

   Nom de la classe session, au format C *Nomcourt* Session.

- **Session .h file** (Fichier .h Session)

   Fichier d’en-tête pour la classe session. Vous pouvez modifier le nom de ce fichier ou sélectionner un fichier d’en-tête existant.

- **Classe Command**

   Nom de la classe command, au format C *Nomcourt* Command.

- **Command .h file** (Fichier .h Command)

   Fichier d’en-tête pour la classe command. Ce nom ne peut pas être modifié et dépend du nom du fichier d’en-tête rowset.

- **Rowset class** (Classe Rowset)

   Nom de la classe Rowset, au format C *Nomcourt* Rowset.

- **Rowset .h file** (Fichier .h Rowset)

   Fichier d’en-tête pour la classe rowset. Vous pouvez modifier le nom de ce fichier ou sélectionner un fichier d’en-tête existant.

- **Rowset .cpp file** (Fichier .cpp Rowset)

   Fichier d’implémentation du fournisseur. Vous pouvez modifier le nom de ce fichier ou sélectionner un fichier d’implémentation existant.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Ajout d’un fournisseur OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)
