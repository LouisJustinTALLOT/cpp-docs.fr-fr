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
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371663"
---
# <a name="creating-new-documents-windows-and-views"></a>Création de documents, fenêtres et vues

Les chiffres suivants donnent un aperçu du processus de création des documents, des vues et des fenêtres de cadre. D’autres articles qui mettent l’accent sur les objets participants fournissent plus de détails.

Une fois ce processus terminé, les objets coopérants existent et stockent des indications les uns aux autres. Les chiffres suivants montrent la séquence dans laquelle les objets sont créés. Vous pouvez suivre la séquence d’une figure à l’autre.

![Séquence de la création d'un document](../mfc/media/vc387l1.gif "Séquence de la création d'un document") <br/>
Séquence dans la création d’un document

![Séquence de création d'une fenêtre frame](../mfc/media/vc387l2.png "Séquence de création d'une fenêtre frame") <br/>
Séquence dans la création d’une fenêtre de cadre

![Séquence de la création d'une vue](../mfc/media/vc387l3.gif "Séquence de la création d'une vue") <br/>
Séquence dans la création d’une vue

Pour plus d’informations sur la façon dont le cadre initialise le nouveau document, la vue et les objets de fenêtre de cadre, voir les classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dans la référence de bibliothèque MFC. Voir également [la note technique 22](../mfc/tn022-standard-commands-implementation.md), qui explique les processus de création et d’initialisation plus loin dans le cadre de sa discussion des commandes standard du cadre pour les éléments **nouveaux** et **ouverts** sur le menu **du fichier.**

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Initialiser vos propres ajouts à ces classes

Les chiffres précédents suggèrent également les points auxquels vous pouvez remplacer les fonctions des membres pour initialiser les objets de votre application. Un remplacement `OnInitialUpdate` de dans votre classe de vue est le meilleur endroit pour initialiser la vue. L’appel `OnInitialUpdate` se produit immédiatement après la création de la fenêtre du cadre et la vue dans la fenêtre du cadre est attachée à son document. Par exemple, si votre vue est `CScrollView` une `CView`vue de défilement (dérivée de `OnInitialUpdate` plutôt que), vous devez définir la taille de vue en fonction de la taille du document dans votre remplacement. (Ce processus est décrit dans la description de la classe [CScrollView](../mfc/reference/cscrollview-class.md).) Vous pouvez remplacer `CDocument` les `OnNewDocument` fonctions des membres et `OnOpenDocument` fournir une initialisation spécifique à l’application du document. En règle générale, vous devez passer outre les deux car un document peut être créé de deux façons.

Dans la plupart des cas, votre remplacement devrait appeler la version de la classe de base. Pour plus d’informations, consultez les fonctions des membres nommés des classes [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), et [CWinApp](../mfc/reference/cwinapp-class.md) dans la référence de bibliothèque MFC.

## <a name="see-also"></a>Voir aussi

[Modèles de documents et processus de création de documents/vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création de modèle de document](../mfc/document-template-creation.md)<br/>
[Création d'un document/d'une vue](../mfc/document-view-creation.md)<br/>
[Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)
