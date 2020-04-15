---
title: "Procédure pas à pas : utilisation des nouveaux contrôles d'environnement MFC"
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360212"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Procédure pas à pas : utilisation des nouveaux contrôles d'environnement MFC

Dans cette procédure pas à pas, vous allez créer une application qui ressemble à File Explorer. Vous allez créer une fenêtre qui a deux vitres. Le volet gauche tiendra un objet [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) qui affiche votre bureau dans une vue hiérarchique. Le volet droit tiendra un [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) qui affiche les fichiers dans le dossier qui est sélectionné dans la vitre gauche.

## <a name="prerequisites"></a>Prérequis

- Dans Visual Studio 2017 et plus tard, le support MFC est un composant optionnel. Pour l’installer, ouvrez l’installateur Visual Studio à partir du menu Windows Start. Trouvez la version de Visual Studio que vous utilisez et choisissez le bouton **Modifier.** Assurez-vous que le développement de bureau avec la tuile **CMD** est vérifié. Sous **les composants facultatifs,** vérifiez le bouton **de support MFC.**

- Ce pas-là suppose que vous avez mis en place Visual Studio pour utiliser **General Development Settings**. Si vous utilisez un paramètre de développement différent, certaines fenêtres Visual Studio que nous utilisons dans cette procédure pas à pas peuvent ne pas être affichées par défaut.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Créer une nouvelle application MFC en utilisant le MFC Application Wizard

Ces étapes varient selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Créer un projet MFC dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. Dans la zone de recherche en haut, tapez **MFC** et choisissez ensuite **L’application MFC** dans la liste des résultats.

1. Cliquez sur **Suivant**. Dans la page suivante, entrez un nom pour le projet et spécifiez l’emplacement du projet si désiré.

1. Choisissez le bouton **Créer** pour créer le projet.

   Après **l’affichage de MFC Application Wizard,** utilisez les options suivantes :

   1. Choisissez **le type d’application** sur la gauche. Sélectionnez ensuite **un document unique** et sélectionnez le support **d’architecture Document/View**. Sous **le style Projet**, sélectionnez Visual **Studio**, et à partir du style visuel et les **couleurs** déposer liste de sélection **Office 2007 (thème bleu)**.

   1. Sur la vitre **de support de document composé,** sélectionnez **Aucun**.

   1. N’effectuez aucune modification à la vitre **de Documents Template Properties.**

   1. Sur la vitre **des fonctionnalités d’interface utilisateur,** **assurez-vous que l’option Utiliser une barre de menu et une barre d’outils** est sélectionnée. Laissez toutes les autres options telles qu’elles sont.

   1. Sur le volet **Advanced Features,** sélectionnez **les commandes ActiveX,** **le manifeste de contrôle commun**et **l’option de panoramique de navigation.** Laissez tout le reste tel qu’il est. **L’option Navigation Pane** amènera l’assistant à créer la `CMFCShellTreeCtrl` vitre à gauche de la fenêtre avec un déjà intégré.

   1. Nous n’allons pas apporter de modifications à la vitre **des classes générées,** alors cliquez sur **Finition** pour créer votre nouveau projet MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Créer un projet MFC en Visual Studio 2017 ou plus tôt

1. Utilisez **l’assistant d’application MFC** pour créer une nouvelle application MFC. Pour exécuter l’assistant, à partir du menu **Fichier** sélectionnez **Nouveau**, puis sélectionnez **Projet**. La boîte de dialogue **du nouveau projet** sera affichée.

1. Dans la boîte de dialogue **du nouveau projet,** étendre le nœud **Visual CMD** dans le volet **des types de projets** et sélectionnez **MFC**. Ensuite, dans le volet **Templates,** sélectionnez **L’application MFC**. Tapez un nom pour `MFCShellControls` le projet, comme et cliquez **sur OK**.

   Après **l’affichage de MFC Application Wizard,** utilisez les options suivantes :

   1. Sur le volet **type d’application,** sous **type d’application,** effacez **l’option des documents Tabbed.** Ensuite, sélectionnez **un document unique** et sélectionnez le support **d’architecture Document/View**. Sous **le style Projet**, sélectionnez Visual **Studio**, et à partir du style visuel et les **couleurs** déposer liste de sélection **Office 2007 (thème bleu)**.

   1. Sur la vitre **de support de document composé,** sélectionnez **Aucun**.

   1. N’effectuez aucune modification à la vitre **des chaînes de modèles de documents.**

   1. Sur le volet **de support de base de données** (Visual Studio 2015 et plus), sélectionnez **Aucun** parce que l’application n’utilise pas de base de données.

   1. Sur la vitre **des fonctionnalités d’interface utilisateur,** **assurez-vous que l’option Utiliser une barre de menu et une barre d’outils** est sélectionnée. Laissez toutes les autres options telles qu’elles sont.

   1. Sur le volet **Advanced Features,** sous **les fonctionnalités avancées,** sélectionnez uniquement **les commandes ActiveX** et **le manifeste de contrôle commun.** Sous **les volets de cadre avancés,** sélectionnez seulement l’option **de panoramique de navigation.** Il fera en sorte que le magicien créera la `CMFCShellTreeCtrl` vitre à gauche de la fenêtre avec un déjà intégré.

   1. Nous n’allons pas apporter de modifications à la vitre **des classes générées,** alors cliquez sur **Finition** pour créer votre nouveau projet MFC.

::: moniker-end

Vérifiez que l’application a été créée avec succès en la construisant et en l’exécutant. Pour construire l’application, à partir du menu **Build** select **Build Solution**. Si l’application se construit avec succès, exécutez l’application en sélectionnant **Start Debugging** dans le menu **Debug.**

L’assistant crée automatiquement une application qui dispose d’une barre de menu standard, d’une barre d’outils standard, d’une barre d’état standard et d’une barre Outlook à gauche de la fenêtre avec une vue **de dossiers** et une vue **de calendrier.**

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Pour ajouter le contrôle de la liste de coquilles à la vue de document

1. Dans cette section, vous ajouterez `CMFCShellListCtrl` un exemple de la vue que l’assistant a créée. Ouvrez le fichier d’en-tête de vue en cliquant en double **MFCShellControlsView.h** dans la **solution Explorer**.

   Localiser `#pragma once` la directive près du haut du fichier d’en-tête. Immédiatement en dessous, ajouter ce code `CMFCShellListCtrl`pour inclure le fichier d’en-tête pour :

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Maintenant, ajoutez une `CMFCShellListCtrl`variable de membre de type . Tout d’abord, localiser le commentaire suivant dans le fichier d’en-tête:

   ```cpp
   // Generated message map functions
   ```

   Immédiatement au-dessus de ce commentaire, ajoutez ce code:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. Le **MFC Application** Wizard `CMFCShellTreeCtrl` a `CMainFrame` déjà créé un objet dans la classe, mais c’est un membre protégé. Nous accéderons à l’objet plus tard, alors créez un accesseur pour cela maintenant. Ouvrez le fichier d’en-tête MainFrm.h en le cliquant en double dans la **Solution Explorer**. Localiser le commentaire suivant :

   ```cpp
   // Attributes
   ```

   Immédiatement sous elle, ajoutez la déclaration de méthode suivante :

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Ensuite, ouvrez le fichier source MainFrm.cpp en le cliquant en double dans la **Solution Explorer**. Au bas de ce fichier, ajoutez la définition de méthode suivante :

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Maintenant, nous `CMFCShellControlsView` mettons à `WM_CREATE` jour la classe pour gérer le message Windows. Ouvrez la fenêtre Class `CMFCShellControlsView` **View** et sélectionnez la classe. Effectuez un clic droit et sélectionnez **Propriétés**.

   Ensuite, dans [la classe Wizard](reference/mfc-class-wizard.md), cliquez sur l’onglet **Messages.** Faites défiler vers le bas jusqu’à ce que vous trouviez le `WM_CREATE` message. De la liste d’abandon à `WM_CREATE`côté de , sélectionnez ** \<Ajouter> OnCreate**. La commande crée un gestionnaire de message pour nous et met à jour automatiquement la carte de message MFC.

   Dans `OnCreate` la méthode, nous allons `CMFCShellListCtrl` maintenant créer notre objet. Trouvez `OnCreate` la définition de la méthode dans le fichier source MFCShellControlsView.cpp et remplacez sa mise en œuvre par le code suivant :

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. Répétez l’étape `WM_SIZE` précédente, mais pour le message. Il entraînera la redessin de votre vue d’applications chaque fois qu’un utilisateur change la taille de la fenêtre d’application. Remplacer la définition `OnSize` de la méthode par le code suivant :

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. La dernière étape consiste `CMFCShellTreeCtrl` `CMFCShellListCtrl` à connecter les objets et les objets en utilisant la méthode [CMFCShellTreeCtrl::SetRelatedList.](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) Après votre `CMFCShellTreeCtrl::SetRelatedList`appel, le `CMFCShellListCtrl` sera automatiquement afficher le `CMFCShellTreeCtrl`contenu de l’élément sélectionné dans le . Nous connectons les `OnActivateView` objets dans la méthode, qui est annulée à partir de [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   Dans le fichier d’en-tête MFCShellControlsView.h, à l’intérieur de la `CMFCShellControlsView` déclaration de classe, ajoutez la déclaration de méthode suivante :

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Ensuite, ajoutez la définition de la méthode au fichier MFCShellControlsView.cpp source:

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   Parce que nous appelons `CMainFrame` les méthodes de `#include` la classe, nous devons ajouter une directive en haut du fichier MFCShellControlsView.cpp source:

    ```cpp
    #include "MainFrm.h"
    ```

1. Vérifiez que l’application a été créée avec succès en la construisant et en l’exécutant. Pour construire l’application, à partir du menu **Build** select **Build Solution**. Si l’application se construit avec succès, exécutez-la en sélectionnant **Start Debugging** à partir du menu **Debug.**

   Vous devez maintenant voir les détails `CMFCShellTreeCtrl` de l’élément sélectionné dans le volet de vue. Lorsque vous cliquez sur `CMFCShellTreeCtrl`un `CMFCShellListCtrl` nœud dans le , le sera automatiquement mis à jour. De même, si vous doublez `CMFCShellListCtrl`un `CMFCShellTreeCtrl` dossier dans le , le doit être automatiquement mis à jour.

   Cliquez à droite sur n’importe quel élément dans le contrôle de l’arbre ou dans le contrôle de liste. Vous obtenez le même menu de contexte que si vous utilisiez le vrai **File Explorer**.

## <a name="next-steps"></a>Étapes suivantes

- L’assistant a créé une barre Outlook avec à la fois une vitre **Folders** et une vitre **Calendrier.** Il n’a probablement pas de sens d’avoir une vitre **Calendrier** dans une fenêtre **Explorer,** alors retirez cette vitre maintenant.

- Les `CMFCShellListCtrl` fichiers de visualisation prend en charge dans différents modes, tels que **Les grandes icônes**, **les petites icônes**, **la liste**, et **les détails**. Mettez à jour votre application pour implémenter cette fonctionnalité. Astuce: voir [VisualCM Échantillons](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)
