---
title: "Procédure pas à pas : utilisation des nouveaux contrôles d'environnement MFC"
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 0d8db9044a64305bd7bb9ef6fe10de9ecef1ce51
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924752"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Procédure pas à pas : utilisation des nouveaux contrôles d'environnement MFC

Dans cette procédure pas à pas, vous allez créer une application qui ressemble à l’Explorateur de fichiers. Vous allez créer une fenêtre qui comporte deux volets. Le volet gauche contiendra un objet [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) qui affiche votre bureau dans une vue hiérarchique. Le volet droit contiendra un [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) qui affiche les fichiers dans le dossier sélectionné dans le volet gauche.

## <a name="prerequisites"></a>Conditions préalables requises

- Dans Visual Studio 2017 et versions ultérieures, la prise en charge de MFC est un composant facultatif. Pour l’installer, ouvrez le Visual Studio Installer à partir du menu Démarrer de Windows. Recherchez la version de Visual Studio que vous utilisez et choisissez le bouton **modifier** . Assurez-vous que la vignette **développement Desktop avec C++** est cochée. Sous **composants facultatifs** , activez le bouton **prise en charge MFC** .

- Cette procédure pas à pas suppose que vous avez configuré Visual Studio pour utiliser les **paramètres de développement généraux** . Si vous utilisez un autre paramètre de développement, certaines fenêtres Visual Studio que nous utilisons dans cette procédure pas à pas peuvent ne pas être affichées par défaut.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Pour créer une application MFC à l’aide de l’Assistant Application MFC

Ces étapes varient en fonction de la version de Visual Studio que vous utilisez. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="msvc-160"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Pour créer un projet MFC dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet** .

1. Dans la zone de recherche située en haut, tapez **MFC** , puis choisissez **application MFC** dans la liste des résultats.

1. Cliquez sur **Suivant** . Dans la page suivante, entrez un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

   Après l’affichage de l' **Assistant Application MFC** , utilisez les options suivantes :

   1. Choisissez le **type d’application** sur la gauche. Sélectionnez ensuite **document unique** et sélectionnez **document/vue architecture prise en charge** . Sous **style du projet** , **Sélectionnez Visual Studio** , puis dans la liste déroulante **style visuel et couleurs** , sélectionnez **Office 2007 (thème Blue)** .

   1. Dans le volet **prise en charge des documents composés** , sélectionnez **aucun** .

   1. N’apportez aucune modification au volet **Propriétés du modèle de document** .

   1. Dans le volet fonctionnalités de l' **interface utilisateur** , assurez-vous que l’option **utiliser une barre de menus et une barre d’outils** est sélectionnée. Laissez toutes les autres options telles quelles.

   1. Dans le volet **fonctionnalités avancées** , sélectionnez **contrôles ActiveX** , **manifeste de contrôle commun** et option **volet de navigation** . Laissez tout le reste tel quel. L’option du **volet de navigation** force l’Assistant à créer le volet à gauche de la fenêtre avec un `CMFCShellTreeCtrl` déjà incorporé.

   1. Nous n’allons pas apporter de modifications au volet **classes générées** . cliquez sur **Terminer** pour créer votre nouveau projet MFC.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Pour créer un projet MFC dans Visual Studio 2017 ou version antérieure

1. Utilisez l **'Assistant Application MFC** pour créer une application MFC. Pour exécuter l’Assistant, dans le menu **fichier** , sélectionnez **nouveau** , puis sélectionnez **projet** . La boîte **de dialogue Nouveau projet** s’affiche.

1. Dans la boîte de dialogue **nouveau projet** , développez le nœud **Visual C++** dans le volet **types de projets** , puis sélectionnez **MFC** . Ensuite, dans le volet **modèles** , sélectionnez **application MFC** . Tapez un nom pour le projet, par exemple, `MFCShellControls` puis cliquez sur **OK** .

   Après l’affichage de l' **Assistant Application MFC** , utilisez les options suivantes :

   1. Dans le volet **type d’application** , sous type d' **application** , désactivez l’option documents avec **onglet** . Ensuite, sélectionnez **document unique** et sélectionnez **document/vue architecture prise en charge** . Sous **style du projet** , **Sélectionnez Visual Studio** , puis dans la liste déroulante **style visuel et couleurs** , sélectionnez **Office 2007 (thème Blue)** .

   1. Dans le volet **prise en charge des documents composés** , sélectionnez **aucun** .

   1. N’apportez aucune modification au volet **chaînes du modèle de document** .

   1. Dans le volet **de prise en charge de base de données** (Visual Studio 2015 et versions antérieures), sélectionnez **aucun** , car l’application n’utilise pas de base de données.

   1. Dans le volet fonctionnalités de l' **interface utilisateur** , assurez-vous que l’option **utiliser une barre de menus et une barre d’outils** est sélectionnée. Laissez toutes les autres options telles quelles.

   1. Dans le volet **fonctionnalités avancées** , sous **fonctionnalités avancées** , sélectionnez uniquement **contrôles ActiveX** et **manifeste de contrôle commun** . Sous **volets des frames avancés** , sélectionnez uniquement l’option **volet de navigation** . L’Assistant crée alors le volet à gauche de la fenêtre avec un `CMFCShellTreeCtrl` déjà incorporé.

   1. Nous n’allons pas apporter de modifications au volet **classes générées** . cliquez sur **Terminer** pour créer votre nouveau projet MFC.

::: moniker-end

Vérifiez que l’application a été créée avec succès en la générant et en l’exécutant. Pour générer l’application, dans le menu **générer** , sélectionnez **générer la solution** . Si l’application est générée avec succès, exécutez l’application en sélectionnant **Démarrer le débogage** dans le menu **Déboguer** .

L’Assistant crée automatiquement une application dotée d’une barre de menus standard, d’une barre d’outils standard, d’une barre d’état standard et d’une barre Outlook située à gauche de la fenêtre, avec une vue **dossiers** et un affichage **calendrier** .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Pour ajouter le contrôle de liste de Shell à la vue de document

1. Dans cette section, vous allez ajouter une instance de `CMFCShellListCtrl` à la vue créée par l’Assistant. Ouvrez le fichier d’en-tête de vue en double-cliquant sur **MFCShellControlsView. h** dans le **Explorateur de solutions** .

   Localisez la `#pragma once` directive près du haut du fichier d’en-tête. Immédiatement en dessous, ajoutez ce code pour inclure le fichier d’en-tête pour `CMFCShellListCtrl` :

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   À présent, ajoutez une variable membre de type `CMFCShellListCtrl` . Tout d’abord, recherchez le commentaire suivant dans le fichier d’en-tête :

   ```cpp
   // Generated message map functions
   ```

   Juste au-dessus de ce commentaire, ajoutez ce code :

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. L' **Assistant Application MFC** a déjà créé un `CMFCShellTreeCtrl` objet dans la `CMainFrame` classe, mais il s’agit d’un membre protégé. Nous allons accéder ultérieurement à l’objet. par conséquent, créez un accesseur pour celui-ci. Ouvrez le fichier d’en-tête MainFrm. h en double-cliquant dessus dans la **Explorateur de solutions** . Recherchez le commentaire suivant :

   ```cpp
   // Attributes
   ```

   Immédiatement en dessous, ajoutez la déclaration de méthode suivante :

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Ensuite, ouvrez le fichier source MainFrm. cpp en double-cliquant dessus dans la **Explorateur de solutions** . En bas de ce fichier, ajoutez la définition de méthode suivante :

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. À présent, nous mettons à jour la `CMFCShellControlsView` classe pour gérer le `WM_CREATE` message Windows. Ouvrez la fenêtre de **affichage de classes** et sélectionnez la `CMFCShellControlsView` classe. Effectuez un clic droit et sélectionnez **Propriétés** .

   Ensuite, dans l' [Assistant classe](reference/mfc-class-wizard.md), cliquez sur l’onglet **messages** . Faites défiler jusqu’à ce que vous trouviez le `WM_CREATE` message. Dans la liste déroulante en regard de `WM_CREATE` , sélectionnez **\<Add> OnCreate** . La commande crée un gestionnaire de messages pour nous et met automatiquement à jour la table des messages MFC.

   Dans la `OnCreate` méthode, nous allons maintenant créer notre `CMFCShellListCtrl` objet. Recherchez la `OnCreate` définition de méthode dans le fichier source MFCShellControlsView. cpp et remplacez son implémentation par le code suivant :

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

1. Répétez l’étape précédente, mais pour le `WM_SIZE` message. Cela entraîne le redessin de la vue des applications chaque fois qu’un utilisateur modifie la taille de la fenêtre d’application. Remplacez la définition de la `OnSize` méthode par le code suivant :

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. La dernière étape consiste à connecter les `CMFCShellTreeCtrl` objets et à `CMFCShellListCtrl` l’aide de la méthode [CMFCShellTreeCtrl :: SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) . Une fois que vous avez appelé `CMFCShellTreeCtrl::SetRelatedList` , le `CMFCShellListCtrl` affiche automatiquement le contenu de l’élément sélectionné dans le `CMFCShellTreeCtrl` . Nous connectons les objets dans la `OnActivateView` méthode, qui est remplacée par [CView :: OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   Dans le fichier d’en-tête MFCShellControlsView. h, à l’intérieur de la `CMFCShellControlsView` déclaration de classe, ajoutez la déclaration de méthode suivante :

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Ensuite, ajoutez la définition de la méthode au fichier source MFCShellControlsView. cpp :

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

   Étant donné que nous appelons des méthodes à partir de la `CMainFrame` classe, nous devons ajouter une `#include` directive en haut du fichier source MFCShellControlsView. cpp :

    ```cpp
    #include "MainFrm.h"
    ```

1. Vérifiez que l’application a été créée avec succès en la générant et en l’exécutant. Pour générer l’application, dans le menu **générer** , sélectionnez **générer la solution** . Si l’application est générée avec succès, exécutez-la en sélectionnant **Démarrer le débogage** dans le menu **Déboguer** .

   Vous devez maintenant voir les détails de l’élément sélectionné dans le `CMFCShellTreeCtrl` volet vue. Lorsque vous cliquez sur un nœud dans le `CMFCShellTreeCtrl` , le `CMFCShellListCtrl` est automatiquement mis à jour. De même, si vous double-cliquez sur un dossier dans le `CMFCShellListCtrl` , le `CMFCShellTreeCtrl` doit être mis à jour automatiquement.

   Cliquez avec le bouton droit sur un élément dans le contrôle d’arborescence ou dans le contrôle de liste. Vous recevez le même menu contextuel que si vous utilisiez l' **Explorateur de fichiers** réel.

## <a name="next-steps"></a>Étapes suivantes

- L’Assistant a créé une barre Outlook avec un volet **dossiers** et un volet **calendrier** . Il n’est probablement pas judicieux d’avoir un volet **calendrier** dans une fenêtre de l' **Explorateur** . Supprimez donc ce volet maintenant.

- Le `CMFCShellListCtrl` prend en charge l’affichage des fichiers dans différents modes, tels que les **grandes icônes** , les **petites icônes** , les **listes** et les **Détails** . Mettez à jour votre application pour implémenter cette fonctionnalité. Conseil : consultez les [exemples de Visual C++](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)
