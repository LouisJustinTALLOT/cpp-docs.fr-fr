---
description: 'En savoir plus sur : création d’un fichier Explorer-Style application MFC'
title: Création d'une application MFC de style Explorateur de fichiers
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 9419aae58cf34ec70585b952360cb12702424381
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301319"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Création d'une application MFC de style Explorateur de fichiers

De nombreuses applications système Windows utilisent l’interface utilisateur (IU) pour l’Explorateur de fichiers. Lorsque vous démarrez l’Explorateur de fichiers, par exemple, vous voyez une application avec une barre de fractionnement verticale qui divise la zone cliente. Le côté gauche de la zone cliente fournit des fonctionnalités de navigation et de navigation, et le côté droit de la zone cliente affiche des détails relatifs à la sélection dans le volet gauche. Quand un utilisateur clique sur un élément dans le volet gauche, l’application remplit à nouveau le volet droit. Dans une application MDI, vous pouvez utiliser les commandes du menu **affichage** pour modifier la quantité de détails affichée dans le volet droit. (Dans une application de document SDI ou à plusieurs niveaux de niveau supérieur, vous pouvez modifier les détails à l’aide des boutons de la barre d’outils uniquement.)

Le contenu des volets dépend de l’application. Dans un navigateur de système de fichiers, le volet gauche affiche une vue hiérarchique des répertoires ou des ordinateurs, ou des groupes d’ordinateurs, tandis que le volet droit affiche des dossiers, des fichiers individuels ou des ordinateurs, ainsi que des détails les concernant. Le contenu ne doit pas nécessairement être un fichier. Il peut s’agir de messages électroniques, de rapports d’erreurs ou d’autres éléments d’une base de données.

L’Assistant crée les classes suivantes pour vous :

- La `CLeftView` classe définit le volet gauche de la zone cliente. Elle est toujours dérivée de [CTreeView](../../mfc/reference/ctreeview-class.md).

- La classe C *ProjName* View définit le volet droit de la zone cliente. Par défaut, il est dérivé de [CListView](../../mfc/reference/clistview-class.md) , mais il peut s’agir d’un autre type de vue en fonction de la classe que vous spécifiez dans la liste **classe de base** de la page [classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) de l’Assistant.

L’application générée peut avoir une interface SDI (single document interface), une interface multidocument (MDI, multiple document interface) ou plusieurs documents de niveau supérieur. Chaque fenêtre frame créée par l’application est divisée verticalement à l’aide de [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Le codage de ce type d’application est semblable au codage d’une application MFC normale qui utilise un séparateur, sauf que ce type d’application a des vues de contrôle distinctes dans chaque volet fractionné.

Si vous utilisez l’affichage de liste par défaut dans le volet droit, l’Assistant crée des options de menu supplémentaires (dans les applications MDI uniquement) et des boutons de barre d’outils pour faire basculer le style de la vue parmi les grandes icônes, les petites icônes, les listes et les modes de détails.

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Pour commencer à créer un exécutable MFC de style Explorateur de fichiers

1. Suivez les instructions de [création d’une application MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Dans la page type d' [application](../../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant Application MFC, sélectionnez le style de projet **Explorateur de fichiers** .

1. Définissez les autres options souhaitées sur les autres pages de l’Assistant.

1. Cliquez sur **Terminer** pour générer l’application squelette.

Pour plus d'informations, consultez les pages suivantes :

- [Plusieurs types de documents, vues et fenêtres Frame](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [Classes d’affichage dérivées](../../mfc/derived-view-classes-available-in-mfc.md)

- [Choix de conception d’application](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Création d’une application Web Browser-Style MFC](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[Création d’une application Forms-Based MFC](../../mfc/reference/creating-a-forms-based-mfc-application.md)
