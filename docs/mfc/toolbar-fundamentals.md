---
description: 'En savoir plus sur : notions de base de la barre d’outils'
title: Notions de base de barre d'outils
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: ed52c5878482f2ff0fa1c31a133fd2948d21a76e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264386"
---
# <a name="toolbar-fundamentals"></a>Notions de base de barre d'outils

Cet article décrit l’implémentation MFC fondamentale qui vous permet d’ajouter une barre d’outils par défaut à votre application en sélectionnant une option dans l’Assistant Application. Sont abordés les sujets suivants :

- [Option de la barre d’outils de l’Assistant Application](#_core_the_appwizard_toolbar_option)

- [La barre d’outils dans le code](#_core_the_toolbar_in_code)

- [Modification de la ressource de barre d’outils](#_core_editing_the_toolbar_resource)

- [Barres d’outils multiples](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a> Option de la barre d’outils de l’Assistant Application

Pour obtenir une barre d’outils unique avec les boutons par défaut, sélectionnez l’option standard d’ancrage de la barre d’outils dans la page fonctionnalités de l’interface utilisateur. Cela ajoute du code à votre application qui :

- Crée l’objet Toolbar.

- Gère la barre d’outils, y compris sa capacité à s’ancrer ou à flotter.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a> La barre d’outils dans le code

La barre d’outils est un objet [CToolBar](../mfc/reference/ctoolbar-class.md) déclaré en tant que membre de données de la classe de votre application `CMainFrame` . En d’autres termes, l’objet de barre d’outils est incorporé dans l’objet de fenêtre frame principal. Cela signifie que MFC crée la barre d’outils lorsqu’elle crée la fenêtre frame et détruit la barre d’outils lorsqu’elle détruit la fenêtre frame. La déclaration de classe partielle suivante, pour une application d’interface multidocument (MDI, multiple document interface), affiche les membres de données pour une barre d’outils incorporée et une barre d’État incorporée. Il montre également la substitution de la `OnCreate` fonction membre.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

La création d’une barre d’outils se produit dans `CMainFrame::OnCreate` . MFC appelle [OnCreate](../mfc/reference/cwnd-class.md#oncreate) après la création de la fenêtre pour le frame, mais avant qu’elle ne soit visible. La valeur par défaut `OnCreate` générée par l’Assistant application effectue les tâches suivantes dans la barre d’outils :

1. Appelle la `CToolBar` fonction membre [Create](../mfc/reference/ctoolbar-class.md#create) de l’objet pour créer l’objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) sous-jacent.

1. Appelle [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) pour charger les informations sur les ressources de la barre d’outils.

1. Appelle des fonctions pour activer l’ancrage, les flottants et les info-bulles. Pour plus d’informations sur ces appels, consultez l’article sur les [barres d’outils ancrées et flottantes](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
> L’exemple général MFC [DOCKTOOL](../overview/visual-cpp-samples.md) comprend des illustrations des anciennes et nouvelles barres d’outils MFC. Les barres d’outils qui utilisent `COldToolbar` requièrent des appels à l’étape 2 à `LoadBitmap` (plutôt que `LoadToolBar` ) et à `SetButtons` . Les nouvelles barres d’outils requièrent des appels à `LoadToolBar` .

Les appels d’ancrage, flottants et d’info-bulle sont facultatifs. Vous pouvez supprimer ces lignes de `OnCreate` si vous préférez. Le résultat est une barre d’outils qui reste fixe, qui ne peut pas flotter ou réancrer et ne peut pas afficher les info-bulles.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a> Modification de la ressource de barre d’outils

La barre d’outils par défaut que vous recevez avec l’Assistant application est basée sur une ressource personnalisée **RT_TOOLBAR** , introduite dans MFC version 4,0. Vous pouvez modifier cette ressource à l’aide de l' [éditeur de barres d’outils](../windows/toolbar-editor.md). L’éditeur vous permet d’ajouter, de supprimer et de réorganiser facilement des boutons. Il contient un éditeur graphique pour les boutons qui est très similaire à l’éditeur graphique général de Visual C++. Si vous avez modifié les barres d’outils dans les versions précédentes de Visual C++, vous trouverez la tâche beaucoup plus facile maintenant.

Pour connecter un bouton de barre d’outils à une commande, vous lui donnez un ID de commande, tel que `ID_MYCOMMAND` . Spécifiez l’ID de commande dans la page de propriétés du bouton dans l’éditeur de barres d’outils. Créez ensuite une fonction de gestionnaire pour la commande (consultez [mappage des messages aux fonctions](../mfc/reference/mapping-messages-to-functions.md) pour plus d’informations).

Les nouvelles fonctions membres [CToolBar](../mfc/reference/ctoolbar-class.md) fonctionnent avec la ressource **RT_TOOLBAR** . [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) prend maintenant la place de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) pour charger l’image bitmap des images de bouton de barre d’outils, et [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) pour définir les styles de bouton et les boutons de connexion avec des images bitmap.

Pour plus d’informations sur l’utilisation de l’éditeur de barres d’outils, consultez [éditeur de barres d’outils](../windows/toolbar-editor.md).

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a> Barres d’outils multiples

L’Assistant application vous fournit une barre d’outils par défaut. Si vous avez besoin de plusieurs barres d’outils dans votre application, vous pouvez modéliser votre code pour des barres d’outils supplémentaires basées sur le code généré par l’Assistant pour la barre d’outils par défaut.

Si vous souhaitez afficher une barre d’outils en tant que résultat d’une commande, vous devez :

- Créez une nouvelle ressource de barre d’outils avec l’éditeur de barres d’outils et chargez-la `OnCreate` avec la fonction membre [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) .

- Incorporez un nouvel objet [CToolBar](../mfc/reference/ctoolbar-class.md) dans la classe de fenêtre frame principale.

- Effectuez les appels de fonction appropriés dans `OnCreate` pour ancrer ou détacher la barre d’outils, définir ses styles, et ainsi de suite.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Implémentation de la barre d’outils MFC (informations générales sur les barres d’outils)](../mfc/mfc-toolbar-implementation.md)

- [Ancrer et rendre flottantes les barres d'outils](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- Classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Utilisation du contrôle de barre d'outils](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)
