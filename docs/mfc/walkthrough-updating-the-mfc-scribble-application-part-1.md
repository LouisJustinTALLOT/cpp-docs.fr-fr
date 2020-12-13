---
description: 'En savoir plus sur : procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)'
title: 'Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: bb60e535031670eddc84e7170431ad6622d434b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142972"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)

Cette procédure pas à pas montre comment modifier une application MFC existante pour utiliser l’interface utilisateur du ruban. Visual Studio prend en charge le ruban Office 2007 et le ruban paysages de Windows 7. Pour plus d’informations sur l’interface utilisateur du ruban, consultez [rubans](/windows/win32/uxguide/cmd-ribbons).

Cette procédure pas à pas modifie l’exemple MFC Scribble 1,0 qui vous permet d’utiliser la souris pour créer des dessins en courbes. Cette partie de la procédure pas à pas montre comment modifier l’exemple SCRIBBLE pour qu’il affiche une barre de ruban. La [partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) ajoute davantage de boutons à la barre du ruban.

## <a name="prerequisites"></a>Prérequis

[Exemple MFC scribble 1,0](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/general/Scribble). Pour obtenir de l’aide sur la conversion vers Visual Studio 2017 ou version ultérieure, consultez [Guide du Portage : Scribble MFC](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a> Sections

Cette partie de la procédure pas à pas contient les sections suivantes :

- [Remplacement des classes de base](#replaceclass)

- [Ajout de bitmaps au projet](#addbitmap)

- [Ajout d’une ressource de ruban au projet](#addribbon)

- [Création d’une instance de la barre du ruban](#createinstance)

- [Ajout d’une catégorie de ruban](#addcategory)

- [Définition de l’apparence de l’application](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a> Remplacement des classes de base

Pour convertir une application qui prend en charge un menu en une application qui prend en charge un ruban, vous devez dériver les classes application, fenêtre frame et Toolbar des classes de base mises à jour. (Nous vous suggérons de ne pas modifier l’exemple SCRIBBLE d’origine. Au lieu de cela, nettoyez le projet Scribble, copiez-le dans un autre répertoire, puis modifiez la copie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Pour remplacer les classes de base dans l’application Scribble

1. Dans Scribble. cpp, vérifiez que `CScribbleApp::InitInstance` comprend un appel à [AfxOLEInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Ajoutez le code suivant au fichier *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) :

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. Dans Scribble. h, modifiez la définition de la `CScribbleApp` classe afin qu’elle soit dérivée de la [classe CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1,0 a été écrit lorsque les applications Windows utilisaient un fichier d’initialisation (. ini) pour enregistrer les données de préférence de l’utilisateur. Au lieu d’un fichier d’initialisation, modifiez Scribble pour stocker les préférences de l’utilisateur dans le registre. Pour définir la clé de Registre et la base, tapez le code suivant dans `CScribbleApp::InitInstance` après l' `LoadStdProfileSettings()` instruction.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Le frame principal d’une application d’interface multidocument (MDI, multiple document interface) n’est plus dérivé de la `CMDIFrameWnd` classe. Au lieu de cela, elle est dérivée de la classe [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) .

    Dans les fichiers MainFrm. h et MainFrm. cpp, remplacez toutes les références à `CMDIFrameWnd` par `CMDIFrameWndEx` .

1. Dans les fichiers ChildFrm. h et ChildFrm. cpp, remplacez `CMDIChildWnd` par `CMDIChildWndEx` .

    Dans le ChildFrm. fichier h, remplacez `CSplitterWnd` par `CSplitterWndEx` .

1. Modifiez les barres d’outils et les barres d’État pour utiliser les nouvelles classes MFC.

    Dans le fichier MainFrm. h :

    1. Remplacez `CToolBar` par `CMFCToolBar`.

    1. Remplacez `CStatusBar` par `CMFCStatusBar`.

1. Dans le fichier MainFrm. cpp :

    1. Remplacer `m_wndToolBar.SetBarStyle` par `m_wndToolBar.SetPaneStyle`

    1. Remplacer `m_wndToolBar.GetBarStyle` par `m_wndToolBar.GetPaneStyle`

    1. Remplacer `DockControlBar(&m_wndToolBar)` par `DockPane(&m_wndToolBar)`

1. Dans le fichier IpFrame. cpp, commentez les trois lignes de code suivantes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Enregistrez les modifications, puis générez et exécutez l’application.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a> Ajout de bitmaps au projet

Les quatre étapes suivantes de cette procédure pas à pas requièrent des ressources bitmap. Vous pouvez récupérer les bitmaps appropriées de différentes manières :

- Utilisez les [éditeurs de ressources](../windows/resource-editors.md) pour inventer vos propres bitmaps. Ou utilisez les éditeurs de ressources pour assembler des bitmaps à partir des images. png (Portable Network Graphics) qui sont incluses dans Visual Studio et qui peuvent être téléchargées à partir de la [bibliothèque d’images Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

    Toutefois, l’interface utilisateur du **ruban** requiert que certaines bitmaps prennent en charge les images transparentes. Les bitmaps transparentes utilisent des pixels de 32 bits, où 24 bits spécifient les composants rouge, vert et bleu de la couleur, et 8 bits définissent un *canal alpha* qui spécifie la transparence de la couleur. Les éditeurs de ressources actuels peuvent afficher, mais pas modifier les bitmaps avec des pixels de 32 bits. Par conséquent, utilisez un éditeur d’images externes plutôt que les éditeurs de ressources pour manipuler les bitmaps transparentes.

- Copiez un fichier de ressources approprié à partir d’une autre application dans votre projet, puis importez les bitmaps à partir de ce fichier.

Cette procédure pas à pas copie les fichiers de ressources de l’exemple créé dans [procédure pas à pas : création d’une application de ruban à l’aide de MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Pour ajouter des bitmaps au projet

1. Utilisez l’Explorateur de fichiers pour copier les fichiers. bmp suivants du répertoire Resources ( `res` ) de l’exemple de ruban vers le répertoire de ressources ( `res` ) du projet Scribble :

   1. Copiez main.bmp dans votre projet Scribble.

   1. Copiez filesmall.bmp et filelarge.bmp dans votre projet Scribble.

   1. Créez de nouvelles copies des fichiers filelarge.bmp et filesmall.bmp, mais enregistrez les copies dans l’exemple de ruban. Renommez les copies homesmall.bmp et homelarge.bmp puis déplacez les copies vers votre projet Scribble.

   1. Effectuez une copie du fichier de toolbar.bmp, mais enregistrez la copie dans l’exemple de ruban. Renommez la copie panelicons.bmp puis déplacez la copie dans votre projet Scribble.

1. Importez l’image bitmap pour une application MFC. Dans **affichage des ressources**, double-cliquez sur le nœud **Scribble. RC** , double-cliquez sur le nœud **bitmap** , puis cliquez sur **Ajouter une ressource**. Dans la boîte de dialogue qui s’affiche, cliquez sur **Importer**. Accédez au `res` répertoire, sélectionnez le fichier main.bmp, puis cliquez sur **ouvrir**.

   La bitmap main.bmp contient une image 26x26. Remplacez l’ID de l’image bitmap par `IDB_RIBBON_MAIN` .

1. Importez les bitmaps du menu fichier associé au bouton **application** .

   1. Importez le fichier filesmall.bmp, qui contient onze images de 16 x 16 (16x176). Remplacez l’ID de l’image bitmap par `IDB_RIBBON_FILESMALL` .

   > [!NOTE]
   > Étant donné que nous avons uniquement besoin des huit premières images 16x16 (16x128), vous pouvez éventuellement rogner la largeur de la partie droite de cette image bitmap de 176 à 128.

   1. Importez le filelarge.bmp, qui contient neuf images 32x32 (32x288). Remplacez l’ID de l’image bitmap par `IDB_RIBBON_FILELARGE` .

1. Importez les bitmaps pour les catégories et les panneaux du ruban. Chaque onglet de la barre du ruban est une catégorie et se compose d’une étiquette de texte et d’une image facultative.

   1. Importez le homesmall.bmp bitmap, qui contient onze images 16 x 16 pour les petites bitmaps de bouton. Remplacez l’ID de l’image bitmap par `IDB_RIBBON_HOMESMALL` .

   1. Importez le homelarge.bmp bitmap, qui contient neuf images 32x32 pour les bitmaps de boutons de grande taille. Remplacez l’ID de l’image bitmap par `IDB_RIBBON_HOMELARGE` .

1. Importez des bitmaps pour les panneaux du ruban redimensionnés. Ces bitmaps, ou icônes de panneau, sont utilisées après une opération de redimensionnement si le ruban est trop petit pour afficher le panneau entier.

   1. Importez le panelicons.bmp bitmap, qui contient huit images 16x16. Dans la fenêtre **Propriétés** de l' **éditeur bitmap**, ajustez la largeur de l’image bitmap à 64 (16x64). Remplacez l’ID de l’image bitmap par `IDB_PANEL_ICONS` .

   > [!NOTE]
   > Étant donné que nous avons uniquement besoin des quatre premières images 16x16 (16x64), vous pouvez éventuellement rogner la largeur de la partie droite de cette image bitmap de 128 à 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a> Ajout d’une ressource de ruban au projet

Lorsque vous convertissez une application qui utilise des menus vers une application qui utilise un ruban, vous n’êtes pas obligé de supprimer ou de désactiver les menus existants. Créez simplement une ressource de ruban, ajoutez des boutons de ruban, puis associez les nouveaux boutons aux éléments de menu existants. Bien que les menus ne soient plus visibles, les messages de la barre du ruban sont acheminés via les menus et les raccourcis des menus continuent de fonctionner.

Un ruban se compose du bouton d' **application** , qui est le grand bouton sur le côté supérieur gauche du ruban, ainsi qu’un ou plusieurs onglets de catégorie. Chaque onglet de catégorie contient un ou plusieurs panneaux qui jouent le rôle de conteneurs pour les boutons de ruban et les contrôles. La procédure suivante montre comment créer une ressource de ruban, puis personnaliser le bouton d' **application** .

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Pour ajouter une ressource de ruban au projet

1. Une fois le projet Scribble sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Ajouter une ressource**.

1. Dans la boîte de dialogue **Ajouter une ressource** , sélectionnez **ruban** , puis cliquez sur **nouveau**.

   Visual Studio crée une ressource de ruban et l’ouvre en mode Design. L’ID de ressource du ruban est `IDR_RIBBON1` , qui est affiché dans **affichage des ressources**. Le ruban contient une catégorie et un panneau.

1. Vous pouvez personnaliser le bouton de l' **application** en modifiant ses propriétés. Les ID de message utilisés dans ce code sont déjà définis dans le menu pour Scribble 1,0.

1. En mode conception, cliquez sur le bouton **application** pour afficher ses propriétés. Modifiez les valeurs des propriétés comme suit : **image** vers `IDB_RIBBON_MAIN` , **invite** à, `File` **clés** `f` , **images de grande taille** `IDB_RIBBON_FILELARGE` et **petites images** vers `IDB_RIBBON_FILESMALL` .

1. Les modifications suivantes créent le menu qui s’affiche lorsque l’utilisateur clique sur le bouton **application** . Cliquez sur les points de suspension (**...**) en regard des **éléments principaux** pour ouvrir l' **éditeur d’éléments**.

   1. Le **bouton** type d' **élément** étant sélectionné, cliquez sur **Ajouter** pour ajouter un bouton. Remplacez la **légende** par, `&New` **ID** `ID_FILE_NEW` , **image** par `0` , **image large** par `0` .

   1. Cliquez sur **Ajouter** pour ajouter un bouton. Remplacez **Caption** par `&Save` , **ID** par `ID_FILE_SAVE` , **image** par `2` et **image large** par `2` .

   1. Cliquez sur **Ajouter** pour ajouter un bouton. Remplacez **Caption** par `Save &As` , **ID** par `ID_FILE_SAVE_AS` , **image** par `3` et **image large** par `3` .

   1. Cliquez sur **Ajouter** pour ajouter un bouton. Remplacez **Caption** par `&Print` , **ID** par `ID_FILE_PRINT` , **image** par `4` et **image large** par `4` .

   1. Modifiez le type d' **élément** en **séparateur** , puis cliquez sur **Ajouter**.

   1. Modifiez le type d' **élément** en **Button**. Cliquez sur **Ajouter** pour ajouter un cinquième bouton. Remplacez **Caption** par `&Close` , **ID** par `ID_FILE_CLOSE` , **image** par `5` et **image large** par `5` .

1. Les modifications suivantes créent un sous-menu sous le bouton **Imprimer** que vous avez créé à l’étape précédente.

   1. Cliquez sur le bouton **Imprimer** , changez le type d' **élément** en **étiquette**, puis cliquez sur **Insérer**. Remplacez **Caption** par `Preview and print the document` .

   1. Cliquez sur le bouton **Imprimer** , changez le type d' **élément** en **Button**, puis cliquez sur **Insérer**. Remplacez **Caption** par `&Print` , **ID** par `ID_FILE_PRINT` , **image** par `4` et **image large** par `4` .

   1. Cliquez sur le bouton **Imprimer** , puis cliquez sur **Insérer** pour ajouter un bouton. Remplacez **Caption** par `&Quick Print` , **ID** par `ID_FILE_PRINT_DIRECT` , **image** par `7` et **image large** par `7` .

   1. Cliquez sur le bouton **Imprimer** , puis cliquez sur **Insérer** pour ajouter un autre bouton. Remplacez **Caption** par `Print Pre&view` , **ID** par `ID_FILE_PRINT_PREVIEW` , **image** par `6` et **image large** par `6` .

   1. Vous avez maintenant modifié les **éléments principaux**. Cliquez sur **Fermer** pour quitter l' **éditeur d’éléments**.

1. La modification suivante crée un bouton quitter qui apparaît en bas du menu du bouton de l' **application** .

   1. Choisissez l’onglet **affichage des ressources** dans **Explorateur de solutions**.
   1. Dans la fenêtre **Propriétés** , cliquez sur le **bouton** de sélection (**...**) en regard de pour ouvrir l' **éditeur d’éléments**.

   1. Le **bouton** type d' **élément** étant sélectionné, cliquez sur **Ajouter** pour ajouter un bouton. Remplacez la **légende** par `E&xit` , **ID** par `ID_APP_EXIT` , **image** par `8` .

   1. Vous avez modifié les **boutons**. Cliquez sur **Fermer** pour quitter l' **éditeur d’éléments**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a> Création d’une instance de la barre du ruban

Les étapes suivantes montrent comment créer une instance de la barre du ruban au démarrage de votre application. Pour ajouter une barre de ruban à une application, déclarez la barre du ruban dans le fichier MainFrm. h. Ensuite, dans le fichier MainFrm. cpp, écrivez le code permettant de charger la ressource du ruban.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Pour créer une instance de la barre du ruban

1. Dans le fichier MainFrm. h, ajoutez un membre de données à la section protégée de `CMainFrame` , la définition de classe pour le frame principal. Ce membre est pour la barre de ruban.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Dans le fichier MainFrm. cpp, ajoutez le code suivant avant la dernière **`return`** instruction à la fin de la `CMainFrame::OnCreate` fonction. Elle crée une instance de la barre du ruban.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a> Personnalisation de la ressource du ruban

Maintenant que vous avez créé le bouton **application** , vous pouvez ajouter des éléments au ruban.

> [!NOTE]
> Cette procédure pas à pas utilise la même icône de panneau pour tous les panneaux. Toutefois, vous pouvez utiliser d’autres index de liste d’images pour afficher d’autres icônes.

### <a name="to-add-a-home-category-and-edit-panel"></a>Pour ajouter une catégorie d’hébergement et un panneau d’édition

1. Le programme Scribble requiert une seule catégorie. Dans la vue conception, dans la **boîte à outils**, double-cliquez sur **catégorie** pour en ajouter une et afficher ses propriétés. Modifiez les valeurs des propriétés comme suit : **légende** à `&Home` , **images volumineuses** `IDB_RIBBON_HOMELARGE` , **petites images** à `IDB_RIBBON_HOMESMALL` .

1. Chaque catégorie de ruban est organisée en panneaux nommés. Chaque panneau contient un ensemble de contrôles qui complètent les opérations associées. Cette catégorie dispose d’un panneau. Cliquez sur **panneau**, puis remplacez la **légende** par `Edit` .

1. Dans le volet d' **édition** , ajoutez un bouton responsable de l’effacement du contenu du document. L’ID de message de ce bouton a déjà été défini dans la `IDR_SCRIBBTYPE` ressource de menu. Spécifiez `Clear All` comme texte de bouton et l’index de la bitmap qui décore le bouton. Ouvrez la **boîte à outils**, puis faites glisser un **bouton** sur le panneau d' **édition** . Cliquez sur le bouton, puis remplacez **Caption** par, `Clear All` **ID** to, `ID_EDIT_CLEAR_ALL` **image index** to `0` , **large image index** par `0` .

1. Enregistrez les modifications, puis générez et exécutez l’application. L’application Scribble doit être affichée et elle doit avoir une barre de ruban en haut de la fenêtre au lieu d’une barre de menus. La barre du ruban doit avoir une catégorie, une **page d’habitation** et une **page d’hébergement** avec un panneau, **modifier**. Les boutons du ruban que vous avez ajoutés doivent être associés aux gestionnaires d’événements existants et les boutons **ouvrir**, **Fermer**, **Enregistrer**, **Imprimer** et **Effacer tout** doivent fonctionner comme prévu.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a> Définition de l’apparence de l’application

Un *Gestionnaire visuel* est un objet global qui contrôle tout le dessin pour une application. Étant donné que l’application Scribble d’origine utilise le style de l’interface utilisateur d’Office 2000, l’application peut paraître vieux. Vous pouvez réinitialiser l’application pour qu’elle utilise le gestionnaire visuel Office 2007 pour qu’elle ressemble à une application Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Pour définir l’apparence de l’application

1. Dans la `CMainFrame::OnCreate` fonction, tapez le code suivant avant l' `return 0;` instruction pour modifier le style et le gestionnaire visuel par défaut.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Enregistrez les modifications, puis générez et exécutez l’application. L’interface utilisateur de l’application doit ressembler à l’interface utilisateur d’Office 2007.

## <a name="next-steps"></a>Étapes suivantes

Vous avez modifié l’exemple de MFC Scribble 1,0 pour utiliser le **Concepteur de ruban**. Accédez maintenant à la [partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
