---
title: Modèles OLE DB, attributs et autres implémentations | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9baf43ded1533eb7f4962db7344f9dc1def0ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111170"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Modèles, attributs et autres implémentations OLE DB
## <a name="atl-ole-db-templates"></a>Modèles OLE DB ATL  
 Les modèles OLE DB, qui font partie d’ATL (Active Template Library), assurez-vous que la technologie de base de données OLE DB haute performance plus facile à utiliser en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées. Avec ce modèle de bibliothèque est prise en charge de l’Assistant pour la création d’applications de départ OLE DB.  
  
 Cette bibliothèque de modèles contient deux parties :  
  
-   **Modèles du consommateur OLE DB** utilisé pour implémenter une application de client (consommateur) OLE DB.  
  
-   **Modèles du fournisseur OLE DB** utilisé pour implémenter une application de serveur (fournisseur) OLE DB.  
  
 Pour utiliser les modèles OLE DB, vous devez bien connaître les modèles C++, COM et les interfaces OLE DB. Si vous n’êtes pas familiarisé avec OLE DB, consultez [de référence du programmeur OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx).  
  
 Pour plus d’informations, vous pouvez :  
  
-   Lisez les rubriques sur la [modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) ou [modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Créer un [consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) ou [fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Afficher la liste des [classes de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) ou [classes du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Afficher la liste des [exemples de modèles OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c).  
  
-   Consultez [de référence du programmeur OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (dans le SDK Windows).  
  
## <a name="ole-db-attributes"></a>Attributs OLE DB  
 Le [attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md) fournissent un moyen pratique pour créer des consommateurs OLE DB. Les attributs OLE DB injectent du code basé sur le [modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) pour créer des fournisseurs et consommateurs OLE DB de travail. Si vous devez spécifier une fonctionnalité non prise en charge par les attributs, vous pouvez utiliser les modèles OLE DB conjointement avec des attributs dans votre code.  
  
## <a name="mfc-ole-db-classes"></a>Classes MFC OLE DB  
 La bibliothèque MFC possède une classe, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), qui affiche des enregistrements de base de données dans des contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` de l’objet et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue. Il fournit également une implémentation par défaut pour le déplacement à la première, suivant, précédent ou le dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement affiché. Pour plus d'informations, consultez `COleDBRecordView`.  
  
## <a name="ole-db-sdk-interfaces"></a>Interfaces OLE DB SDK  
 Dans les cas où les modèles OLE DB ne prennent pas en charge la fonctionnalité OLE DB, vous devez utiliser les interfaces OLE DB elles-mêmes. Pour plus d’informations, consultez [de référence du programmeur OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB](../../data/oledb/ole-db-programming.md)   
 [Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)