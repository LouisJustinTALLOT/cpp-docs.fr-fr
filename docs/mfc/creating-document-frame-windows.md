---
title: Création de fenêtres frame de document
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: 66a951994a75cbd99debeb2c6511739411cdd470
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265996"
---
# <a name="creating-document-frame-windows"></a>Création de fenêtres frame de document

[Création de document/vue](../mfc/document-view-creation.md) montre comment la [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objet orchestre la création de la fenêtre frame, le document et la vue et en les connectant ensemble. Trois [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) arguments à la `CDocTemplate` constructeur spécifier la fenêtre frame, document et les classes d’affichage du modèle de document crée dynamiquement en réponse aux commandes utilisateur telles que la nouvelle commande sur le fichier menu ou la commande nouvelle fenêtre dans un menu Fenêtre MDI. Le modèle de document stocke ces informations pour une utilisation ultérieure lorsqu’il crée une fenêtre frame pour une vue et le document.

Pour le [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mécanisme fonctionne correctement, votre dérivée des classes de fenêtre frame doivent être déclarés avec le [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) macro. Il s’agit, car l’infrastructure a besoin créer des fenêtres frame à l’aide du mécanisme de construction dynamique de classe de document `CObject`.

Lorsque l’utilisateur choisit une commande qui crée un document, le framework appelle le modèle de document pour créer l’objet de document, sa vue et la fenêtre frame qui affiche la vue. Lorsqu’il crée la fenêtre frame de document, le modèle de document crée un objet de la classe appropriée, une classe dérivée de [CFrameWnd](../mfc/reference/cframewnd-class.md) pour une application SDI ou à partir de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) pour un formulaire MDI application. Le framework appelle ensuite l’objet fenêtre frame [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) fonction membre pour obtenir des informations sur la création des ressources et créer la fenêtre Windows. L’infrastructure attache le handle de fenêtre à l’objet de fenêtre frame. Il crée ensuite la vue en tant que fenêtre enfant de la fenêtre frame de document.

Soyez prudent dans la décision [quand initialiser](../mfc/when-to-initialize-cwnd-objects.md) votre `CWnd`-objet dérivé.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Dérivation d’une classe de CObject (son mécanisme de création dynamique)](../mfc/deriving-a-class-from-cobject.md)

- [Création de document/vue (modèles et création de la fenêtre frame)](../mfc/document-view-creation.md)

- [Destruction des fenêtres frame](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)
