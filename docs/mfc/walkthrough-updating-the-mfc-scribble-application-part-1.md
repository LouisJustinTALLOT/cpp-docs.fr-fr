---
title: 'Procédure pas à pas : La mise à jour de l’Application de Scribble MFC (partie 1)'
ms.date: 04/25/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: a12c2bd2c1c1963630a1bd74b56f2c832573cc94
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450514"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Procédure pas à pas : La mise à jour de l’Application de Scribble MFC (partie 1)

Cette procédure pas à pas montre comment modifier une application MFC existante à utiliser l’interface utilisateur ruban. Visual Studio prend en charge le ruban d’Office 2007 et le ruban Windows Scenic de Windows 7. Pour plus d’informations sur l’interface utilisateur ruban, consultez [rubans](/windows/desktop/uxguide/cmd-ribbons).

Cette procédure pas à pas modifie l’exemple Scribble des MFC 1.0 classic qui vous permet d’utiliser la souris pour créer des dessins de ligne. Cette partie de la procédure pas à pas montre comment modifier l’exemple Scribble afin qu’il affiche une barre de ruban. [Partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) ajoute plus de boutons à la barre du ruban.

## <a name="prerequisites"></a>Prérequis

Le [exemple Scribble des MFC 1.0](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Pour obtenir de l’aide sur la conversion vers Visual Studio 2017 ou version ultérieure, consultez [Guide du portage : Scribble MFC](../porting/porting-guide-mfc-scribble.md).

##  <a name="top"></a> Sections

Cette partie de la procédure pas à pas comporte les sections suivantes :

- [En remplaçant les Classes de Base](#replaceclass)

- [Ajout de Bitmaps au projet](#addbitmap)

- [Ajout d’une ressource de ruban au projet](#addribbon)

- [Création d’une Instance de la barre du ruban](#createinstance)

- [Ajout d’une catégorie de ruban](#addcategory)

- [Définir l’apparence de l’Application](#setlook)

##  <a name="replaceclass"></a> En remplaçant les Classes de Base

Pour convertir une application qui prend en charge un menu à une application qui prend en charge d’un ruban, vous devez dériver de l’application, fenêtre frame et les classes de barre d’outils à partir de classes de base mis à jour. (Nous vous suggérons de que vous ne modifiez pas l’exemple Scribble d’origine. Au lieu de cela, nettoyer le projet Scribble, copiez-le dans un autre répertoire, puis modifiez la copie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Pour remplacer les classes de base dans l’application Scribble

1. Dans scribble.cpp, vérifiez que `CScribbleApp::InitInstance` inclut un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Ajoutez le code suivant au fichier stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. Dans scribble.h, modifiez la définition de la `CScribbleApp` afin qu’il est dérivé de la classe [CWinAppEx, classe](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 a été écrit lorsque les applications Windows utilisé un fichier d’initialisation (.ini) pour enregistrer les données de préférence utilisateur. Au lieu d’un fichier d’initialisation, modifiez Scribble pour stocker les préférences de l’utilisateur dans le Registre. Pour définir la clé de Registre et la base, tapez le code suivant dans `CScribbleApp::InitInstance` après la `LoadStdProfileSettings()` instruction.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Le frame principal pour une application d’interface (multidocument MDI) document dérivé n’est plus le `CMDIFrameWnd` classe. Au lieu de cela, elle est dérivée de la [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) classe.

    Dans les fichiers mainfrm.h et mainfrm.cpp, remplacez toutes les références à `CMDIFrameWnd` avec `CMDIFrameWndEx`.

1. Dans les fichiers childfrm.h et childfrm.cpp, remplacez `CMDIChildWnd` avec `CMDIChildWndEx`.

    Dans le childfrm. fichier h, remplacez `CSplitterWnd` avec `CSplitterWndEx`.

1. Modifier les barres d’outils et des barres d’état à utiliser les nouvelles classes MFC.

    Dans le fichier mainfrm.h :

    1. Remplacez `CToolBar` par `CMFCToolBar`.

    1. Remplacez `CStatusBar` par `CMFCStatusBar`.

1. Dans le fichier mainfrm.cpp :

    1. Remplacez `m_wndToolBar.SetBarStyle` avec `m_wndToolBar.SetPaneStyle`

    1. Remplacez `m_wndToolBar.GetBarStyle` avec `m_wndToolBar.GetPaneStyle`

    1. Remplacez `DockControlBar(&m_wndToolBar)` avec `DockPane(&m_wndToolBar)`

1. Dans le fichier ipframe.cpp, commentez les trois lignes de code suivantes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Enregistrer les modifications puis générer et exécuter l’application.

##  <a name="addbitmap"></a> Ajout de Bitmaps au projet

Les quatre étapes de cette procédure pas à pas qui nécessitent des ressources de la bitmap. Vous pouvez obtenir les bitmaps appropriés de différentes manières :

- Utilisez le [éditeurs de ressources](../windows/resource-editors.md) d’inventer vos propres images bitmap. Ou utiliser les éditeurs de ressources pour assembler les bitmaps d’images portable network graphics (.png) qui sont inclus avec Visual Studio et peuvent être téléchargées à partir de la [bibliothèque d’images Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Toutefois, le **ruban** interface utilisateur nécessite que certaines images bitmap prend en charge les images transparentes. Bitmaps transparentes utilisent des pixels de 32 bits, où 24 bits spécifier les composants rouges, vert et bleus de la couleur, et 8 bits définissent un *canal alpha* qui spécifie la transparence de la couleur. Les éditeurs de ressources actuel, vous peuvent afficher, mais pas modifier les images bitmap avec 32 bits de pixels. Par conséquent, utilisez un éditeur d’images externes au lieu des éditeurs de ressources pour manipuler des bitmaps transparentes.

- Copier un fichier de ressources approprié à partir d’une autre application à votre projet, puis importez les bitmaps à partir de ce fichier.

Cette procédure pas à pas copie des fichiers de ressources à partir de l’exemple créé dans [procédure pas à pas : Création d’une Application de ruban à l’aide de MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Pour ajouter des images bitmap au projet

1. Utilisez l’Explorateur de fichiers pour copier les fichiers .bmp suivants à partir du répertoire de ressources (`res`) de l’exemple de ruban pour le répertoire de ressources (`res`) du projet Scribble :

   1. Copiez main.bmp à votre projet Scribble.

   1. Copiez filesmall.bmp et filelarge.bmp à votre projet Scribble.

   1. Rendre les nouvelles copies des fichiers filelarge.bmp et filesmall.bmp, mais enregistrer les copies dans l’exemple de ruban. Renommer les copies homesmall.bmp homelarge.bmp, puis déplacez les copies à votre projet Scribble.

   1. Faites une copie du fichier toolbar.bmp, mais la copie est enregistrée dans l’exemple de ruban. Renommer le panelicons.bmp copie, puis déplacez la copie à votre projet Scribble.

1. Importer l’image bitmap pour une application MFC. Dans **affichage des ressources**, double-cliquez sur le **scribble.rc** nœud, double-cliquez sur le **Bitmap** nœud, puis cliquez sur **ajouter une ressource**. Dans la boîte de dialogue qui s’affiche, cliquez sur **importation**. Accédez à la `res` répertoire, sélectionnez le fichier main.bmp, puis cliquez sur **Open**.

   L’image bitmap main.bmp contient une image de 26 x 26. Modifier l’ID de la bitmap à `IDB_RIBBON_MAIN`.

1. Importer les bitmaps pour le menu fichier qui est attaché à la **Application** bouton.

   1. Importer le fichier filesmall.bmp, qui contient les onze 16 x 16 (16 x 176) des images. Modifier l’ID de la bitmap à `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Étant donné que nous avons besoin uniquement les images de huit premières 16 x 16 (16 x 128), vous pouvez survenir si vous le souhaitez la largeur de la partie droite de cette image bitmap à partir de 176 à 128.

   1. Importer le filelarge.bmp, qui contient les 32 x 32 (32 x 288) neuf images. Modifier l’ID de la bitmap à `IDB_RIBBON_FILELARGE`.

1. Importez les bitmaps pour les panneaux et les catégories de ruban. Chaque onglet dans la barre de ruban est une catégorie et se compose d’une étiquette de texte et image facultative.

   1. Importer l’image bitmap homesmall.bmp, qui contient les onze 16 x 16 images pour les bitmaps de petit bouton. Modifier l’ID de la bitmap à `IDB_RIBBON_HOMESMALL`.

   1. Importer l’image bitmap homelarge.bmp, lequel contient neuf 32 x 32 images pour les bitmaps de grand bouton. Modifier l’ID de la bitmap à `IDB_RIBBON_HOMELARGE`.

1. Importer des bitmaps pour les panneaux de ruban redimensionné. Ces fichiers bitmap ou des icônes du Panneau de configuration, sont utilisés après une opération de redimensionnement si le ruban est trop petit pour afficher le panneau tout entier.

   1. Importer l’image bitmap panelicons.bmp, qui contient huit 16 x 16 images. Dans le **propriétés** fenêtre de la **éditeur de bitmaps**, ajustez la largeur de la bitmap à 64 (16 x 64). Modifier l’ID de la bitmap à `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Étant donné que nous avons besoin uniquement les images de quatre premières 16 x 16 (16 x 64), vous pouvez survenir si vous le souhaitez la largeur de la partie droite de cette image bitmap à partir de 128 à 64.

##  <a name="addribbon"></a> Ajout d’une ressource de ruban au projet

Lorsque vous convertissez une application qui utilise les menus à une application qui utilise un ruban, vous n’êtes pas obligé de supprimer ou désactiver des menus existants. Simplement créer une ressource de ruban, ajoutez des boutons de ruban, puis associer les nouveaux boutons avec les éléments de menu existant. Bien que les menus ne sont plus visibles, les messages à partir de la barre du ruban sont routées via les menus et les raccourcis de menu continuent de fonctionner.

Un ruban comporte la **Application** bouton, ce qui est le grand bouton sur le côté supérieur gauche du ruban et un ou plusieurs onglets de catégorie. Chaque onglet de catégorie contient un ou plusieurs panneaux qui agissent comme conteneurs pour les contrôles et les boutons de ruban. La procédure suivante montre comment créer une ressource de ruban, puis personnalisez la **Application** bouton.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Pour ajouter une ressource de ruban au projet

1. Le projet Scribble dans **l’Explorateur de solutions**, dans le **projet** menu, cliquez sur **ajouter une ressource**.

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **ruban** puis cliquez sur **New**.

   Visual Studio crée une ressource de ruban et s’ouvre en mode design. L’ID de ressource de ruban est `IDR_RIBBON1`, qui s’affiche dans **affichage des ressources**. Le ruban contient une catégorie et un panneau.

1. Vous pouvez personnaliser le **Application** bouton en modifiant ses propriétés. Les ID de message utilisés dans ce code sont déjà définies dans le menu pour 1.0 de dessin à main levée.

1. Dans la vue conception, cliquez sur le **Application** bouton pour afficher ses propriétés. Modifier les valeurs des propriétés comme suit : **Image** à `IDB_RIBBON_MAIN`, **invite** à `File`, **clés** à `f`, **grandes Images** à `IDB_RIBBON_FILELARGE`et **Petites Images** à `IDB_RIBBON_FILESMALL`.

1. Les modifications suivantes créer le menu qui s’affiche lorsque l’utilisateur clique sur le **Application** bouton. Cliquez sur le bouton de sélection ( **...** ) à côté **Main éléments** pour ouvrir le **Éditeur d’éléments**.

   1. Avec le **élément** type **bouton** sélectionnée, cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `&New`, **ID** à `ID_FILE_NEW`, **Image** à `0`, **grande Image** à `0`.

   1. Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `&Save`, **ID** à `ID_FILE_SAVE`, **Image** à `2`, et **grande Image** à `2`.

   1. Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `Save &As`, **ID** à `ID_FILE_SAVE_AS`, **Image** à `3`, et **grande Image** à `3`.

   1. Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `&Print`, **ID** à `ID_FILE_PRINT`, **Image** à `4`, et **grande Image** à `4`.

   1. Modifier le **élément** type **séparateur** puis cliquez sur **ajouter**.

   1. Modifier le **élément** type **bouton**. Cliquez sur **ajouter** pour ajouter un cinquième bouton. Modification **légende** à `&Close`, **ID** à `ID_FILE_CLOSE`, **Image** à `5`, et **grande Image** à `5`.

1. Les modifications suivantes créer un sous-menu sous le **impression** bouton que vous avez créé à l’étape précédente.

   1. Cliquez sur le **impression** bouton, remplacez le **élément** type **étiquette**, puis cliquez sur **insérer**. Modification **légende** à `Preview and print the document`.

   1. Cliquez sur le **impression** bouton, remplacez le **élément** type à **bouton**, puis cliquez sur **insérer**. Modification **légende** à `&Print`, **ID** à `ID_FILE_PRINT`, **Image** à `4`, et **grande Image** à `4`.

   1. Cliquez sur le **impression** bouton, puis cliquez sur **insérer** pour ajouter un bouton. Modification **légende** à `&Quick Print`, **ID** à `ID_FILE_PRINT_DIRECT`, **Image** à `7`, et **grande Image** à `7`.

   1. Cliquez sur le **impression** bouton, puis cliquez sur **insérer** pour ajouter un autre bouton. Modification **légende** à `Print Pre&view`, **ID** à `ID_FILE_PRINT_PREVIEW`, **Image** à `6`, et **grande Image** à `6`.

   1. Vous avez modifié le **Main éléments**. Cliquez sur **fermer** pour quitter le **Éditeur d’éléments**.

1. La modification suivante crée un bouton Quitter qui s’affiche en bas de la **Application** menu du bouton.

   1. Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection ( **...** ) à côté **bouton** pour ouvrir le **Éditeur d’éléments**.

   1. Avec le **élément** type **bouton** sélectionnée, cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `E&xit`, **ID** à `ID_APP_EXIT`, **Image** à `8`.

   1. Vous avez modifié le **boutons**. Cliquez sur **fermer** pour quitter le **Éditeur d’éléments**.

##  <a name="createinstance"></a> Création d’une Instance de la barre du ruban

Les étapes suivantes montrent comment créer une instance de la barre du ruban au démarrage de votre application. Pour ajouter une barre de ruban à une application, déclarez la barre du ruban dans le fichier mainfrm.h. Puis, dans le fichier mainfrm.cpp, écrire du code pour charger la ressource de ruban.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Pour créer une instance de la barre du ruban

1. Dans le fichier mainfrm.h, ajoutez un membre de données à la section protégée de `CMainFrame`, la définition de classe pour le frame principal. Ce membre est pour la barre du ruban.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Dans le fichier mainfrm.cpp, ajoutez le code suivant avant la dernière `return` instruction à la fin de la `CMainFrame::OnCreate` (fonction). Il crée une instance de la barre du ruban.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> Personnalisation de la ressource de ruban

Maintenant que vous avez créé le **Application** bouton, vous pouvez ajouter des éléments du ruban.

> [!NOTE]
> Cette procédure pas à pas utilise la même icône du Panneau de configuration pour tous les panneaux. Toutefois, vous pouvez utiliser les autres index de liste d’images pour afficher d’autres icônes.

### <a name="to-add-a-home-category-and-edit-panel"></a>Pour ajouter une catégorie d’accueil et de modifier le panneau de configuration

1. Le programme de dessin à main levée ne requiert qu’une seule catégorie. Dans la vue conception, dans le **boîte à outils**, double-cliquez sur **catégorie** pour ajouter un et afficher ses propriétés. Modifier les valeurs des propriétés comme suit : **Légende** à `&Home`, **grandes Images** à `IDB_RIBBON_HOMELARGE`, **petites Images** à `IDB_RIBBON_HOMESMALL`.

1. Chaque catégorie de ruban s’articule autour des panneaux nommées. Chaque panneau contient un ensemble de contrôles que les opérations connexes terminée. Cette catégorie contient un panneau. Cliquez sur **panneau**, puis modifiez **légende** à `Edit`.

1. Pour le **modifier** panneau, ajoutez un bouton responsable de l’effacement du contenu du document. L’ID de message pour ce bouton a déjà été défini dans le `IDR_SCRIBBTYPE` ressource de menu. Spécifiez `Clear All` comme texte du bouton et l’index de la bitmap qui décore le bouton. Ouvrez le **boîte à outils**, puis faites glisser un **bouton** à la **modifier** panneau. Cliquez sur le bouton et redéfinissez **légende** à `Clear All`, **ID** à `ID_EDIT_CLEAR_ALL`, **Index d’Image** à `0`, **Large Image Index**  à `0`.

1. Enregistrer les modifications, puis générer et exécuter l’application. L’application Scribble doit être affichée, et il doit avoir une barre de ruban en haut de la fenêtre au lieu d’une barre de menus. La barre du ruban doit avoir une seule catégorie, **accueil**, et **accueil** doit avoir un panneau, **modifier**. Les boutons de ruban que vous avez ajouté doivent être associés avec les gestionnaires d’événements existant et le **Open**, **fermer**, **enregistrer**, **Print**, et **Effacer tout** boutons devraient fonctionner comme prévu.

##  <a name="setlook"></a> Définir l’apparence de l’Application

Un *Gestionnaire visuel* est un objet global qui contrôle tout le dessin pour une application. Étant donné que l’application Scribble d’origine utilise le style de l’interface (UI) d’utilisateur Office 2000, l’application peut paraître traditionnelle. Vous pouvez réinitialiser l’application pour utiliser le Gestionnaire visuel Office 2007 afin qu’il ressemble à une application Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Pour définir l’apparence de l’application

1. Dans le `CMainFrame::OnCreate` de fonction, tapez le code suivant avant la `return 0;` instruction pour modifier le Gestionnaire visuel par défaut et le style.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Enregistrer les modifications, puis générer et exécuter l’application. L’interface utilisateur de l’application doit ressembler à l’interface utilisateur d’Office 2007.

## <a name="next-steps"></a>Étapes suivantes

Vous avez modifié l’exemple Scribble des MFC 1.0 classique pour utiliser le **Concepteur de ruban**. Passez maintenant à [partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : Mise à jour de l’application Scribble MFC (partie 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
