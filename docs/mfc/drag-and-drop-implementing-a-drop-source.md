---
title: 'Glisser -déplacer : Implémentation d’une Source de dépôt'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: 2aa593fa953f7a9874036d48124ae7b92d88e0a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219754"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Glisser -déplacer : Implémentation d’une Source de dépôt

Cet article explique comment obtenir votre application pour fournir des données à une opération de glisser-déplacer.

Implémentation de base d’une source de dépôt est relativement simple. La première étape consiste à déterminer les événements qui commencent une opération glisser. Recommandé d’indications de l’interface utilisateur définissent le début d’une opération glisser en tant que la sélection des données et un **WM_LBUTTONDOWN** événement se produisant sur un point de données sélectionnées. Les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md) suivez ces instructions.

Si votre application est un conteneur et les données sélectionnées sont un objet lié ou incorporé de type `COleClientItem`, appeler ses `DoDragDrop` fonction membre. Sinon, construire un `COleDataSource` de l’objet, initialisez-la avec la sélection et appeler l’objet de source de données `DoDragDrop` fonction membre. Si votre application est un serveur, utilisez `COleServerItem::DoDragDrop`. Pour plus d’informations sur la personnalisation du comportement de glisser-déplacer standard, consultez l’article [glisser -déplacer : Personnalisation](../mfc/drag-and-drop-customizing.md).

Si `DoDragDrop` retourne **DROPEFFECT_MOVE**, supprimer la source de données à partir du document source immédiatement. Aucune autre valeur de retour à partir de `DoDragDrop` a un effet sur une source de dépôt.

Pour plus d'informations, voir :

- [Implémentation d’une cible de dépôt](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Personnalisation de glisser- déposer](../mfc/drag-and-drop-customizing.md)

- [Création et la destruction des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulation des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Voir aussi

[Glisser-déposer (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
