---
title: Utilisation des vues de l'enregistrement OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
ms.openlocfilehash: 631e78e1a397ec360b1f3b2d94d7340e96925e23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582710"
---
# <a name="using-ole-db-record-views"></a>Utilisation des vues de l'enregistrement OLE DB

Si vous souhaitez afficher les données d’ensemble de lignes OLE DB dans une application MFC, utilisez la classe MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Un objet de vue d’enregistrement est créé à partir de `COleDBRecordView` vous permet d’afficher les enregistrements de base de données dans les contrôles MFC. La vue de l’enregistrement est une vue de formulaire de boîte de dialogue directement connectée à un objet d’ensemble de lignes OLE DB créé à partir de la `CRowset` classe de modèle. Obtention d’un handle vers l’objet d’ensemble de lignes est simple :

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

La vue affiche les champs de la `CRowset` objet dans les contrôles de la boîte de dialogue. Le `COleDBRecordView` objet utilise l’échange de données de boîte de dialogue (DDX) et les fonctionnalités de navigation intégrée à `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, et `MoveLast`) pour automatiser le déplacement des données entre les contrôles sur le formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` effectue le suivi de position de l’utilisateur dans l’ensemble de lignes afin que la vue de l’enregistrement peut mettre à jour l’interface utilisateur et fournit un [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) méthode de mise à jour de l’enregistrement en cours avant de passer à un autre.

Vous pouvez utiliser des fonctions DDX avec `COleDbRecordView` pour obtenir des données directement à partir de l’ensemble d’enregistrements de base de données et les afficher dans un contrôle de boîte de dialogue. Utilisez le **DDX_** <strong>\*</strong> méthodes (telles que `DDX_Text`), et non le **DDX_Field** <strong>\*</strong> fonctions () comme `DDX_FieldText`) avec `COleDbRecordView`.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView, classe](../../mfc/reference/coledbrecordview-class.md)<br/>
