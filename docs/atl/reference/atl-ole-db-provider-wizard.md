---
title: Assistant fournisseur Oledb ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 827b46de299341f23d0b799a5ed44b8923bbc182
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357478"
---
# <a name="atl-ole-db-provider-wizard"></a>Assistant Fournisseur OLEDB ATL
Cet Assistant crée les classes qui composent un fournisseur OLE DB.  
  
## <a name="remarks"></a>Notes  
 À compter de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrira ses composants COM sous **HKEY_CURRENT_USER** au lieu de **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez la **inscrire le composant pour tous les utilisateurs** option de l’Assistant ATL.  
  
 Le tableau suivant décrit les options de l’Assistant fournisseur OLE DB ATL :  
  
 **Nom court**  
 Tapez le nom court du fournisseur à créer. Les autres zones d’édition dans l’Assistant seront rempliront automatiquement en fonction de ce que vous tapez ici. Vous pouvez modifier les autres zones de nom si vous le souhaitez.  
  
 **coclasse**  
 Le nom de la coclasse. Le nom du ProgID sera modifié pour correspondre à ce nom.  
  
 **Attribué**  
 Cette option spécifie si l’Assistant va créer des classes de fournisseur à l’aide des attributs ou des déclarations de modèle. Lorsque vous sélectionnez cette option, l’Assistant utilise les attributs à la place des déclarations de modèle (il s’agit de l’option par défaut si vous avez créé un projet avec attributs). Lorsque vous désactivez cette option, l’Assistant utilise des déclarations de modèle au lieu d’attributs (il s’agit de l’option par défaut si vous avez créé un projet sans attributs).  
  
 Si vous sélectionnez cette option lorsque vous avez créé un projet sans attributs, l’Assistant vous avertit que le projet sera converti en un projet avec attributs et vous demande s’il faut continuer ou non.  
  
 **ProgID**  
 Le ProgID, ou identificateur programmatique, est une chaîne de texte que votre application peut utiliser à la place d’un GUID. Le nom du ProgID présente sous la forme *NomProjet.NomCoclasse*.  
  
 **Version**  
 Le numéro de version de votre fournisseur. La valeur par défaut est 1.  
  
 **Classe de source de données**  
 Le nom de la classe de source de données, sous la forme C*Shortname*Source.  
  
 **Fichier .h de la source de données**  
 Le fichier d’en-tête pour la classe de source de données. Vous pouvez modifier le nom de ce fichier ou sélectionnez un fichier d’en-tête existant.  
  
 **Classe de session**  
 Le nom de la classe session, sous la forme C*Shortname*Session.  
  
 **Fichier .h de session**  
 Le fichier d’en-tête pour la classe session. Vous pouvez modifier le nom de ce fichier ou sélectionnez un fichier d’en-tête existant.  
  
 **Classe de commande**  
 Le nom de la classe de commande, sous la forme C*Shortname*commande.  
  
 **Fichier .h de commande**  
 Le fichier d’en-tête pour la classe de commande. Ce nom ne peut pas être modifié et dépend du nom de l’ensemble de lignes du fichier d’en-tête.  
  
 **Classe de l’ensemble de lignes**  
 Le nom de la classe rowset, de la forme C*Shortname*ensemble de lignes.  
  
 **Fichier .h ensemble de lignes**  
 Le fichier d’en-tête pour la classe rowset. Vous pouvez modifier le nom de ce fichier ou sélectionnez un fichier d’en-tête existant.  
  
 **Fichier .cpp de jeu de lignes**  
 Fichier d’implémentation du fournisseur. Vous pouvez modifier le nom de ce fichier ou sélectionnez un fichier d’implémentation existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)

