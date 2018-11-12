---
title: Classes d'architecture des applications MFC
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 3287ac31744506720f1c5c1080a6225311f0e3a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512759"
---
# <a name="mfc-application-architecture-classes"></a>Classes d'architecture des applications MFC

Les classes de cette catégorie contribuent à l'architecture d'une application framework. Elles fournissent la fonctionnalité commune à la plupart des applications. Vous remplissez le framework pour ajouter des fonctionnalités spécifiques à l'application. En général, cela se produit en faisant dériver de nouvelles classes à partir des classes de l'architecture, puis en ajoutant de nouveaux membres ou en remplaçant les fonctions membres existantes.

[Les Assistants application](../mfc/reference/mfc-application-wizard.md) générer plusieurs types d’applications, qui utilisent l’infrastructure d’application de différentes façons. Les applications SDI (interface monodocument) et MDI (interface multidocument) utilisent pleinement le framework appelée architecture Document/Vue. D’autres types d’applications, telles que les applications basées sur les boîtes de dialogue, sur les formulaires et les DLL, utilisent uniquement certaines des fonctionnalités de l’architecture Document/Vue.

Les applications Document/Vue contiennent un ou plusieurs jeux de documents, de vues et fenêtres frame. Un objet de modèle de document associe les classes pour chaque document/vue/ensemble de frames.

Bien que vous ne devez pas utiliser l'architecture Document/Vue dans votre application MFC, il existe de nombreux avantages à le faire. La prise en charge du conteneur et du serveur OLE MFC est basée sur l'architecture Document/Vue, comme prise en charge d'impression et d'aperçu avant impression.

Toutes les applications MFC ont au moins deux objets : un objet application dérivé [CWinApp](../mfc/reference/cwinapp-class.md)et une sorte d’objet de la fenêtre principale, dérivé (souvent indirectement) [CWnd](../mfc/reference/cwnd-class.md). (Le plus souvent, la fenêtre principale est dérivée de [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), ou [CDialog](../mfc/reference/cdialog-class.md), qui sont dérivés de `CWnd`.)

Les applications qui utilisent l'architecture Document/Vue contiennent des objets supplémentaires. Les principaux objets sont :

- Un objet d’application dérivée de la classe [CWinApp](../mfc/reference/cwinapp-class.md), comme indiqué précédemment.

- Un ou plusieurs objets de classe de document dérivée de la classe [CDocument](../mfc/reference/cdocument-class.md). Les objets de classe de document sont responsables de la représentation interne des données manipulées dans la vue. Ils peuvent être associés à un fichier de données.

- Un ou plusieurs objets de vue dérivé de la classe [CView](../mfc/reference/cview-class.md). Chaque vue est une fenêtre qui est associée à un élément et associée à une fenêtre frame. Les vues affichent et manipulent les données contenues dans un objet de classe de document.

Les applications de document/vue contiennent également des fenêtres frame (dérivées de [CFrameWnd](../mfc/reference/cframewnd-class.md)) et les modèles de document (dérivée de [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

