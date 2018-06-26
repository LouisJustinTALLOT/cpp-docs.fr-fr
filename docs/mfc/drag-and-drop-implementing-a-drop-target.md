---
title: 'Glisser -déplacer : implémentation d’une cible de dépôt | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33088477c579cbdfe48140b806c6376b520e470c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928916"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Glisser-déposer : implémentation d’une cible de dépôt
Cet article explique comment rendre votre application à une cible de dépôt. Implémentation d’une cible de dépôt prend plus de temps que l’implémentation d’une source de déplacement, mais elle est toujours relativement simple. Ces techniques s’appliquent également aux applications non-OLE.  
  
#### <a name="to-implement-a-drop-target"></a>Pour implémenter une cible de dépôt  
  
1.  Ajouter une variable membre à chaque vue dans l’application que vous souhaitez être une cible de dépôt. Cette variable membre doit être de type `COleDropTarget` ou à une classe dérivée.  
  
2.  À partir de la fonction de la classe d’affichage qui gère la **WM_CREATE** message (généralement `OnCreate`), appelez la nouvelle variable de membre `Register` fonction membre. `Revoke` sera appelé automatiquement pour vous lors de la destruction de la vue.  
  
3.  Substituer les fonctions suivantes. Si vous souhaitez que le même comportement dans l’ensemble de votre application, substituez ces fonctions dans votre classe d’affichage. Si vous souhaitez modifier le comportement dans certains cas isolés ou souhaitez activer la suppression non -`CView` windows, remplacez ces fonctions dans votre `COleDropTarget`-classe dérivée.  
  
    |Remplacer|Pour autoriser|  
    |--------------|--------------|  
    |`OnDragEnter`|Supprimer les opérations dans la fenêtre. Appelé lorsque le curseur entre d’abord dans la fenêtre.|  
    |`OnDragLeave`|Comportement spécial lorsque l’opération de glissement quitte la fenêtre spécifiée.|  
    |`OnDragOver`|Supprimer les opérations dans la fenêtre. Appelé lorsque le curseur est déplacé dans la fenêtre.|  
    |`OnDrop`|La gestion des données en cours de suppression dans la fenêtre spécifiée.|  
    |`OnScrollBy`|Comportement spécial lorsque le défilement est nécessaire dans la fenêtre cible.|  
  
 Consultez le fichier MAINVIEW. Cpp qui fait partie de l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) pour obtenir un exemple de la façon dont ces fonctions fonctionnent ensemble.  
  
 Pour plus d'informations, voir :  
  
-   [Implémentation d’une Source de dépôt](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Création et la destruction des Sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulation des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Glisser -déplacer (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget, classe](../mfc/reference/coledroptarget-class.md)
