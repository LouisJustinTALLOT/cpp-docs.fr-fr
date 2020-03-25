---
title: Classes de bases de données ATL (modèles OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 76e9f49d4b394d0c807ca1f3d103ff325ded8a09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213497"
---
# <a name="atl-database-classes-ole-db-templates"></a>Classes de bases de données ATL (modèles OLE DB)

Microsoft fournit plusieurs implémentations de OLE DB, un ensemble d’interfaces COM qui fournissent un accès uniforme aux données dans divers formats et sources d’informations.

Les modèles OLE DB sont C++ des modèles dans ATL qui facilitent l’utilisation des technologies de base de données OLE DB en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées.

Cette bibliothèque de modèles contient deux parties :

- [Modèles de consommateur OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) Utilisé pour implémenter une application cliente OLE DB (consommateur).

- [Modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) Utilisé pour implémenter une application de serveur OLE DB (fournisseur).

En outre, les [attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md) offrent un moyen pratique de créer des OLE DB consommateurs. Les attributs OLE DB injectent du code basé sur les modèles de consommateurs OLE DB pour créer des consommateurs de OLE DB fonctionnels.

Notez que la bibliothèque MFC contient une classe, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), qui affiche des enregistrements de base de données dans des contrôles. La vue est une vue de formulaire directement connectée à un objet `CRowset` et affiche les champs de l’objet `CRowset` dans les contrôles du modèle de boîte de dialogue.

Pour plus d’informations, consultez [OLE DB programmation](../data/oledb/ole-db-programming.md) et [OLE DB Guide du programmeur](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Création d’un fournisseur OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Référence des modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Référence des modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Exemples de modèles OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
