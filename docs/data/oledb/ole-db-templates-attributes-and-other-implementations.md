---
title: Modèles, attributs et autres implémentations OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 217db304c7d0b5723b7af383e07290f160cc9465
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500922"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Modèles, attributs et autres implémentations OLE DB

## <a name="atl-ole-db-templates"></a>Modèles de OLE DB ATL

Les modèles de OLE DB, qui font partie d’ATL (Active Template Library), facilitent l’utilisation de la technologie de base de données OLE DB de performances en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées. En plus de cette bibliothèque de modèles, la prise en charge de l’Assistant pour la création d’applications OLE DB démarre.

Cette bibliothèque de modèles contient deux parties :

- **Modèles de consommateur OLE DB** Utilisé pour implémenter une application cliente OLE DB (consommateur).

- **Modèles du fournisseur OLE DB** Utilisé pour implémenter une application de serveur OLE DB (fournisseur).

Pour utiliser les modèles OLE DB, vous devez bien connaître les modèles C++, COM et les interfaces OLE DB. Si vous n’êtes pas familiarisé avec OLE DB, consultez [Guide de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Pour plus d’informations, vous pouvez :

- Lisez les rubriques relatives aux modèles de [consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) ou aux [modèles de fournisseur d’OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Créez un [OLE DB consommateur](../../data/oledb/creating-an-ole-db-consumer.md) ou un [fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md).

- Consultez la liste des classes de [consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) ou des [classes de fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Consultez la liste des [exemples de modèles de OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB).

- Consultez [OLE DB Guide de référence du programmeur](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (dans le SDK Windows).

## <a name="ole-db-attributes"></a>Attributs OLE DB

Les [attributs du consommateur OLE DB](../../windows/attributes/ole-db-consumer-attributes.md) offrent un moyen pratique de créer des OLE DB consommateurs. Les attributs OLE DB injectent du code basé sur les [modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) pour créer des consommateurs et des fournisseurs OLE DB. Si vous devez spécifier une fonctionnalité qui n’est pas prise en charge par les attributs, vous pouvez utiliser les modèles de OLE DB conjointement aux attributs dans votre code.

## <a name="mfc-ole-db-classes"></a>Classes de OLE DB MFC

La bibliothèque MFC a une classe, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), qui affiche des enregistrements de base de données dans des contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` objet et affiche les champs de l' `CRowset` objet dans les contrôles du modèle de boîte de dialogue. Il fournit également une implémentation par défaut pour passer au premier enregistrement, suivant, précédent ou dernier, ainsi qu’une interface pour la mise à jour de l’enregistrement actuellement affiché. Pour plus d'informations, consultez `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Interfaces du kit de développement logiciel OLE DB

Dans les cas où les modèles de OLE DB ne prennent pas en charge OLE DB fonctionnalité, vous devez utiliser les interfaces OLE DB elles-mêmes. Pour plus d’informations, consultez [OLE DB Guide de référence du programmeur](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
