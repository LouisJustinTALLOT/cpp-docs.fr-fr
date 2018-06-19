---
title: Création du fournisseur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b08d2a2f68d174ae7c92d1d6bc0fa2bbb764fdca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097183"
---
# <a name="creating-the-provider"></a>Création du fournisseur
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Pour créer un fournisseur OLE DB avec l’Assistant fournisseur OLE DB ATL  
  
1.  Cliquez sur le projet.  
  
2.  Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une classe**.  
  
3.  Dans le **ajouter une classe** boîte de dialogue, sélectionnez le **fournisseur OLE DB ATL** icône, puis cliquez sur **ouvrir**.  
  
4.  Dans l’Assistant fournisseur OLE DB ATL, entrez un nom court pour le fournisseur dans le **nom court** boîte. Les rubriques suivantes utilisent le nom court « MyProvider », mais vous pouvez utiliser un autre nom. Les autres zones de nom remplissent en fonction du nom que vous entrez.  
  
5.  Modifiez les autres zones de nom si nécessaire. Outre les noms d’objet et de fichier, vous pouvez modifier les éléments suivants :  
  
    -   **Coclasse**: le nom utilisé par COM pour créer le fournisseur.  
  
    -   **ProgID**: l’identificateur programmatique, qui est une chaîne de texte qui peut être utilisée à la place d’un GUID.  
  
    -   **Version**: utilisée avec ProgID et coclasse pour générer un ID programmatique de dépendants de la version.  
  
6.  Cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)