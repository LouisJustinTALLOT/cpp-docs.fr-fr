---
title: "Procédure pas à pas : Placement de contrôles dans les barres d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f991f8ebf87535de09dc7c3dce5e0f4ca2ee457b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Procédure pas à pas : placement de contrôles dans les barres d'outils
Cette rubrique explique comment ajouter un bouton de barre d'outils qui contient un contrôle Windows. Dans les MFC, un bouton de barre d’outils doit être un [CMFCToolBarButton classe](../mfc/reference/cmfctoolbarbutton-class.md)-classe dérivée, par exemple [CMFCToolBarComboBoxButton classe](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton classe](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton classe](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), ou [CMFCToolBarMenuButton classe](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## <a name="adding-controls-to-toolbars"></a>Ajout de contrôles aux barres d'outils  
 Pour ajouter un contrôle à une barre d'outils, suivez ces étapes :  
  
1.  Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente. Pour plus d’informations sur la façon de créer des boutons à l’aide de l’éditeur de la barre d’outils dans Visual Studio, consultez le [barre d’outils Éditeur](../windows/toolbar-editor.md) rubrique.  
  
2.  Réservez une image de barre d'outils (icône bouton) pour le bouton dans toutes les images bitmap de la barre d'outils parente.  
  
3.  Dans le gestionnaire de messages qui gère le message `AFX_WM_RESETTOOLBAR`, procédez comme suit :  
  
    1.  Construisez le contrôle de bouton à l'aide d'une classe dérivée de `CMFCToolbarButton`.  
  
    2.  Remplacer le bouton factice avec le nouveau contrôle à l’aide de [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Vous pouvez construire l'objet bouton sur la pile, car `ReplaceButton` copie l'objet bouton et conserve la copie.  
  
> [!NOTE]
>  Si vous avez activé la personnalisation dans votre application, vous devrez peut-être réinitialiser la barre d’outils à l’aide de la **réinitialiser** bouton sur le **barres d’outils** onglet de la **personnaliser** boîte de dialogue pour afficher le contrôle mis à jour dans votre application après recompilation. L'état de la barre d'outils est stocké dans le Registre Windows, et les informations de Registre sont chargées et appliquées après que la méthode `ReplaceButton` se soit exécutée au démarrage de l'application.  
  
## <a name="toolbar-controls-and-customization"></a>Contrôles de barre d'outils et personnalisation  
 Le **commandes** onglet de la **personnaliser** boîte de dialogue contient une liste de commandes qui sont disponibles dans l’application. Par défaut, le **personnaliser** boîte de dialogue traite les menus d’application et génère la liste des boutons de barre d’outils standard dans chaque catégorie de menu. Pour conserver les fonctionnalités étendues fournies par les contrôles de barre d’outils, vous devez remplacer le bouton de barre d’outils standard par le contrôle personnalisé dans le **personnaliser** boîte de dialogue.  
  
 Lorsque vous activez la personnalisation, vous créez le **personnaliser** boîte de dialogue dans le Gestionnaire de personnalisation `OnViewCustomize` à l’aide de la [CMFCToolBarsCustomizeDialog classe](../mfc/reference/cmfctoolbarscustomizedialog-class.md) classe. Avant d’afficher le **personnaliser** boîte de dialogue en appelant [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), appelez [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) à remplacer le bouton standard avec le nouveau contrôle.  
  
## <a name="example-creating-a-find-combo-box"></a>Exemple : création d'une zone de liste déroulante Rechercher  
 Cette section décrit comment créer un contrôle de zone de liste déroulante `Find` qui apparaît dans une barre d'outils et contient les dernières chaînes utilisées. L'utilisateur peut entrer une chaîne du contrôle puis appuyer sur la touche d'entrée pour rechercher un document, ou appuyer sur la touche Échap pour retourner le focus au frame principal. Cet exemple suppose que le document s’affiche dans un [classe CEditView](../mfc/reference/ceditview-class.md)-dérivée de vue.  
  
### <a name="creating-the-find-control"></a>Création du contrôle de recherche (Find)  
 En premier lieu, créez le contrôle de la zone de liste déroulante `Find` :  
  
1.  Ajoutez le bouton et ses commandes aux ressources d'application :  
  
    1.  Dans les ressources d'application, ajoutez un nouveau bouton avec un ID de commande `ID_EDIT_FIND` à une barre d'outils de votre application et à toutes les images bitmap associées à la barre d'outils.  
  
    2.  Créez un élément de menu avec l'ID de commande ID_EDIT_FIND.  
  
    3.  Ajoutez une nouvelle chaîne "Find the text\nFind" à la table de chaînes et assignez-lui un ID de commande `ID_EDIT_FIND_COMBO`. Cet ID sera utilisé comme ID de commande du bouton de zone de liste déroulante `Find`.  
  
        > [!NOTE]
        >  Comme `ID_EDIT_FIND` est une commande standard traitée par `CEditView`, vous n'êtes pas tenu d'implémenter un gestionnaire spécial pour cette commande.  Toutefois, vous devez implémenter un gestionnaire pour la nouvelle commande `ID_EDIT_FIND_COMBO`.  
  
2.  Créer une nouvelle classe, `CFindComboBox`, dérivée de [CComboBox (classe)](../mfc/reference/ccombobox-class.md).  
  
3.  Dans la classe `CFindComboBox`, substituez la méthode virtuelle `PreTranslateMessage`. Cette méthode active la zone de liste déroulante traiter les [WM_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) message. Si l'utilisateur appuie sur la touche Échap (`VK_ESCAPE`), retournez le focus sur la fenêtre frame principale. Si l'utilisateur appuie sur la touche Entrée (`VK_ENTER`), publiez dans la fenêtre frame principale un message `WM_COMMAND` contenant l'ID de commande `ID_EDIT_FIND_COMBO`.  
  
4.  Créez une classe pour le `Find` bouton de zone de liste modifiable, dérivé [CMFCToolBarComboBoxButton classe](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). Dans cet exemple, cela est nommé `CFindComboButton`.  
  
5.  Le constructeur de `CMFCToolbarComboBoxButton` prend trois paramètres : l'ID de commande du bouton, l'index d'image du bouton et le style de la zone de liste déroulante. Définissez ces paramètres comme suit :  
  
    1.  Passez `ID_EDIT_FIND_COMBO` en tant qu'ID de commande.  
  
    2.  Utilisez [CCommandManager::GetCmdImage](http://msdn.microsoft.com/en-us/4094d08e-de74-4398-a483-76d27a742dca) avec `ID_EDIT_FIND` pour obtenir l’index de l’image.  
  
    3.  Pour obtenir la liste des styles de zone de liste déroulante disponible, consultez [Styles de zone de liste déroulante](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
6.  Dans la classe `CFindComboButton`, remplacez la méthode `CMFCToolbarComboBoxButton::CreateCombo`. Maintenant, vous devez créer l'objet `CFindComboButton` et retourner un pointeur vers lui.  
  
7.  Utilisez le [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) macro pour rendre le bouton de liste déroulante persistant. Le gestionnaire de l'espace de travail charge et stocke automatiquement l'état du bouton dans le Registre Windows.  
  
8.  Implémentez le gestionnaire `ID_EDIT_FIND_COMBO` dans l'affichage de votre document. Utilisez [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) avec `ID_EDIT_FIND_COMBO` pour récupérer tous les `Find` boutons de zone de liste déroulante. Il peut exister plusieurs copies d'un bouton avec le même ID de commande suite à la personnalisation.  
  
9. Dans le Gestionnaire de messages ID_EDIT_FIND `OnFind`, utilisez [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) pour déterminer si la commande find a été envoyée à partir de la `Find` bouton de zone de liste déroulante. Si oui, recherchez le texte et ajoutez la chaîne recherchée dans la zone de liste déroulante.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>Ajout du contrôle de recherche (Find) dans la barre d'outils principale  
 Pour ajouter le bouton de zone de liste déroulante à la barre d'outils, suivez ces étapes :  
  
1.  Implémentez le gestionnaire de messages `AFX_WM_RESETTOOLBAR` `OnToolbarReset` dans la fenêtre frame principale.  
  
    > [!NOTE]
    >  Le framework envoie le message à la fenêtre frame principale lorsqu'une barre d'outils est initialisée pendant le démarrage de l'application, ou lorsqu'une barre d'outils est réinitialisée pendant la personnalisation. Dans les deux cas, vous devez remplacer le bouton de barre d'outils standard par le bouton de zone de liste déroulante `Find` personnalisé.  
  
2.  Dans le gestionnaire `AFX_WM_RESETTOOLBAR`, examinez l'ID de barre d'outils, autrement dit, `WPARAM` du message `AFX_WM_RESETTOOLBAR`. Si l’ID de la barre d’outils est égale à celle de la barre d’outils qui contient le `Find` bouton de zone de liste déroulante, appelez [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) pour remplacer le `Find` bouton (autrement dit, le bouton avec l’ID de commande `ID_EDIT_FIND)` avec un `CFindComboButton` objet.  
  
    > [!NOTE]
    >  Vous pouvez construire un objet `CFindComboBox` sur la pile, car `ReplaceButton` copie le bouton et conserve la copie.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Ajout du contrôle de recherche (Find) dans la boîte de dialogue Personnaliser  
 Dans le Gestionnaire de personnalisation `OnViewCustomize`, appelez [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) pour remplacer le `Find` bouton (autrement dit, le bouton avec l’ID de commande `ID_EDIT_FIND)` avec un `CFindComboButton` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../mfc/hierarchy-chart.md)   
 [Classes](../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolBar](../mfc/reference/cmfctoolbar-class.md)   
 [Classe de CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)   
 [Classe de CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog, classe](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
