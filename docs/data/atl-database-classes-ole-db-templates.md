---
title: Classes de bases de données ATL (modèles OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: dc016a5e1e1d9652f6a69f73b5760f42dec5e889
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222556"
---
# <a name="atl-database-classes-ole-db-templates"></a>Classes de bases de données ATL (modèles OLE DB)

Microsoft fournit plusieurs implémentations d’OLE DB, un ensemble d’interfaces COM qui assurent un accès uniforme aux données de diverses sources d’informations et de formats.

Les modèles OLE DB sont des modèles C++ dans ATL qui facilitent la technologie de base de données OLE DB à utiliser en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées.

Cette bibliothèque de modèles contient deux parties :

- [Modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) permettent d’implémenter une application de client (consommateur) OLE DB.

- [Modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) permettent d’implémenter une application de serveur (fournisseur) OLE DB.

En outre, le [attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md) offrent un moyen pratique pour créer des consommateurs OLE DB. Les attributs OLE DB injectent du code basé sur les modèles du consommateur OLE DB pour créer des consommateurs OLE DB de travail.

Notez que la bibliothèque MFC contient une classe, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), qui affiche les enregistrements de base de données dans les contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` de l’objet et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue.

Pour plus d’informations, consultez [programmation OLE DB](../data/oledb/ole-db-programming.md) et [Guide du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Création d’un fournisseur OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Référence des modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Référence des modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Exemples de modèles OLE DB](https://github.com/Microsoft/VCSamples)
