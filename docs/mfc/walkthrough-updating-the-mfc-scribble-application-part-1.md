---
title: 'Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360256"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)

Cette procédure pas à pas montre comment modifier une application MFC existante pour utiliser l’interface utilisateur Ribbon. Visual Studio prend en charge à la fois le ruban Office 2007 et le ruban scénique Windows 7. Pour plus d’informations sur l’interface utilisateur Ribbon, voir [Rubans](/windows/win32/uxguide/cmd-ribbons).

Ce pas-là modifie l’échantillon classique Scribble 1.0 MFC qui vous permet d’utiliser la souris pour créer des dessins en ligne. Cette partie de la procédure pas à pas montre comment modifier l’échantillon Scribble afin qu’il affiche une barre de ruban. [La partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) ajoute plus de boutons à la barre de ruban.

## <a name="prerequisites"></a>Prérequis

[L’échantillon Scribble 1.0 MFC](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Pour obtenir de l’aide pour vous convertir au Visual Studio 2017 ou plus tard, voir [Porting Guide: MFC Scribble](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Sections

Cette partie de la procédure pas à pas a les sections suivantes:

- [Remplacement des classes de base](#replaceclass)

- [Ajout de Bitmaps au projet](#addbitmap)

- [Ajout d’une ressource ruban au projet](#addribbon)

- [Création d’une instance de la barre de ruban](#createinstance)

- [Ajout d’une catégorie ruban](#addcategory)

- [Définir l’apparence de l’application](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Remplacement des classes de base

Pour convertir une application qui prend en charge un menu en une application qui prend en charge un ruban, vous devez tirer les classes d’application, de fenêtre de cadre et de barre d’outils des classes de base mises à jour. (Nous vous suggérons de ne pas modifier l’échantillon original de griffonnage. Au lieu de cela, nettoyer le projet Scribble, le copier à un autre répertoire, puis modifier la copie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Remplacer les classes de base de l’application Scribble

1. Dans scribble.cpp, `CScribbleApp::InitInstance` vérifiez qui comprend un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Ajoutez le code suivant au fichier *pch.h* *(stdafx.h* dans Visual Studio 2017 et plus tôt) :

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. Dans scribble.h, modifier la `CScribbleApp` définition de la classe afin qu’elle soit dérivée de [la classe CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 a été écrit lorsque les applications Windows ont utilisé un fichier d’initialisation (.ini) pour enregistrer les données de préférence de l’utilisateur. Au lieu d’un fichier d’initialisation, modifiez Scribble pour stocker les préférences des utilisateurs dans le registre. Pour définir la clé et la base `CScribbleApp::InitInstance` du `LoadStdProfileSettings()` registre, tapez le code suivant après l’énoncé.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Le cadre principal d’une application d’interface documentaire multiple `CMDIFrameWnd` (MDI) n’est plus dérivé de la classe. Au lieu de cela, il est dérivé de la classe [CMDIFrameWndEx.](../mfc/reference/cmdiframewndex-class.md)

    Dans les fichiers mainfrm.h et mainfrm.cpp, remplacez toutes les références à `CMDIFrameWnd` `CMDIFrameWndEx`.

1. Dans les fichiers childfrm.h et childfrm.cpp, remplacez par `CMDIChildWnd` `CMDIChildWndEx`.

    Dans le childfrm. h fichier, `CSplitterWnd` `CSplitterWndEx`remplacer par .

1. Modifier les barres d’outils et les barres d’état pour utiliser les nouvelles classes MFC.

    Dans le fichier mainfrm.h:

    1. Remplacez `CToolBar` par `CMFCToolBar`.

    1. Remplacez `CStatusBar` par `CMFCStatusBar`.

1. Dans le fichier mainfrm.cpp:

    1. Remplacer `m_wndToolBar.SetBarStyle` par `m_wndToolBar.SetPaneStyle`

    1. Remplacer `m_wndToolBar.GetBarStyle` par `m_wndToolBar.GetPaneStyle`

    1. Remplacer `DockControlBar(&m_wndToolBar)` par `DockPane(&m_wndToolBar)`

1. Dans le fichier ipframe.cpp, commentez les trois lignes de code suivantes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Enregistrer les modifications, puis construire et exécuter l’application.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Ajout de Bitmaps au projet

Les quatre prochaines étapes de cette procédure pas à pas nécessitent des ressources de bitmap. Vous pouvez obtenir les bitmaps appropriés de différentes façons:

- Utilisez les [éditeurs de ressources](../windows/resource-editors.md) pour inventer vos propres bitmaps. Ou utilisez les éditeurs de ressources pour assembler des bitmaps à partir des images graphiques réseau portable (.png) qui sont inclus avec Visual Studio et peuvent être téléchargés à partir de la [bibliothèque d’images Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Cependant, l’interface utilisateur **Ribbon** nécessite que certains bitmaps prennent en charge des images transparentes. Les bitmaps transparents utilisent des pixels 32 bits, où 24 bits spécifient les composants rouges, verts et bleus de la couleur, et 8 bits définissent un *canal alpha* qui spécifie la transparence de la couleur. Les éditeurs de ressources actuels peuvent afficher, mais ne pas modifier les bitmaps avec des pixels 32 bits. Par conséquent, utilisez un éditeur d’images externe au lieu des éditeurs de ressources pour manipuler des bitmaps transparents.

- Copiez un fichier de ressources approprié d’une autre application à votre projet, puis importez des bitmaps à partir de ce fichier.

Ce procédure pas à pas copie des fichiers de ressources de l’exemple créé dans [Pas à pas: Créer une application ruban en utilisant MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Pour ajouter des bitmaps au projet

1. Utilisez File Explorer pour copier les fichiers .bmp`res`suivants de l’annuaire des`res`ressources ( ) de l’exemple Ribbon à l’annuaire des ressources ( ) du projet Scribble :

   1. Copiez main.bmp à votre projet Scribble.

   1. Copiez filesmall.bmp et filelarge.bmp à votre projet Scribble.

   1. Faites de nouvelles copies des fichiers filelarge.bmp et filesmall.bmp, mais enregistrez les copies dans l’exemple du ruban. Renommer les copies homesmall.bmp et homelarge.bmp, puis déplacer les copies à votre projet Scribble.

   1. Faites une copie du fichier toolbar.bmp, mais enregistrez la copie dans l’exemple du ruban. Renommer la copie panelicons.bmp, puis déplacer la copie à votre projet Scribble.

1. Importer la bitmap pour une application MFC. Dans **Resource View**, double-cliquez sur le nœud **scribble.rc,** double-cliquez sur le nœud **Bitmap,** puis cliquez sur **Ajouter la ressource**. Sur la boîte de dialogue qui apparaît, cliquez sur **Import**. Naviguez sur `res` l’annuaire, sélectionnez le fichier main.bmp, puis cliquez sur **Open**.

   Le bitmap main.bmp contient une image 26x26. Modifier l’ID de la `IDB_RIBBON_MAIN`bitmap à .

1. Importez les bitmaps pour le menu de fichiers qui est attaché au bouton **d’application.**

   1. Importez le fichier filesmall.bmp, qui contient onze images 16x16 (16x176). Modifier l’ID de la `IDB_RIBBON_FILESMALL`bitmap à .

   > [!NOTE]
   > Parce que nous avons seulement besoin des huit premières images 16x16 (16x128), vous pouvez en option cultiver la largeur du côté droit de cette bitmap de 176 à 128.

   1. Importez le fichierlarge.bmp, qui contient neuf images 32x32 (32x288). Modifier l’ID de la `IDB_RIBBON_FILELARGE`bitmap à .

1. Importer les bitmaps pour les catégories de ruban et les panneaux. Chaque onglet sur la barre de ruban est une catégorie, et se compose d’une étiquette de texte et d’une image facultative.

   1. Importez le bitmap homemall.bmp, qui contient onze images 16x16 pour les petits bitmaps bouton. Modifier l’ID de la `IDB_RIBBON_HOMESMALL`bitmap à .

   1. Importez le bitmap homelarge.bmp, qui contient neuf images 32x32 pour les gros bitmaps bouton. Modifier l’ID de la `IDB_RIBBON_HOMELARGE`bitmap à .

1. Importer des bitmaps pour les panneaux de ruban resized. Ces bitmaps, ou icônes de panneau, sont utilisés après une opération de resize si le ruban est trop petit pour afficher le panneau entier.

   1. Importez le bitmap panelicons.bmp, qui contient huit images 16x16. Dans la fenêtre **Propriétés** de **l’éditeur Bitmap**, ajuster la largeur de la bitmap à 64 (16x64). Modifier l’ID de la `IDB_PANEL_ICONS`bitmap à .

   > [!NOTE]
   > Parce que nous avons seulement besoin des quatre premières images 16x16 (16x64), vous pouvez en option cultiver la largeur du côté droit de cette bitmap de 128 à 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Ajout d’une ressource ruban au projet

Lorsque vous convertissez une application qui utilise des menus en une application qui utilise un ruban, vous n’avez pas à supprimer ou désactiver les menus existants. Il suffit de créer une ressource ruban, ajouter des boutons ruban, puis associer les nouveaux boutons avec les éléments de menu existants. Bien que les menus ne soient plus visibles, les messages de la barre de ruban sont acheminés à travers les menus et les raccourcis de menu continuent de fonctionner.

Un ruban se compose du bouton **d’application,** qui est le grand bouton sur le côté supérieur gauche du ruban, et un ou plusieurs onglets de catégorie. Chaque onglet de catégorie contient un ou plusieurs panneaux qui servent de conteneurs pour les boutons et les commandes de ruban. La procédure suivante montre comment créer une ressource ruban, puis personnaliser le bouton **d’application.**

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Pour ajouter une ressource ruban au projet

1. Avec le projet Scribble sélectionné dans **Solution Explorer**, dans le menu **du projet,** cliquez sur **Add Resource**.

1. Dans la boîte de dialogue **Add Resource,** sélectionnez **Ruban,** puis cliquez sur **Nouveau**.

   Visual Studio crée une ressource ruban et l’ouvre dans la vue de conception. L’ID de `IDR_RIBBON1`la ressource ruban est , qui est affiché dans **Resource View**. Le ruban contient une catégorie et un panneau.

1. Vous pouvez personnaliser le bouton **Application** en modifiant ses propriétés. Les cartes d’identification du message qui sont utilisées dans ce code sont déjà définies dans le menu pour Scribble 1.0.

1. Dans la vue de conception, cliquez sur le bouton **Application** pour afficher ses propriétés. Changer les valeurs de `IDB_RIBBON_MAIN`propriété comme suit: **Image** à `IDB_RIBBON_FILELARGE`, **Prompt** à `File`, **Keys** to `f`, Large **Images** à , et Small **Images** à `IDB_RIBBON_FILESMALL`.

1. Les modifications suivantes créent le menu qui apparaît lorsque l’utilisateur clique sur le bouton **Application.** Cliquez sur l’ellipsis (**...**) à côté **des articles principaux** pour ouvrir **l’éditeur d’articles**.

   1. Avec le **bouton** de type **article** sélectionné, cliquez sur **Ajouter** pour ajouter un bouton. Légende **Caption** de `&New`changement `ID_FILE_NEW`à , **ID** à `0`, **Image** à `0`, Image **Large** à .

   1. Cliquez **sur Ajouter** pour ajouter un bouton. Légende **Caption** de `&Save`changement `ID_FILE_SAVE`à , **ID** à `2`, **Image** à `2`, et Image **Large** à .

   1. Cliquez **sur Ajouter** pour ajouter un bouton. Légende **Caption** de `Save &As`changement `ID_FILE_SAVE_AS`à , **ID** à `3`, **Image** à `3`, et Image **Large** à .

   1. Cliquez **sur Ajouter** pour ajouter un bouton. Légende **Caption** de `&Print`changement `ID_FILE_PRINT`à , **ID** à `4`, **Image** à `4`, et Image **Large** à .

   1. Modifier le type **d’élément** en **séparateur,** puis cliquez sur **Ajouter**.

   1. Modifier le type **d’élément** en **bouton**. Cliquez **sur Ajouter** pour ajouter un cinquième bouton. Légende **Caption** de `&Close`changement `ID_FILE_CLOSE`à , **ID** à `5`, **Image** à `5`, et Image **Large** à .

1. Les modifications suivantes créent un sous-mois sous le bouton **Imprimer** que vous avez créé dans l’étape précédente.

   1. Cliquez sur le bouton **Imprimer,** modifier le type **d’article** pour **l’étiquette,** puis cliquez sur **Insert**. Légende **Caption** de `Preview and print the document`changement pour .

   1. Cliquez sur le bouton **Imprimer,** modifier le type **d’élément** en **bouton**et cliquez sur **Insert**. Légende **Caption** de `&Print`changement `ID_FILE_PRINT`à , **ID** à `4`, **Image** à `4`, et Image **Large** à .

   1. Cliquez sur le bouton **Imprimer,** puis cliquez sur **Insert** pour ajouter un bouton. Légende **Caption** de `&Quick Print`changement `ID_FILE_PRINT_DIRECT`à , **ID** à `7`, **Image** à `7`, et Image **Large** à .

   1. Cliquez sur le bouton **Imprimer,** puis cliquez sur **Insert** pour ajouter un autre bouton. Légende **Caption** de `Print Pre&view`changement `ID_FILE_PRINT_PREVIEW`à , **ID** à `6`, **Image** à `6`, et Image **Large** à .

   1. Vous avez maintenant modifié les **éléments principaux**. Cliquez **près** pour quitter l’éditeur **d’éléments**.

1. La modification suivante crée un bouton de sortie qui apparaît au bas du menu du bouton **d’application.**

   1. Choisissez l’onglet **Vue des ressources** dans Solution **Explorer**.
   1. Dans la fenêtre **Propriétés,** cliquez sur l’ellipsis (**...**) à côté de **Button** pour ouvrir **l’éditeur d’éléments**.

   1. Avec le **bouton** de type **article** sélectionné, cliquez sur **Ajouter** pour ajouter un bouton. Légende **Caption** de `E&xit`changement à , `8` **ID** à `ID_APP_EXIT`, **Image** à .

   1. Vous avez modifié les **boutons**. Cliquez **près** pour quitter l’éditeur **d’éléments**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Création d’une instance de la barre de ruban

Les étapes suivantes montrent comment créer une instance de la barre de ruban lorsque votre application commence. Pour ajouter une barre de ruban à une demande, déclarez la barre de ruban dans le fichier mainfrm.h. Ensuite, dans le fichier mainfrm.cpp, écrivez du code pour charger la ressource ruban.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Pour créer une instance de la barre de ruban

1. Dans le fichier mainfrm.h, ajoutez un membre `CMainFrame`de données à la section protégée de , la définition de classe pour le cadre principal. Ce membre est pour la barre de ruban.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Dans le fichier mainfrm.cpp, ajoutez le `return` code suivant avant `CMainFrame::OnCreate` l’énoncé final à la fin de la fonction. Il crée une instance de la barre de ruban.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Personnaliser la ressource Ruban

Maintenant que vous avez créé le bouton **Application,** vous pouvez ajouter des éléments au ruban.

> [!NOTE]
> Cette procédure pas à pas utilise la même icône de panneau pour tous les panneaux. Cependant, vous pouvez utiliser d’autres index de liste d’images pour afficher d’autres icônes.

### <a name="to-add-a-home-category-and-edit-panel"></a>Pour ajouter une catégorie Home et un panneau d’édition

1. Le programme Scribble ne nécessite qu’une seule catégorie. Dans la vue de conception, dans la **boîte à outils**, **double-clic Catégorie** pour ajouter un et afficher ses propriétés. Changer les valeurs de `&Home`propriété comme `IDB_RIBBON_HOMELARGE`suit: **Légende** à , Grandes **Images** à , Petites **Images** à `IDB_RIBBON_HOMESMALL`.

1. Chaque catégorie de ruban est organisée en panneaux nommés. Chaque panneau contient un ensemble de contrôles qui complètent les opérations connexes. Cette catégorie comporte un panel. Cliquez sur **Panneau**, `Edit`puis changer **caption** pour .

1. Au panneau **Modifier,** ajoutez un bouton responsable de l’effacement du contenu du document. L’ID de message pour ce `IDR_SCRIBBTYPE` bouton a déjà été défini dans la ressource de menu. Spécifier `Clear All` comme le texte de bouton et l’index de la bitmap qui décore le bouton. Ouvrez la **boîte à outils,** puis faites glisser un **bouton** vers le panneau **Edit.** Cliquez sur le bouton, puis **changez de légende** pour `Clear All` `0`, **ID** à `ID_EDIT_CLEAR_ALL`, Image **Index** à `0`, Grand Indice **d’Image** à .

1. Enregistrer les modifications, puis construire et exécuter l’application. L’application Scribble doit être affichée, et il devrait avoir une barre de ruban en haut de la fenêtre au lieu d’une barre de menu. La barre de ruban devrait avoir une catégorie, **Accueil**, et **Accueil** devrait avoir un panneau, **Edit**. Les boutons ruban que vous avez ajoutés doivent être associés aux gestionnaires d’événements existants, et les boutons **Open**, **Close**, **Save**, **Print**, et **Clear All** devraient fonctionner comme prévu.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Définir l’apparence de l’application

Un *gestionnaire visuel* est un objet global qui contrôle tout dessin pour une application. Étant donné que l’application Scribble originale utilise le style d’interface utilisateur Office 2000 (interface utilisateur), l’application peut sembler démodée. Vous pouvez réinitialiser l’application pour utiliser le gestionnaire visuel Office 2007 afin qu’elle ressemble à une application Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Pour définir l’apparence de l’application

1. Dans `CMainFrame::OnCreate` la fonction, tapez `return 0;` le code suivant avant l’instruction pour modifier le gestionnaire visuel par défaut et le style.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Enregistrer les modifications, puis construire et exécuter l’application. L’interface utilisateur d’application devrait ressembler à l’interface utilisateur Office 2007.

## <a name="next-steps"></a>Étapes suivantes

Vous avez modifié l’échantillon classique Scribble 1.0 MFC pour utiliser le **concepteur de ruban**. Maintenant, allez à [la partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
