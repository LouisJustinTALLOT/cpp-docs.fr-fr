---
title: Création de nouveaux Documents, fenêtres et vues | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c0abc53e1a24d822605c9e5bfd7ab8276b32f82
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931204"
---
# <a name="creating-new-documents-windows-and-views"></a>Création de documents, fenêtres et vues
Les illustrations suivantes donnent une vue d’ensemble du processus de création de documents, vues et fenêtres frame. Autres articles qui vous concentrer sur les objets participants fournissent davantage d’informations.  
  
 À la fin de ce processus, les objets contributif existent et stockent les pointeurs vers les uns des autres. Les figures suivantes montrent la séquence dans laquelle les objets sont créés. Vous pouvez suivre la séquence d’illustration à.  
  
 ![Procédure de création d’un document](../mfc/media/vc387l1.gif "vc387l1")  
Séquence de création d’un Document  
  
 ![Séquence de création de fenêtre de frame](../mfc/media/vc387l2.png "vc387l2")  
Séquence de création d’une fenêtre Frame  
  
 ![Procédure de création d’une vue](../mfc/media/vc387l3.gif "vc387l3")  
Séquence de création d’une vue  
  
 Pour plus d’informations sur la façon dont le framework initialise du nouveau document, vue et les objets de la fenêtre frame, voir les classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dans la référence de la bibliothèque MFC. Consultez également [Note technique 22](../mfc/tn022-standard-commands-implementation.md), qui explique les processus de création et d’initialisation plus sous la discussion des commandes standard de l’infrastructure pour le **nouveau** et **ouvrir** sur les éléments de la **fichier** menu.  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> L’initialisation de vos propres ajouts à ces Classes  
 Les illustrations précédentes indiquent également les points à laquelle vous pouvez substituer des fonctions membres pour initialiser des objets de votre application. Une substitution de `OnInitialUpdate` dans votre vue de la classe est le meilleur endroit pour initialiser la vue. Le `OnInitialUpdate` appel se produit immédiatement après la création de la fenêtre frame et la vue dans la fenêtre frame est attachée à son document. Par exemple, si votre vue est une vue de défilement (dérivée de `CScrollView` plutôt que `CView`), vous devez définir la taille d’affichage en fonction de la taille du document dans votre `OnInitialUpdate` remplacer. (Ce processus est décrit dans la description de la classe [CScrollView](../mfc/reference/cscrollview-class.md).) Vous pouvez remplacer le `CDocument` fonctions membres `OnNewDocument` et `OnOpenDocument` pour fournir l’initialisation spécifique à l’application du document. En règle générale, vous devez substituer les deux dans la mesure où un document peut être créé de deux manières.  
  
 Dans la plupart des cas, votre substitution doit appeler la version classe de base. Pour plus d’informations, consultez les fonctions membres nommées des classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), et [CWinApp](../mfc/reference/cwinapp-class.md) dans la bibliothèque MFC Référence de la bibliothèque.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Création de modèle de document](../mfc/document-template-creation.md)   
 [La création de document/vue](../mfc/document-view-creation.md)   
 [Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)

