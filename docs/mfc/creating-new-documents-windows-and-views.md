---
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
ms.openlocfilehash: 57e558848ce76a7c74b5715529661ad24c9cbb8e
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175390"
---
# <a name="creating-new-documents-windows-and-views"></a>Création de documents, fenêtres et vues

Les illustrations suivantes donnent une vue d’ensemble du processus de création de documents, vues et fenêtres frame. Autres articles qui vous concentrer sur les objets qui participent fournissent d’autres informations.

À la fin de ce processus, les objets coopérant existent et stockent les pointeurs vers les uns des autres. Les figures suivantes illustrent la séquence dans laquelle les objets sont créés. Vous pouvez suivre la séquence à partir d’une illustration à.

![Séquence de création d’un document](../mfc/media/vc387l1.gif "séquence pour la création d’un document") <br/>
Séquence de création d’un Document

![Séquence de création de fenêtre de frame](../mfc/media/vc387l2.png "séquence de création de fenêtre de Frame") <br/>
Séquence de création d’une fenêtre Frame

![Séquence de création d’une vue](../mfc/media/vc387l3.gif "séquence pour la création d’une vue") <br/>
Séquence de création d’une vue

Pour plus d’informations sur la façon dont le framework initialise le nouveau document, vue et les objets de fenêtre frame, consultez la section classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dans la référence de la bibliothèque MFC. Consultez également [Note technique 22](../mfc/tn022-standard-commands-implementation.md), qui explique les processus de création et d’initialisation supplémentaires sous sa discussion des commandes standard de l’infrastructure pour le **New** et **ouvrir** éléments sur le **fichier** menu.

##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> L’initialisation de vos propres ajouts à ces Classes

Les figures précédentes indiquent également les points à partir duquel vous pouvez substituer des fonctions membres pour initialiser des objets de votre application. Une substitution de `OnInitialUpdate` dans votre vue de la classe est le meilleur endroit pour initialiser la vue. Le `OnInitialUpdate` appel se produit immédiatement après la fenêtre frame est créée et la vue dans la fenêtre frame est attachée à son document. Par exemple, si votre vue est une vue de défilement (dérivée de `CScrollView` plutôt que `CView`), vous devez définir la taille d’affichage en fonction de la taille du document dans votre `OnInitialUpdate` remplacer. (Ce processus est décrit dans la description de la classe [CScrollView](../mfc/reference/cscrollview-class.md).) Vous pouvez remplacer le `CDocument` fonctions membres `OnNewDocument` et `OnOpenDocument` pour fournir l’initialisation spécifique à l’application du document. En règle générale, vous devez substituer les deux dans la mesure où un document peut être créé de deux manières.

Dans la plupart des cas, votre substitution doit appeler la version de la classe de base. Pour plus d’informations, consultez les fonctions membres nommées des classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), et [CWinApp](../mfc/reference/cwinapp-class.md) dans la bibliothèque MFC Référence de la bibliothèque.

## <a name="see-also"></a>Voir aussi

[Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création de modèle de document](../mfc/document-template-creation.md)<br/>
[Création d’un document/vue](../mfc/document-view-creation.md)<br/>
[Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)

