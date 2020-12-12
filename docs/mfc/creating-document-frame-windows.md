---
description: 'En savoir plus sur : création de fenêtres frame de document'
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
ms.openlocfilehash: e2c4f72ab56045df7bb121be3bb557314780fedb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309808"
---
# <a name="creating-document-frame-windows"></a>Création de fenêtres frame de document

La création d’un [document/](document-view-creation.md) d’une vue montre comment l’objet [CDocTemplate](reference/cdoctemplate-class.md) orchestre la création de la fenêtre frame, du document et de la vue et de la connexion de tous les deux. Trois arguments [CRuntimeClass](reference/cruntimeclass-structure.md) du `CDocTemplate` constructeur spécifient la fenêtre frame, le document et les classes de vue que le modèle de document crée dynamiquement en réponse à des commandes utilisateur telles que la commande nouveau du menu fichier ou la commande nouvelle fenêtre dans un menu Fenêtre MDI. Le modèle de document stocke ces informations pour une utilisation ultérieure lorsqu’il crée une fenêtre frame pour un affichage et un document.

Pour que le mécanisme de [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) fonctionne correctement, vos classes de fenêtres Frame dérivées doivent être déclarées avec la macro [DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate) . Cela est dû au fait que le Framework doit créer des fenêtres frame de document à l’aide du mécanisme de construction dynamique de la classe `CObject` .

Quand l’utilisateur choisit une commande qui crée un document, le Framework appelle sur le modèle de document pour créer l’objet de document, sa vue et la fenêtre frame qui affichera la vue. Lorsqu’il crée la fenêtre frame de document, le modèle de document crée un objet de la classe appropriée (une classe dérivée de [CFrameWnd](reference/cframewnd-class.md) pour une application SDI ou de [CMDIChildWnd](reference/cmdichildwnd-class.md) pour une application MDI). Le Framework appelle ensuite la fonction membre [LoadFrame](reference/cframewnd-class.md#loadframe) de l’objet fenêtre frame pour recevoir des informations de création à partir des ressources et pour créer la fenêtre Windows. L’infrastructure attache le handle de fenêtre à l’objet de fenêtre frame. Ensuite, il crée la vue en tant que fenêtre enfant de la fenêtre frame de document.

Soyez vigilant lorsque vous décidez [quand initialiser](when-to-initialize-cwnd-objects.md) votre `CWnd` objet dérivé de.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Dérivation d’une classe de CObject (son mécanisme de création dynamique)](deriving-a-class-from-cobject.md)

- [Création de document/vue (création de modèles et de fenêtres frames)](document-view-creation.md)

- [Destruction des fenêtres d’image](destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
