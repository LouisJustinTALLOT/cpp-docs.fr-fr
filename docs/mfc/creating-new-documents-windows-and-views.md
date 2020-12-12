---
description: 'En savoir plus sur : création de documents, fenêtres et vues'
title: Création de documents, fenêtres et vues
ms.date: 11/19/2018
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
ms.openlocfilehash: 718d24d63811d4e3b5cc847b5d0ef69361c6fdf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309873"
---
# <a name="creating-new-documents-windows-and-views"></a>Création de documents, fenêtres et vues

Les figures suivantes donnent une vue d’ensemble du processus de création des documents, des vues et des fenêtres Frame. D’autres articles qui se concentrent sur les objets participants fournissent des détails supplémentaires.

À la fin de ce processus, les objets coopérants existent et stockent les pointeurs les uns sur les autres. Les figures suivantes illustrent l’ordre dans lequel les objets sont créés. Vous pouvez suivre la séquence de la figure à la figure.

![Séquence de la création d'un document](../mfc/media/vc387l1.gif "Séquence de la création d'un document") <br/>
Séquence de création d’un document

![Séquence de création d'une fenêtre frame](../mfc/media/vc387l2.png "Séquence de création d'une fenêtre frame") <br/>
Séquence dans la création d’une fenêtre frame

![Séquence de la création d'une vue](../mfc/media/vc387l3.gif "Séquence de la création d'une vue") <br/>
Séquence de création d’une vue

Pour plus d’informations sur la façon dont l’infrastructure initialise les nouveaux objets document, vue et fenêtre frame, consultez classes [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)et [CMDIChildWnd](reference/cmdichildwnd-class.md) dans la référence de la bibliothèque MFC. Consultez également la [note technique 22](tn022-standard-commands-implementation.md), qui explique les processus de création et d’initialisation plus en détail dans la discussion des commandes standard du Framework pour les éléments **nouveaux** et **ouverts** dans le menu **fichier** .

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a> Initialisation de vos propres ajouts à ces classes

Les figures précédentes suggèrent également les points à partir desquels vous pouvez substituer des fonctions membres pour initialiser les objets de votre application. Une substitution de `OnInitialUpdate` dans votre classe d’affichage est le meilleur emplacement pour initialiser la vue. L' `OnInitialUpdate` appel se produit immédiatement après la création de la fenêtre frame et la vue dans la fenêtre frame est attachée à son document. Par exemple, si votre vue est une vue de défilement (dérivée de `CScrollView` au lieu de `CView` ), vous devez définir la taille de la vue en fonction de la taille du document dans votre `OnInitialUpdate` remplacement. (Ce processus est décrit dans la description de la classe [CScrollView](reference/cscrollview-class.md).) Vous pouvez substituer les `CDocument` fonctions membres `OnNewDocument` et `OnOpenDocument` fournir l’initialisation propre à l’application du document. En règle générale, vous devez remplacer les deux, car un document peut être créé de deux façons.

Dans la plupart des cas, votre substitution doit appeler la version de la classe de base. Pour plus d’informations, consultez les fonctions membres nommées des classes [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md)et [CWINAPP](reference/cwinapp-class.md) dans la référence de la bibliothèque MFC.

## <a name="see-also"></a>Voir aussi

[Modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md)<br/>
[Création d’un modèle de document](document-template-creation.md)<br/>
[Création de document/vue](document-view-creation.md)<br/>
[Relations entre les objets MFC](relationships-among-mfc-objects.md)
