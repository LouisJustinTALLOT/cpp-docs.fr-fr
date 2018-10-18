---
title: Création du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2018
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
ms.openlocfilehash: 0dbdf7350eeba1a29392bafc2f099a857e212e37
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410744"
---
# <a name="creating-the-provider"></a>Création du fournisseur

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Pour créer un fournisseur OLE DB avec l’Assistant fournisseur OLE DB ATL

1. Cliquez sur le projet.

1. Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une classe**.

1. Dans le **ajouter une classe** boîte de dialogue **installé** > **Visual C++** > **ATL**, sélectionnez le **Fournisseur de ATL OLEDB** icône, puis cliquez sur **Open**.

1. Dans le **Assistant fournisseur OLE DB ATL**, entrez un nom court pour le fournisseur dans le **nom court** boîte. Les rubriques suivantes utilisent le nom court « MyProvider », mais vous pouvez utiliser un autre nom. Les autres zones de nom remplissent en fonction du nom que vous entrez.

1. Modifiez les autres zones, si nécessaire. Outre les noms d’objet et de fichier, il se peut que vous pouvez modifier les éléments suivants :

   - **Coclasse**: le nom utilisé par COM pour créer le fournisseur.

   - **ProgID**: l’identificateur programmatique, qui est une chaîne de texte qui peut être utilisée au lieu d’un GUID.

   - **Version**: utilisé avec ProgID et coclasse pour générer un ID programmatique de dépendants de la version.

1. Cliquez sur **Terminer**.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
