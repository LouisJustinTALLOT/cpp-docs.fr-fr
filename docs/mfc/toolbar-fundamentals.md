---
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
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373479"
---
# <a name="toolbar-fundamentals"></a>Notions de base de barre d'outils

Cet article décrit la implémentation MFC fondamentale qui vous permet d’ajouter une barre d’outils par défaut à votre application en sélectionnant une option dans l’Assistant d’Application. Sont abordés les sujets suivants :

- [L’option barre d’outils Application Wizard](#_core_the_appwizard_toolbar_option)

- [La barre d’outils dans le code](#_core_the_toolbar_in_code)

- [Modifier la ressource de la barre d’outils](#_core_editing_the_toolbar_resource)

- [Plusieurs barres d’outils](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>L’option Toolbar d’assistant d’application

Pour obtenir une seule barre d’outils avec des boutons par défaut, sélectionnez l’option barre d’outils Standard Docking sur la page étiquetée User Interface Features. Cela ajoute du code à votre application qui :

- Crée l’objet de barre d’outils.

- Gère la barre d’outils, y compris sa capacité à accoster ou à flotter.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>La barre d’outils en code

La barre d’outils est un objet [CToolBar](../mfc/reference/ctoolbar-class.md) déclaré `CMainFrame` membre des données de la classe de votre application. En d’autres termes, l’objet de la barre d’outils est intégré dans l’objet de fenêtre de cadre principal. Cela signifie que MFC crée la barre d’outils quand il crée la fenêtre de cadre et détruit la barre d’outils quand il détruit la fenêtre de cadre. La déclaration partielle suivante de classe, pour une application d’interface documentaire multiple (MDI), montre les membres de données pour une barre d’outils intégrée et une barre d’état intégrée. Il montre également la `OnCreate` dérogation de la fonction membre.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

La création de `CMainFrame::OnCreate`barres d’outils se produit dans . MFC appelle [OnCreate](../mfc/reference/cwnd-class.md#oncreate) après avoir créé la fenêtre pour le cadre, mais avant qu’il ne devienne visible. La `OnCreate` valeur par défaut générée par l’Assistant d’Application effectue les tâches suivantes de barre d’outils :

1. Appelle `CToolBar` la fonction membre [Créer](../mfc/reference/ctoolbar-class.md#create) de l’objet pour créer l’objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) sous-jacent.

1. Appelle [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) pour charger les informations sur les ressources de la barre d’outils.

1. Appels fonctions pour permettre l’amarrage, flottant, et conseils d’outil. Pour plus de détails sur ces appels, voir l’article [Docking and Floating Toolbars](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
> L’échantillon général de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) comprend des illustrations de barres d’outils MFC anciennes et nouvelles. Les barres d’outils qui `COldToolbar` utilisent nécessitent `LoadBitmap` des `LoadToolBar`appels à l’étape 2 à (plutôt que ) et à `SetButtons`. Les nouvelles barres d’outils nécessitent des appels à `LoadToolBar`.

Les appels à l’amarrage, flottant et aux conseils d’outils sont facultatifs. Vous pouvez supprimer `OnCreate` ces lignes si vous préférez. Le résultat est une barre d’outils qui reste fixe, incapable de flotter ou redock et incapable d’afficher des conseils d’outils.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>Modifier la ressource Toolbar

La barre d’outils par défaut que vous obtenez avec l’Assistant d’Application est basée sur une ressource personnalisée **RT_TOOLBAR,** introduite dans la version MFC 4.0. Vous pouvez modifier cette ressource avec l’éditeur de la [barre d’outils](../windows/toolbar-editor.md). L’éditeur vous permet d’ajouter, de supprimer et de réorganiser facilement les boutons. Il contient un éditeur graphique pour les boutons qui est très similaire à l’éditeur graphique général dans Visual C . Si vous avez édité des barres d’outils dans les versions précédentes de Visual CMD, vous trouverez la tâche beaucoup plus facile dès maintenant.

Pour connecter un bouton de barre d’outils à une `ID_MYCOMMAND`commande, vous donnez au bouton un IDENTIFIANT de commande, tel que . Spécifiez l’ID de commande dans la page de propriété du bouton dans l’éditeur de la barre d’outils. Ensuite, créez une fonction de gestionnaire pour la commande (voir [Messages de cartographie aux fonctions](../mfc/reference/mapping-messages-to-functions.md) pour plus d’informations).

Les nouvelles fonctions des membres [de CToolBar](../mfc/reference/ctoolbar-class.md) fonctionnent avec la ressource **RT_TOOLBAR.** [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) prend maintenant la place de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) pour charger la bitmap des images bouton de barre d’outils, et [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) pour définir les styles de bouton et de connecter les boutons avec des images bitmap.

Pour plus de détails sur l’utilisation de l’éditeur de la barre d’outils, voir [Toolbar Editor](../windows/toolbar-editor.md).

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>Barres d’outils multiples

L’Assistant d’Application vous fournit une barre d’outils par défaut. Si vous avez besoin de plus d’une barre d’outils dans votre application, vous pouvez modéliser votre code pour des barres d’outils supplémentaires en fonction du code généré par l’assistant pour la barre d’outils par défaut.

Si vous souhaitez afficher une barre d’outils à la suite d’une commande, vous devrez :

- Créez une nouvelle ressource de barre d’outils `OnCreate` avec l’éditeur de la barre d’outils et chargez-la avec la fonction membre [LoadToolbar.](../mfc/reference/ctoolbar-class.md#loadtoolbar)

- Intégrer un nouvel objet [CToolBar](../mfc/reference/ctoolbar-class.md) dans votre classe de fenêtre de cadre principale.

- Faites les appels `OnCreate` de fonction appropriés pour amarrer ou flotter la barre d’outils, définir ses styles, et ainsi de suite.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Mise en œuvre de la barre d’outils MFC (informations d’aperçu sur les barres d’outils)](../mfc/mfc-toolbar-implementation.md)

- [Docking et barres d’outils flottantes](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- Les classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Utilisation du contrôle de barre d'outils](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'outils MFC](../mfc/mfc-toolbar-implementation.md)
