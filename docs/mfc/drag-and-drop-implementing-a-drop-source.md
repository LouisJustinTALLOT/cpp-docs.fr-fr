---
title: 'Glisser -déplacer : implémentation d’une Source de dépôt | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c057657605296b3ba65128f26b25aa526f45b211
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345610"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Glisser-déposer : implémentation d’une source de dépôt
Cet article explique comment obtenir votre application pour fournir des données à une opération de glisser-déplacer.  
  
 Implémentation de base d’une source de déplacement est relativement simple. La première étape consiste à déterminer quels événements commenceront une opération glisser. Recommandé d’indications de l’interface utilisateur définissent le début d’une opération de glissement de la sélection de données et un `WM_LBUTTONDOWN` événement se produisant sur un point de données sélectionnées. Les exemples OLE MFC [OCLIENT](../visual-cpp-samples.md) et [HIERSVR](../visual-cpp-samples.md) suivez ces instructions.  
  
 Si votre application est un conteneur et les données sélectionnées seront lié ou un objet incorporé de type `COleClientItem`, appelez sa `DoDragDrop` fonction membre. Sinon, construisez un `COleDataSource` de l’objet, initialisez-la avec la sélection et appeler l’objet de source de données `DoDragDrop` fonction membre. Si votre application est un serveur, utilisez `COleServerItem::DoDragDrop`. Pour plus d’informations sur la personnalisation du comportement de glisser-déplacer standard, consultez l’article [glisser -déplacer : personnalisation](../mfc/drag-and-drop-customizing.md).  
  
 Si `DoDragDrop` retourne `DROPEFFECT_MOVE`, supprimer la source de données à partir du document source immédiatement. Aucune autre valeur de retour `DoDragDrop` a un effet sur une source de déplacement.  
  
 Pour plus d'informations, voir :  
  
-   [Implémentation d’une cible de dépôt](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Personnalisation de glisser- déposer](../mfc/drag-and-drop-customizing.md)  
  
-   [Création et la destruction des Sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulation des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Glisser -déplacer (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)   
 [COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)   
 [CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)

