---
title: Classes de base de données ATL (modèles OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabced79232d17807d252da9dac5b066ddf69f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089050"
---
# <a name="atl-database-classes-ole-db-templates"></a>Classes de bases de données ATL (modèles OLE DB)
Microsoft fournit plusieurs implémentations d’OLE DB, un ensemble d’interfaces COM qui assurent un accès uniforme aux données de diverses sources d’informations et de formats.  OLE DB est officiellement déconseillée ; Cette documentation est destiné aux développeurs chargés de la maintenance code hérité. Nouvelles applications doivent utiliser ODBC pour se connecter aux sources de données SQL.
  
 Les modèles OLE DB sont des modèles C++ dans ATL qui simplifient la technologie de base de données OLE DB à utiliser en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées.  
  
 Cette bibliothèque de modèles contient deux parties :  
  
-   [Modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) utilisé pour implémenter une application de client (consommateur) OLE DB.  
  
-   [Modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) utilisé pour implémenter une application de serveur (fournisseur) OLE DB.  
  
 En outre, le [attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md) fournissent un moyen pratique pour créer des consommateurs OLE DB. OLE DB injectent du code basé sur les modèles du consommateur OLE DB pour créer des consommateurs OLE DB de travail.  
  
 Notez que la bibliothèque MFC contient une classe, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), qui affiche des enregistrements de base de données dans des contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` de l’objet et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue.  
  
 Pour plus d’informations, consultez [programmation OLE DB](../data/oledb/ole-db-programming.md) et [Guide du programmeur OLE DB](http://go.microsoft.com/fwlink/p/?linkid=121548).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un consommateur OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Création d’un fournisseur OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Référence des modèles de consommateur OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Référence des modèles de fournisseur OLE DB](../data/oledb/ole-db-provider-templates-reference.md)   
 [Exemples de modèles OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)