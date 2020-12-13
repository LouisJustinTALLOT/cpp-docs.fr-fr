---
description: 'En savoir plus sur : utilisation des vues d’enregistrement OLE DB'
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
ms.openlocfilehash: 8230ba118038852f81159d21a51165b7448a26aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332462"
---
# <a name="using-ole-db-record-views"></a>Utilisation des vues de l'enregistrement OLE DB

Si vous souhaitez afficher OLE DB données de l’ensemble de lignes dans une application MFC, utilisez la classe MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Un objet de vue d’enregistrement créé à partir de `COleDBRecordView` vous permet d’afficher les enregistrements de base de données dans les contrôles MFC. La vue d’enregistrement est une vue de formulaire de boîte de dialogue directement connectée à un objet d’ensemble de lignes OLE DB créé à partir de la `CRowset` classe de modèle. L’obtention d’un handle vers l’objet rowset est simple :

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

La vue affiche les champs de l' `CRowset` objet dans les contrôles de la boîte de dialogue. L' `COleDBRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et les fonctionnalités de navigation intégrées `CRowset` `MoveFirst` à (, `MoveNext` , `MovePrev` et `MoveLast` ) pour automatiser le déplacement des données entre les contrôles du formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` effectue le suivi de la position de l’utilisateur dans l’ensemble de lignes afin que la vue de l’enregistrement puisse mettre à jour l’interface utilisateur et fournit une méthode [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) pour mettre à jour l’enregistrement en cours avant de passer à un autre.

Vous pouvez utiliser les fonctions DDX avec `COleDbRecordView` pour obtenir des données directement à partir de l’ensemble d’enregistrements de la base de données et les afficher dans un contrôle de boîte de dialogue. Utilisez les méthodes **DDX_** <strong>\*</strong> (telles que `DDX_Text` ), et non les fonctions **DDX_Field** <strong>\*</strong> (telles que `DDX_FieldText` ) avec `COleDbRecordView` .

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView (classe)](../../mfc/reference/coledbrecordview-class.md)<br/>
