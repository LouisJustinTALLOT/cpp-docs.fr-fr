---
title: Création d'une application MFC de style Explorateur de fichiers
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 16969b7ef9c0447dfce971af8d329c5b93367041
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372242"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Création d'une application MFC de style Explorateur de fichiers

De nombreuses applications de système de Windows utilisent l’interface utilisateur (IU) de l’Explorateur de fichiers. Lorsque vous démarrez l’Explorateur de fichiers, par exemple, vous voyez une application avec un séparateur vertical de la barre séparant la zone cliente. Fournit des fonctionnalités de navigation et le côté gauche de la zone cliente et le côté droit de la zone cliente affiche des détails relatifs à la sélection dans le volet gauche. Lorsqu’un utilisateur clique sur un élément dans le volet gauche, l’application remplit à nouveau le volet de droite. Dans une application MDI, vous pouvez utiliser des commandes sur le **vue** menu pour modifier la quantité de détail affiché dans le volet droit. (Dans une interface SDI ou plusieurs applications de document de niveau supérieur, vous pouvez modifier les détails en utilisant les boutons de barre d’outils uniquement.)

Le contenu des volets dépend de l’application. Dans un navigateur de système de fichiers, le volet gauche affiche une vue hiérarchique des répertoires ou des machines ou des groupes d’ordinateurs, tandis que le volet droit affiche les dossiers, des fichiers individuels, ou ordinateurs et les détails. Le contenu n’ont pas nécessairement être des fichiers. Elles peuvent être des messages électroniques, de rapports d’erreurs ou d’autres éléments dans une base de données.

L’Assistant crée les classes suivantes pour vous :

- Le `CLeftView` classe définit le volet gauche de la zone cliente. Il est toujours dérivé [CTreeView](../../mfc/reference/ctreeview-class.md).

- Le C*ProjName*classe View définit le volet droit de la zone cliente. Par défaut, il est dérivé [CListView](../../mfc/reference/clistview-class.md) mais peut être un autre type de vue en fonction de la classe spécifiée à partir de la **classe de Base** liste dans le [Classes générées par](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de la Assistant.

L’application générée peut avoir une interface monodocument (SDI), une interface multidocument (MDI) ou une architecture à plusieurs documents de niveau supérieur. Chaque fenêtre frame crée l’application est divisée verticalement à l’aide de [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Codage de ce type d’application est semblable au codage d’une application MFC normale qui utilise un séparateur, à ceci près que ce type d’application dispose de vues de contrôle distincts au sein de chaque volet de fractionnement.

Si vous utilisez l’affichage de liste par défaut dans le volet droit, l’Assistant crée des choix de menu supplémentaires (dans les applications MDI uniquement) et les boutons de barre d’outils pour basculer le style d’affichage parmi les grandes icônes, petites icônes, liste et modes de détail.

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Pour commencer à créer un exécutable MFC de style Explorateur de fichiers

1. Suivez les instructions de [création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Dans l’Assistant Application MFC [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page, sélectionnez le **Explorateur de fichiers** style de projet.

1. Définissez d’autres options de que votre choix sur les autres pages de l’Assistant.

1. Cliquez sur **Terminer** pour générer l’application squelette.

Pour plus d'informations, voir :

- [Types multidocuments, vues et fenêtres frame](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [Classes d’affichage dérivées](../../mfc/derived-view-classes-available-in-mfc.md)

- [Choix en matière de conception d’applications](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Création d’une application MFC de style navigateur web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[Création d’une application MFC basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md)
