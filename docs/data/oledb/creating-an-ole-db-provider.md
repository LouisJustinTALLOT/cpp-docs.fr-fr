---
title: "Création d’un fournisseur OLE DB | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97d5edb8e65729f8bee68043b316fa74f78fb0da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-ole-db-provider"></a>Création d'un fournisseur OLE DB
La méthode recommandée pour créer un fournisseur OLE DB doit utiliser les Assistants pour créer un projet ATL COM et un fournisseur, puis modifier les fichiers en utilisant les modèles OLE DB. Quand vous personnalisez votre fournisseur, vous pouvez commenter les propriétés indésirables et ajouter des interfaces facultatives.  
  
 Les étapes de base sont les suivantes :  
  
1.  Utilisez l’Assistant Projet ATL pour créer les fichiers de projet de base et l’Assistant fournisseur OLE DB ATL pour créer le fournisseur (sélectionnez **fournisseur OLE DB ATL** à partir du dossier Visual C++ dans **ajouter une classe**).  
  
2.  Modifier le code dans la `Execute` méthode dans CMyProviderRS.h. Pour obtenir un exemple, consultez [lecture de chaînes dans le fournisseur OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Modifiez les mappages de propriété dans MyProviderDS.h, MyProviderSess.h et MyProviderRS.h. L’Assistant crée des mappages de propriété qui contiennent toutes les propriétés qu’un fournisseur peut implémenter. Parcourez les mappages de propriété et supprimez ou commentez les propriétés de votre fournisseur n’a pas besoin pour prendre en charge.  
  
4.  Mettre à jour de la macro PROVIDER_COLUMN_MAP, qui se trouve dans MyProviderRS.h. Pour obtenir un exemple, consultez [le stockage de chaînes dans le fournisseur OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Lorsque vous êtes prêt à tester votre fournisseur, vous pouvez le tester en essayant de trouver le fournisseur dans une énumération de fournisseurs. Pour obtenir des exemples de code de test qui retrouve un fournisseur dans une énumération, consultez la [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) et [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ou l’exemple fourni dans [implémentation d’un consommateur Simple](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Ajoutez les interfaces supplémentaires que vous le souhaitez. Pour obtenir un exemple, consultez [amélioration du fournisseur Simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Par défaut, les Assistants génèrent un code OLE DB conforme au niveau 0. Pour vous assurer que votre application conserve une conformité au niveau 0, ne supprimez pas une des interfaces générées par l’Assistant à partir du code.  
  
## <a name="see-also"></a>Voir aussi  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)