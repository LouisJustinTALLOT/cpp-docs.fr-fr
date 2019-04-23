---
title: Modèles, attributs et autres implémentations OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 0e6b5dbc97f6a7bea1df342d6a792ea43907ca33
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039583"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Modèles, attributs et autres implémentations OLE DB

## <a name="atl-ole-db-templates"></a>Modèles OLE DB ATL

Les modèles OLE DB, qui font partie d’ATL (Active Template Library), assurez-vous que la technologie de base de données OLE DB hautes performances plus facile à utiliser en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées. Avec ce modèle de bibliothèque est prise en charge de l’Assistant pour la création d’applications de départ OLE DB.

Cette bibliothèque de modèles contient deux parties :

- **Les modèles du consommateur OLE DB** permettent d’implémenter une application de client (consommateur) OLE DB.

- **Les modèles du fournisseur OLE DB** permettent d’implémenter une application de serveur (fournisseur) OLE DB.

Pour utiliser les modèles OLE DB, vous devez bien connaître les modèles C++, COM et les interfaces OLE DB. Si vous n’êtes pas familiarisé avec OLE DB, consultez [de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Pour plus d’informations, vous pouvez :

- Lisez les rubriques sur la [les modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) ou [les modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Créer un [consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) ou [fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md).

- Afficher la liste des [classes de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) ou [classes du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Afficher la liste des [exemples de modèles OLE DB](https://github.com/Microsoft/VCSamples).

- Consultez [de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (dans le Kit de développement logiciel Windows).

## <a name="ole-db-attributes"></a>Attributs du Kit de développement OLE DB

Le [attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md) offrent un moyen pratique pour créer des consommateurs OLE DB. Les attributs OLE DB injectent du code basé sur le [modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) pour la création de fournisseurs et consommateurs OLE DB de travail. Si vous avez besoin spécifier les fonctionnalités non prises en charge par les attributs, vous pouvez utiliser les modèles OLE DB conjointement avec des attributs dans votre code.

## <a name="mfc-ole-db-classes"></a>Classes MFC OLE DB

La bibliothèque MFC possède une classe, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), qui affiche les enregistrements de base de données dans les contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` de l’objet et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue. Il fournit également une implémentation par défaut pour le déplacement vers le premier, suivant, précédent ou le dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement dans la vue. Pour plus d'informations, consultez `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Interfaces OLE DB SDK

Dans les cas où les modèles OLE DB ne prennent en charge des fonctionnalités OLE DB, vous devez utiliser les interfaces OLE DB elles-mêmes. Pour plus d’informations, consultez [de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)