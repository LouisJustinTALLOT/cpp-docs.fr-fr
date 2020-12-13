---
description: 'En savoir plus sur : procédure pas à pas : ajout de contrôles aux barres d’outils'
title: "Procédure pas à pas : placement de contrôles dans les barres d'outils"
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: eafb1afa2ffffeaaabfc6b463e2951d8d532db58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143050"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Procédure pas à pas : placement de contrôles dans les barres d'outils

Cet article explique comment ajouter un bouton de barre d’outils qui contient un contrôle Windows à une barre d’outils. Dans MFC, un bouton de barre d’outils doit être une classe [CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)dérivée de classe, par exemple classe [CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), classe [CMFCToolBarEditBoxButton](../mfc/reference/cmfctoolbareditboxbutton-class.md), [classe CMFCDropDownToolbarButton](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)ou [classe CMFCToolBarMenuButton](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Ajout de contrôles aux barres d'outils

Pour ajouter un contrôle à une barre d'outils, suivez ces étapes :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente. Pour plus d’informations sur la création de boutons à l’aide de l' **éditeur de barres d’outils** dans Visual Studio, consultez l’article [éditeur de barres d’outils](../windows/toolbar-editor.md) .

1. Réservez une image de barre d'outils (icône bouton) pour le bouton dans toutes les images bitmap de la barre d'outils parente.

1. Dans le gestionnaire de messages qui traite le `AFX_WM_RESETTOOLBAR` message, procédez comme suit :

   1. Construisez le contrôle de bouton à l'aide d'une classe dérivée de `CMFCToolbarButton`.

   1. Remplacez le bouton factice par le nouveau contrôle à l’aide de [CMFCToolBar :: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Vous pouvez construire l'objet bouton sur la pile, car `ReplaceButton` copie l'objet bouton et conserve la copie.

> [!NOTE]
> Si vous avez activé la personnalisation dans votre application, vous devrez peut-être réinitialiser la barre d’outils en utilisant le bouton **Réinitialiser** sous l’onglet **barres d’outils** de la boîte de dialogue **personnaliser** pour voir le contrôle mis à jour dans votre application après la recompilation. L'état de la barre d'outils est stocké dans le Registre Windows, et les informations de Registre sont chargées et appliquées après que la méthode `ReplaceButton` se soit exécutée au démarrage de l'application.

## <a name="toolbar-controls-and-customization"></a>Contrôles de barre d'outils et personnalisation

L’onglet **commandes** de la boîte de dialogue **personnaliser** contient la liste des commandes disponibles dans l’application. Par défaut, la boîte de dialogue **personnaliser** traite les menus de l’application et génère une liste de boutons de barre d’outils standard dans chaque catégorie de menu. Pour conserver les fonctionnalités étendues fournies par les contrôles ToolBar, vous devez remplacer le bouton de barre d’outils standard par le contrôle personnalisé dans la boîte de dialogue **personnaliser** .

Lorsque vous activez la personnalisation, vous créez la boîte de dialogue **personnaliser** dans le gestionnaire de personnalisation à `OnViewCustomize` l’aide de la classe de [classe CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md) . Avant d’afficher la boîte de dialogue **personnaliser** en appelant [CMFCToolBarsCustomizeDialog :: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), appelez [CMFCToolBarsCustomizeDialog :: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) pour remplacer le bouton standard par le nouveau contrôle.

## <a name="example-creating-a-find-combo-box"></a>Exemple : création d'une zone de liste déroulante Rechercher

Cette section décrit comment créer un contrôle de zone de liste déroulante de **recherche** qui apparaît dans une barre d’outils et contient des chaînes de recherche utilisées récemment. L'utilisateur peut entrer une chaîne du contrôle puis appuyer sur la touche d'entrée pour rechercher un document, ou appuyer sur la touche Échap pour retourner le focus au frame principal. Cet exemple suppose que le document est affiché dans une vue dérivée de la [classe CEditView](../mfc/reference/ceditview-class.md).

### <a name="creating-the-find-control"></a>Création du contrôle de recherche (Find)

Tout d’abord, créez le contrôle de zone de liste déroulante **Rechercher** :

1. Ajoutez le bouton et ses commandes aux ressources d'application :

   1. Dans les ressources d'application, ajoutez un nouveau bouton avec un ID de commande `ID_EDIT_FIND` à une barre d'outils de votre application et à toutes les images bitmap associées à la barre d'outils.

   1. Créez un nouvel élément de menu avec l' `ID_EDIT_FIND` ID de commande.

   1. Ajoutez une nouvelle chaîne "Find the text\nFind" à la table de chaînes et assignez-lui un ID de commande `ID_EDIT_FIND_COMBO`. Cet ID sera utilisé comme ID de commande du bouton **Rechercher** une zone de liste déroulante.

        > [!NOTE]
        > Comme `ID_EDIT_FIND` est une commande standard traitée par `CEditView`, vous n'êtes pas tenu d'implémenter un gestionnaire spécial pour cette commande.  Toutefois, vous devez implémenter un gestionnaire pour la nouvelle commande `ID_EDIT_FIND_COMBO`.

1. Créez une classe, `CFindComboBox` , dérivée de la [classe CComboBox](../mfc/reference/ccombobox-class.md).

1. Dans la classe `CFindComboBox`, substituez la méthode virtuelle `PreTranslateMessage`. Cette méthode permet à la zone de liste déroulante de traiter le message de [WM_KEYDOWN](/windows/win32/inputdev/wm-keydown) . Si l'utilisateur appuie sur la touche Échap (`VK_ESCAPE`), retournez le focus sur la fenêtre frame principale. Si l'utilisateur appuie sur la touche Entrée (`VK_ENTER`), publiez dans la fenêtre frame principale un message `WM_COMMAND` contenant l'ID de commande `ID_EDIT_FIND_COMBO`.

1. Créez une classe pour le bouton de zone de liste déroulante **Rechercher** , dérivé de la [classe CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). Dans cet exemple, il est nommé `CFindComboButton`.

1. Le constructeur de `CMFCToolbarComboBoxButton` prend trois paramètres : l'ID de commande du bouton, l'index d'image du bouton et le style de la zone de liste déroulante. Définissez ces paramètres comme suit :

   1. Passez `ID_EDIT_FIND_COMBO` en tant qu'ID de commande.

   1. Utilisez [CCommandManager :: GetCmdImage](reference/internal-classes.md) avec `ID_EDIT_FIND` pour récupérer l’index d’image.

   1. Pour obtenir la liste des styles de zone de liste déroulante disponibles, consultez styles de zone de liste [déroulante](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. Dans la classe `CFindComboButton`, remplacez la méthode `CMFCToolbarComboBoxButton::CreateCombo`. Maintenant, vous devez créer l'objet `CFindComboButton` et retourner un pointeur vers lui.

1. Utilisez la macro [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) pour rendre persistant le bouton de liste déroulante. Le gestionnaire de l'espace de travail charge et stocke automatiquement l'état du bouton dans le Registre Windows.

1. Implémentez le gestionnaire `ID_EDIT_FIND_COMBO` dans l'affichage de votre document. Utilisez [CMFCToolBar :: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) avec `ID_EDIT_FIND_COMBO` pour récupérer tous les boutons de zone de liste déroulante de **recherche** . Il peut exister plusieurs copies d'un bouton avec le même ID de commande suite à la personnalisation.

1. Dans le `ID_EDIT_FIND` Gestionnaire de messages `OnFind` , utilisez [CMFCToolBar :: IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) pour déterminer si la commande de recherche a été envoyée à partir du bouton de la zone de liste déroulante **Rechercher** . Si oui, recherchez le texte et ajoutez la chaîne recherchée dans la zone de liste déroulante.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Ajout du contrôle de recherche (Find) dans la barre d'outils principale

Pour ajouter le bouton de zone de liste déroulante à la barre d'outils, suivez ces étapes :

1. Implémentez le gestionnaire de messages `AFX_WM_RESETTOOLBAR``OnToolbarReset` dans la fenêtre frame principale.

    > [!NOTE]
    > Le framework envoie le message à la fenêtre frame principale lorsqu'une barre d'outils est initialisée pendant le démarrage de l'application, ou lorsqu'une barre d'outils est réinitialisée pendant la personnalisation. Dans les deux cas, vous devez remplacer le bouton de barre d’outils standard par le bouton de zone de liste modifiable **recherche** personnalisée.

1. Dans le `AFX_WM_RESETTOOLBAR` Gestionnaire, examinez l’ID de la barre d’outils, autrement dit, le *wParam* du message AFX_WM_RESETTOOLBAR. Si l’ID de barre d’outils est égal à celui de la barre d’outils qui contient le bouton **Rechercher** une zone de liste déroulante, appelez [CMFCToolBar :: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) pour remplacer le bouton **Rechercher** (autrement dit, le bouton avec l’ID de commande `ID_EDIT_FIND)` avec un `CFindComboButton` objet.

    > [!NOTE]
    > Vous pouvez construire un objet `CFindComboBox` sur la pile, car `ReplaceButton` copie le bouton et conserve la copie.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Ajout du contrôle de recherche (Find) dans la boîte de dialogue Personnaliser

Dans le gestionnaire de personnalisation `OnViewCustomize` , appelez [CMFCToolBarsCustomizeDialog :: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) pour remplacer le bouton **Rechercher** (c’est-À-dire le bouton par l’ID de commande `ID_EDIT_FIND` ) par un `CFindComboButton` objet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../mfc/hierarchy-chart.md)<br/>
[Classes](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog, classe](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
