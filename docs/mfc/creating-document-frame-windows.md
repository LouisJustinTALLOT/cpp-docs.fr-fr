---
title: Création de fenêtres Frame de Document | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4b27154197e4e8347e73936f319aeb416a153d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342941"
---
# <a name="creating-document-frame-windows"></a>Création de fenêtres frame de document
[Création de document/vue](../mfc/document-view-creation.md) montre comment la [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objet orchestre la création de la fenêtre frame, le document et la vue et en les connectant ensemble. Trois [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) arguments à la `CDocTemplate` constructeur spécifie la fenêtre frame, document et les classes d’affichage du modèle de document crée dynamiquement en réponse à des commandes telles que la commande Nouveau dans le fichier de l’utilisateur menu ou la commande nouvelle fenêtre dans un menu Fenêtre MDI. Le modèle de document stocke ces informations pour une utilisation ultérieure lorsqu’il crée une fenêtre frame pour une vue ou d’un document.  
  
 Pour le [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mécanisme fonctionne correctement, votre dérivées des classes de fenêtre frame doivent être déclarés avec le [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) (macro). Il s’agit, car l’infrastructure doit créer des fenêtres frame à l’aide du mécanisme de construction dynamique de la classe de document `CObject`.  
  
 Lorsque l’utilisateur choisit une commande qui crée un document, le framework appelle le modèle de document pour créer l’objet de document, sa vue et la fenêtre frame qui affiche la vue. Lorsqu’il crée la fenêtre frame de document, le modèle de document crée un objet de la classe appropriée, une classe dérivée de [CFrameWnd](../mfc/reference/cframewnd-class.md) pour une application SDI ou de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) pour un formulaire MDI application. Le framework appelle ensuite l’objet fenêtre frame [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) fonction membre pour obtenir des informations sur la création des ressources et de créer la fenêtre Windows. L’infrastructure attache le handle de fenêtre à l’objet fenêtre frame. Il crée ensuite la vue comme une fenêtre enfant de la fenêtre frame de document.  
  
 Soyez prudent lorsque vous déterminez de [quand initialiser](../mfc/when-to-initialize-cwnd-objects.md) votre `CWnd`-objet dérivé.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Dérivation d’une classe de CObject (son mécanisme de création dynamique)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Création de document/vue (modèles et création de la fenêtre frame)](../mfc/document-view-creation.md)  
  
-   [Détruire des fenêtres frame](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

