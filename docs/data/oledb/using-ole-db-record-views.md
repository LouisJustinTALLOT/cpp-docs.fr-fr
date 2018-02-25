---
title: "À l’aide des vues des enregistrements OLE DB | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa7cfd6fba45c3d221d22fc7b8938addeef09d1a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="using-ole-db-record-views"></a>Utilisation des vues de l'enregistrement OLE DB
Si vous souhaitez afficher les données d’ensemble de lignes OLE DB dans une application MFC, vous devez utiliser la classe MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Un objet de vue de l’enregistrement créé à partir de `COleDBRecordView` vous permet d’afficher les enregistrements de base de données dans des contrôles MFC. La vue de l’enregistrement est une vue de formulaire de boîte de dialogue directement connectée à un objet de l’ensemble de lignes OLE DB créé à partir de la `CRowset` classe de modèle. Obtention d’un handle vers l’objet d’ensemble de lignes est simple :  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 La vue affiche les champs de la `CRowset` objet dans les contrôles de la boîte de dialogue. Le `COleDBRecordView` objet utilise l’échange de données de boîte de dialogue (DDX) et les fonctionnalités de navigation intégrées `CRowset` (**MoveFirst**, `MoveNext`, `MovePrev`, et `MoveLast`) pour automatiser le déplacement des données entre les contrôles sur le formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` effectue le suivi de position de l’utilisateur dans l’ensemble de lignes afin que la vue de l’enregistrement peut mettre à jour l’interface utilisateur et fournit un [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) méthode de mise à jour de l’enregistrement actif avant de passer à un autre.  
  
 Vous pouvez utiliser des fonctions DDX avec **COleDbRecordView** pour obtenir des données directement à partir de l’ensemble d’enregistrements de base de données et les afficher dans un contrôle de boîte de dialogue. Vous devez utiliser le **DDX_\***  méthodes (tel que `DDX_Text`), et non le **DDX_Field\***  fonctions (telles que `DDX_FieldText`) avec **COleDbRecordView** .  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’accesseurs](../../data/oledb/using-accessors.md)   
 [COleDBRecordView, classe](../../mfc/reference/coledbrecordview-class.md)