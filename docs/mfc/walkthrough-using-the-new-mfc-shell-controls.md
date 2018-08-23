---
title: 'Procédure pas à pas : À l’aide de la bibliothèque MFC nouveau Shell de contrôles | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fbf10ef749df0ce5e5984ac773e0d2c00106b82
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541243"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Procédure pas à pas : utilisation des nouveaux contrôles d'environnement MFC

Dans cette procédure pas à pas, vous allez créer une application qui ressemble à l’Explorateur de fichiers. Vous allez créer une fenêtre qui contient deux volets. Le volet gauche contiendra un [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objet qui affiche votre poste de travail dans une vue hiérarchique. Le volet de droite contiendra un [CMFCShellListCtrl affichant](../mfc/reference/cmfcshelllistctrl-class.md) qui affiche les fichiers dans le dossier sélectionné dans le volet gauche.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas suppose que vous avez configuré Visual Studio à utiliser **paramètres de développement généraux**. Si vous utilisez un paramètre de développement différent, certaines fenêtres de Visual Studio que nous utilisons dans cette procédure pas à pas ne peuvent pas affichés par défaut.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Pour créer une nouvelle application MFC à l’aide de l’Assistant Application MFC

1. Utilisez le **Assistant Application MFC** pour créer une application MFC. Pour exécuter l’Assistant, à partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**. Le **nouveau projet** boîte de dialogue s’affiche.

2. Dans le **nouveau projet** boîte de dialogue, développez le **Visual C++** nœud dans le **types de projets** volet et sélectionnez **MFC**. Ensuite, dans le **modèles** volet, sélectionnez **Application MFC**. Tapez un nom pour le projet, tel que `MFCShellControls` et cliquez sur **OK**. Le **Assistant Application MFC** s’affichera.

3. Dans le **Assistant Application MFC** boîte de dialogue, cliquez sur **suivant**. Le **Type d’Application** volet s’affiche.

4. Sur le **Type d’Application** volet, sous **type d’Application**, désactivez le **documents avec onglet** option. Ensuite, sélectionnez **monodocument** et sélectionnez **support de l’architecture Document/vue**. Sous **projet style**, sélectionnez **Visual Studio**et à partir de la **style visuel et couleurs** liste déroulante liste, sélectionnez **Office 2007 (thème Blue)**. Laissez toutes les autres options telles quelles. Cliquez sur **suivant** pour afficher le **prise en charge des documents composés** volet.

5. Sur le **prise en charge des documents composés** volet, sélectionnez **aucun**. Cliquez sur **suivant** pour afficher le **chaînes modèles de Document** volet.

6. N’apportez pas de modifications à la **chaînes modèles de Document** volet. Cliquez sur **suivant** pour afficher le **prise en charge de la base de données** volet.

7. Sur le **prise en charge de la base de données** volet, sélectionnez **aucun** , car cette application n’utilise pas une base de données. Cliquez sur **suivant** pour afficher le **fonctionnalités d’Interface utilisateur** volet.

8. Sur le **fonctionnalités d’Interface utilisateur** volet, assurez-vous que le **utiliser une barre de menus et la barre d’outils** option est sélectionnée. Laissez toutes les autres options telles quelles. Cliquez sur **suivant** pour afficher le **fonctionnalités avancées** volet.

9. Sur le **fonctionnalités avancées** volet, sous **fonctionnalités avancées**, sélectionnez uniquement **contrôles ActiveX** et **le manifeste de contrôle commun**. Sous **avancé des fenêtres frames**, sélectionnez uniquement le **volet de Navigation** option. Cela entraîne l’Assistant créer le volet à gauche de la fenêtre avec un `CMFCShellTreeCtrl` déjà incorporées. Cliquez sur **suivant** pour afficher le **Classes générées** volet.

10. Nous n’allons pas d’apporter des modifications à la **Classes générées** volet. Par conséquent, cliquez sur **Terminer** pour créer votre projet MFC.

11. Vérifiez que l’application a été créée avec succès en créant et son exécution. Pour générer l’application, à partir de la **Build** menu, sélectionnez **générer la Solution**. Si l’application est générée avec succès, exécutez l’application en sélectionnant **démarrer le débogage** à partir de la **déboguer** menu.

   L’Assistant crée automatiquement une application qui a une barre de menus standard, une barre d’outils standard, une barre d’état standard et une barre Outlook à gauche de la fenêtre avec un **dossiers** vue et un **calendrier** vue .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Pour ajouter le contrôle de liste de shell en mode document

1. Dans cette section, vous allez ajouter une instance de `CMFCShellListCtrl` à la vue créée par l’Assistant. Ouvrez le fichier d’en-tête de vue en double-cliquant sur MFCShellControlsView.h dans le **l’Explorateur de solutions**.

   Recherchez la `#pragma once` directive au début du fichier d’en-tête. Juste en dessous, elle ajoute ce code pour inclure le fichier d’en-tête pour `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Ajoutez maintenant une variable membre de type `CMFCShellListCtrl`. Tout d’abord, recherchez le commentaire suivant dans le fichier d’en-tête :

   ```cpp
   // Generated message map functions
   ```

   Immédiatement au-dessus de ce commentaire ajoutez ce code :

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

2. Le **Assistant Application MFC** déjà créé un `CMFCShellTreeCtrl` de l’objet dans le `CMainFrame` classe, mais il est un membre protégé. Nous accéderons ultérieurement cet objet. Par conséquent, créez un accesseur pour celle-ci maintenant. Ouvrez le fichier d’en-tête MainFrm.h en double-cliquant dessus dans le **l’Explorateur de solutions**. Recherchez le commentaire suivant :

   ```cpp
   // Attributes
   ```

   Immédiatement dans cette section, ajoutez la déclaration de méthode suivante :

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Ensuite, ouvrez le fichier source MainFrm.cpp en double-cliquant dessus dans le **l’Explorateur de solutions**. En bas de ce fichier, ajoutez la définition de méthode suivante :

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

3. Maintenant nous mettons à jour le `CMFCShellControlsView` classe pour gérer les **WM_CREATE** message windows. Ouvrez le fichier d’en-tête MFCShellControlsView.h, puis cliquez sur cette ligne de code :

    ```cpp
    class CMFCShellControlsView : public CView
    ```

   Ensuite, dans le **propriétés** fenêtre, cliquez sur le **Messages** icône. Défiler vers le bas jusqu'à ce que vous trouviez le **WM_CREATE** message. Dans la liste déroulante liste suivant pour **WM_CREATE**, sélectionnez  **\<Ajouter > OnCreate**. Cela crée un gestionnaire de messages pour nous et met automatiquement à jour la table des messages MFC.

   Dans le `OnCreate` méthode nous allons maintenant créer notre `CMFCShellListCtrl` objet. Rechercher le `OnCreate` définition de méthode dans le MFCShellControlsView.cpp de source de fichier et remplacez son implémentation par le code suivant :

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

4. Répétez l’étape précédente, mais pour le **WM_SIZE** message. Cela entraîne l’affichage des applications à être redessiné chaque fois qu’un utilisateur modifie la taille de la fenêtre d’application. Remplacez la définition pour le `OnSize` méthode avec le code suivant :

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

5. La dernière étape consiste à se connecter le `CMFCShellTreeCtrl` et `CMFCShellListCtrl` objets à l’aide de la [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) (méthode). Après avoir appelé cette méthode, le `CMFCShellListCtrl` s’affiche automatiquement le contenu de l’élément sélectionné dans le `CMFCShellTreeCtrl`. Nous le ferons le `OnActivateView` (méthode), qui est substituée à partir de [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   Dans le fichier d’en-tête MFCShellControlsView.h, à l’intérieur de la `CMFCShellControlsView` déclaration de classe, ajoutez la déclaration de méthode suivante :

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Ensuite, ajoutez la définition de cette méthode au fichier source MFCShellControlsView.cpp :

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

   Étant donné que nous allons appeler des méthodes à partir de la `CMainFrame` (classe), nous devons ajouter un `#include` directive en haut du fichier source MFCShellControlsView.cpp :

    ```cpp
    #include "MainFrm.h"
    ```

6. Vérifiez que l’application a été créée avec succès en créant et son exécution. Pour générer l’application, à partir de la **Build** menu, sélectionnez **générer la Solution**. Si l’application est générée avec succès, exécutez-la en sélectionnant **démarrer le débogage** à partir de la **déboguer** menu.

   Vous devriez maintenant voir les détails de l’élément sélectionné dans le `CMFCShellTreeCtrl` dans le volet d’affichage. Lorsque vous cliquez sur un nœud dans le `CMFCShellTreeCtrl`, le `CMFCShellListCtrl` sera automatiquement mise à jour. De même, si vous double-cliquez sur un dossier dans le `CMFCShellListCtrl`, la `CMFCShellTreeCtrl` doit être automatiquement mis à jour.

   Cliquez avec le bouton droit de la souris sur n’importe quel élément dans le contrôle d’arborescence ou dans le contrôle de liste. Notez que vous obtenez le même menu contextuel comme si vous utilisiez l’Explorateur de fichiers réels.

## <a name="next-steps"></a>Étapes suivantes

- L’Assistant a créé une barre Outlook avec à la fois un **dossiers** volet et un **calendrier** volet. Il ne fait probablement pas judicieux d’avoir un **calendrier** volet dans une fenêtre d’Explorateur. Par conséquent, supprimez ce volet maintenant.

- Le `CMFCShellListCtrl` prend en charge l’affichage des fichiers dans des modes différents, tels que **grandes icônes**, **petites icônes**, **liste**, et **détails**. Mettre à jour votre application pour implémenter cette fonctionnalité. Conseil : consultez [exemples Visual C++](../visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)  
