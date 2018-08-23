---
title: 'Procédure pas à pas : Mise à jour de l’Application de Scribble MFC (partie 1) | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cec86d276732bd7273d0f5585de5093f0cd01f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540645"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Procédure pas à pas : Mise à jour de l’Application de Scribble MFC (partie 1)

Cette procédure pas à pas montre comment modifier une application MFC existante à utiliser l’interface utilisateur ruban. Visual Studio prend en charge le ruban d’Office 2007 et le ruban Windows Scenic de Windows 7. Pour plus d’informations sur l’interface utilisateur ruban, consultez [rubans](http://go.microsoft.com/fwlink/p/?linkid=129233) sur le site Web MSDN.

Cette procédure pas à pas modifie l’exemple Scribble des MFC 1.0 classic qui vous permet d’utiliser la souris pour créer des dessins de ligne. Cette partie de la procédure pas à pas montre comment modifier l’exemple Scribble afin qu’il affiche une barre de ruban. [Partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) ajoute plus de boutons à la barre du ruban.

## <a name="prerequisites"></a>Prérequis

[Exemples Visual C++](../visual-cpp-samples.md)

[Exemples Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Sections

Cette partie de la procédure pas à pas comporte les sections suivantes :

- [En remplaçant les Classes de Base](#replaceclass)

- [Ajout de Bitmaps au projet](#addbitmap)

- [Ajout d’une ressource de ruban au projet](#addribbon)

- [Création d’une Instance de la barre du ruban](#createinstance)

- [Ajout d’une catégorie de ruban](#addcategory)

- [Définir l’apparence de l’Application](#setlook)

##  <a name="replaceclass"></a> En remplaçant les Classes de Base

Pour convertir une application qui prend en charge un menu à une application qui prend en charge d’un ruban, vous devez dériver de l’application, fenêtre frame et les classes de barre d’outils à partir de classes de base mis à jour. (Nous vous suggérons que vous ne pas modifier l’exemple Scribble d’origine ; au lieu de cela, nettoyer le projet Scribble, copiez-le vers un autre répertoire et ensuite modifier la copie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Pour remplacer les classes de base dans l’application Scribble

1. Dans scribble.cpp, vérifiez que `CScribbleApp::InitInstance` inclut un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

2. Ajoutez le code suivant au fichier stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

3. Dans scribble.h, modifiez la définition de la `CScribbleApp` afin qu’il est dérivé de la classe [CWinAppEx, classe](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

4. Scribble 1.0 a été écrit lorsque les applications Windows utilisé un fichier d’initialisation (.ini) pour enregistrer les données de préférence utilisateur. Au lieu d’un fichier d’initialisation, modifiez Scribble pour stocker les préférences de l’utilisateur dans le Registre. Pour définir la clé de Registre et la base, tapez le code suivant dans `CScribbleApp::InitInstance` après la `LoadStdProfileSettings()` instruction.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

5. Le frame principal pour une application d’interface (multidocument MDI) document dérivé n’est plus le `CMDIFrameWnd` classe. Au lieu de cela, elle est dérivée de la [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) classe.

     Dans les fichiers mainfrm.h et mainfrm.cpp, remplacez toutes les références à `CMDIFrameWnd` avec `CMDIFrameWndEx`.

6. Dans les fichiers childfrm.h et childfrm.cpp, remplacez `CMDIChildWnd` avec `CMDIChildWndEx`.

     Dans le childfrm. fichier h, remplacez `CSplitterWnd` avec `CSplitterWndEx`.

7. Modifier les barres d’outils et des barres d’état à utiliser les nouvelles classes MFC.

     Dans le fichier mainfrm.h :

    1. Remplacez `CToolBar` par `CMFCToolBar`.

    2. Remplacez `CStatusBar` par `CMFCStatusBar`.

8. Dans le fichier mainfrm.cpp :

    1. Remplacez `m_wndToolBar.SetBarStyle` avec `m_wndToolBar.SetPaneStyle`

    2. Remplacez `m_wndToolBar.GetBarStyle` avec `m_wndToolBar.GetPaneStyle`

    3. Remplacez `DockControlBar(&m_wndToolBar)` avec `DockPane(&m_wndToolBar)`

9. Dans le fichier ipframe.cpp, commentez les trois lignes de code suivantes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

10. Si vous avez l’intention de lier statiquement de votre application, ajoutez le code suivant au début du fichier de ressources (.rc) du projet.

    ```cpp
    #include "afxribbon.rc"
    ```

     Le fichier afxribbon.rc contient des ressources qui sont requises au moment de l’exécution. Le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md) inclut automatiquement ce fichier lorsque vous créez une application.

11. Enregistrer les modifications puis générer et exécuter l’application.

[[Sections](#top)]

##  <a name="addbitmap"></a> Ajout de Bitmaps au projet

Les quatre étapes de cette procédure pas à pas qui nécessitent des ressources de la bitmap. Vous pouvez obtenir des bitmaps appropriés de différentes manières :

- Utilisez le [éditeurs de ressources](../windows/resource-editors.md) d’inventer vos propres images bitmap. Ou utiliser les éditeurs de ressources pour assembler les bitmaps d’images portable network graphics (.png) qui sont inclus avec Visual Studio. Ces images sont dans le `VS2008ImageLibrary` directory.

     Toutefois, l’interface utilisateur ruban nécessite que certaines images bitmap prend en charge les images transparentes. Bitmaps transparentes utilisent des pixels de 32 bits, où 24 bits spécifier les composants rouges, vert et bleus de la couleur, et 8 bits définissent un *canal alpha* qui spécifie la transparence de la couleur. Les éditeurs de ressources actuel, vous peuvent afficher, mais pas modifier les images bitmap avec 32 bits de pixels. Par conséquent, utilisez un éditeur d’images externes au lieu des éditeurs de ressources pour manipuler des bitmaps transparentes.

- Copier un fichier de ressources approprié à partir d’une autre application à votre projet, puis importez les bitmaps à partir de ce fichier.

Cette procédure pas à pas copie des fichiers de ressources à partir d’une application dans le répertoire d’exemples.

### <a name="to-add-bitmaps-to-the-project"></a>Pour ajouter des images bitmap au projet

1. Utilisez l’Explorateur de fichiers pour copier les fichiers .bmp suivants à partir du répertoire de ressources (`res`) de l’exemple RibbonGadgets :

   1. Copiez main.bmp à votre projet Scribble.

   2. Copiez filesmall.bmp et filelarge.bmp à votre projet Scribble.

   3. Rendre les nouvelles copies des fichiers filelarge.bmp et filesmall.bmp, mais enregistrer les copies dans l’exemple RibbonGadgets. Renommer les copies homesmall.bmp homelarge.bmp, puis déplacez les copies à votre projet Scribble.

   4. Faites une copie du fichier toolbar.bmp, mais la copie est enregistrée dans l’exemple RibbonGadgets. Renommer le panelicons.bmp copie, puis déplacez la copie à votre projet Scribble.

2. Importer l’image bitmap pour une application MFC. Dans **affichage des ressources**, double-cliquez sur le **scribble.rc** nœud, double-cliquez sur le **Bitmap** nœud, puis cliquez sur **ajouter une ressource**. Dans la boîte de dialogue qui s’affiche, cliquez sur **importation**. Accédez à la `res` répertoire, sélectionnez le fichier main.bmp, puis cliquez sur **Open**.

   L’image bitmap main.bmp contient une image de 26 x 26. Modifier l’ID de l’image bitmap à IDB_RIBBON_MAIN.

3. Importez les bitmaps pour le menu fichier qui est attaché au bouton d’Application.

   1. Importer le fichier filesmall.bmp, qui contient les dix 16 x 16 (16 x 160) des images. Étant donné que nous avons besoin d’images que huit 16 x 16 (16 x 128), utilisez le **affichage des ressources** pour modifier la largeur de cette bitmap de 160 à 128. Modifier l’ID de l’image bitmap à IDB_RIBBON_FILESMALL.

   2. Importer le filelarge.bmp, qui contient huit 32 x 32 (32 x 256) des images. Modifier l’ID de l’image bitmap à IDB_RIBBON_FILELARGE.

4. Importez les bitmaps pour les panneaux et les catégories de ruban. Chaque onglet dans la barre de ruban est une catégorie et se compose d’une étiquette de texte et image facultative.

   1. Importer l’image bitmap homesmall.bmp, qui contient huit 16 x 16 images pour les bitmaps de petit bouton. Modifier l’ID de l’image bitmap à IDB_RIBBON_HOMESMALL.

   2. Importer l’image bitmap homelarge.bmp, qui contient huit 32 x 32 images pour les bitmaps de grand bouton. Modifier l’ID de l’image bitmap à IDB_RIBBON_HOMELARGE.

5. Importer des bitmaps pour les panneaux de ruban redimensionné. Ces fichiers bitmap ou des icônes du Panneau de configuration, sont utilisés après une opération de redimensionnement si le ruban est trop petit pour afficher le panneau tout entier.

   1. Importer l’image bitmap panelicons.bmp, qui contient huit 16 x 16 images. Dans le **propriétés** fenêtre de la **éditeur de bitmaps**, ajustez la largeur de la bitmap à 64 (16 x 64). Modifier l’ID de l’image bitmap à IDB_PANEL_ICONS.

[[Sections](#top)]

##  <a name="addribbon"></a> Ajout d’une ressource de ruban au projet

Lorsque vous convertissez une application qui utilise les menus à une application qui utilise un ruban, il est inutile de supprimer ou désactiver des menus existants. Au lieu de cela, vous créez une ressource de ruban, ajoutez des boutons de ruban, puis associez les nouveaux boutons avec les éléments de menu existant. Bien que les menus ne sont plus visibles, les messages à partir de la barre du ruban sont routées via les menus. En outre, les raccourcis du menu continuent de fonctionner.

Un ruban comporte le bouton d’Application, qui est le grand bouton sur le côté supérieur gauche du ruban, et un ou plusieurs onglets de catégorie. Chaque onglet de catégorie contient un ou plusieurs panneaux qui agissent comme conteneurs pour les contrôles et les boutons de ruban. La procédure suivante montre comment créer une ressource de ruban, puis personnaliser le bouton d’Application.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Pour ajouter une ressource de ruban au projet

1. Sur le **projet** menu, cliquez sur **ajouter une ressource**.

2. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **ruban** puis cliquez sur **New**.

   Visual Studio crée une ressource de ruban et s’ouvre en mode design. L’ID de ressource de ruban est IDR_RIBBON1, qui s’affiche dans **affichage des ressources**. Le ruban contient une catégorie et un panneau.

3. Vous pouvez personnaliser le bouton d’Application en modifiant ses propriétés. Les ID de message utilisés dans ce code sont déjà définies dans le menu pour 1.0 de dessin à main levée.

4. Dans la vue conception, cliquez sur le bouton d’Application pour afficher ses propriétés. Modifier les valeurs des propriétés comme suit : **Image** à `IDB_RIBBON_MAIN`, **invite** à `File`, **clés** à `f`, **degrandesImages** à `IDB_RIBBON_FILELARGE`, et **petites Images** à `IDB_RIBBON_FILESMALL`.

5. Les modifications suivantes créer le menu qui s’affiche lorsque l’utilisateur clique sur le bouton d’Application. Cliquez sur le bouton de sélection (**...** ) à côté **Main éléments** pour ouvrir le **Éditeur d’éléments**.

   1. Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `&New`, **ID** à `ID_FILE_NEW`, **Image** à `0`, **grande Image** à `0`.

   2. Cliquez sur **ajouter** pour ajouter un deuxième bouton. Modification **légende** à `&Save`, **ID** à `ID_FILE_SAVE`, **Image** à `2`, et **grande Image** à `2`.

   3. Cliquez sur **ajouter** pour ajouter un troisième bouton. Modification **légende** à `Save &As`, **ID** à `ID_FILE_SAVE_AS`, **Image** à `3`, et **grande Image** à `3`.

   4. Cliquez sur **ajouter** pour ajouter un quatrième bouton. Modification **légende** à `&Print`, **ID** à `ID_FILE_PRINT`, **Image** à `4`, et **grande Image** à `4`.

   5. Modifier le **élément** type **séparateur** puis cliquez sur **ajouter**.

   6. Modifier le **élément** type **bouton**. Cliquez sur **ajouter** pour ajouter un cinquième bouton. Modification **légende** à `&Close`, **ID** à `ID_FILE_CLOSE`, **Image** à `5`, et **grande Image** à `5`.

6. Les modifications suivantes créer un sous-menu sous le bouton d’impression que vous avez créé à l’étape précédente.

   1. Cliquez sur le **impression** bouton, remplacez le **élément** type **étiquette**, puis cliquez sur **insérer**. Modification **légende** à `Preview and print the document`.

   2. Cliquez sur le **impression** bouton, remplacez le **élément** type à **bouton**, puis cliquez sur **insérer**. Modification **légende** à `&Print`, **ID** à `ID_FILE_PRINT`, **Image** à `4`, et **grande Image** à `4`.

   3. Cliquez sur le **impression** bouton, puis cliquez sur **insérer** pour ajouter un bouton. Modification **légende** à `&Quick Print`, **ID** à `ID_FILE_PRINT_DIRECT`, **Image** à `7`, et **grande Image** à `7`.

   4. Cliquez sur le **impression** bouton, puis cliquez sur **insérer** pour ajouter un autre bouton. Modification **légende** à `Print Pre&view`, **ID** à `ID_FILE_PRINT_PREVIEW`, **Image** à `6`, et **grande Image** à `6`.

   5. Vous avez modifié le **Main éléments**. Cliquez sur **fermer** pour quitter le **Éditeur d’éléments**.

7. La modification suivante crée un bouton Quitter qui s’affiche en bas du menu de bouton d’Application.

   1. Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) à côté **bouton** pour ouvrir le **Éditeur d’éléments**.

   2. Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à `E&xit`, **ID** à `ID_APP_EXIT`, **Image** à `8`.

[[Sections](#top)]

##  <a name="createinstance"></a> Création d’une Instance de la barre du ruban

Les étapes suivantes montrent comment créer une instance de la barre du ruban au démarrage de votre application. Pour ajouter une barre de ruban à une application, déclarez la barre du ruban dans le fichier mainfrm.h. Puis, dans le fichier mainfrm.cpp, écrire du code pour charger la ressource de ruban.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Pour créer une instance de la barre du ruban

1. Dans le fichier mainfrm.h, ajoutez un membre de données à la section protégée de `CMainFrame`, la définition de classe pour le frame principal. Ce membre représente la barre du ruban.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Dans le fichier mainfrm.cpp, ajoutez le code suivant avant la dernière `return` instruction à la fin de la `CMainFrame::OnCreate` (fonction). Cette opération crée une instance de la barre du ruban.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

[[Sections](#top)]

##  <a name="addcategory"></a> Personnalisation de la ressource de ruban

Maintenant que vous avez créé le bouton d’Application, vous pouvez ajouter des éléments au ruban.

> [!NOTE]
> Cette procédure pas à pas utilise la même icône du Panneau de configuration pour tous les panneaux. Toutefois, vous pouvez utiliser les autres index de liste d’images pour afficher d’autres icônes.

### <a name="to-add-a-home-category-and-edit-panel"></a>Pour ajouter une catégorie d’accueil et de modifier le panneau de configuration

1. Le programme de dessin à main levée ne requiert qu’une seule catégorie. Dans la vue conception, cliquez sur **catégorie** pour afficher ses propriétés. Modifier les valeurs des propriétés comme suit : **légende** à `&Home`, **grandes Images** à `IDB_RIBBON_HOMELARGE`, **petites Images** à `IDB_RIBBON_HOMESMALL`.

2. Chaque catégorie de ruban s’articule autour des panneaux nommées. Chaque panneau contient un ensemble de contrôles qui effectuent des opérations associées. Cette catégorie contient un panneau. Cliquez sur **panneau**, puis modifiez **légende** à `Edit` et **Index d’Image** à `0`.

3. Pour le **modifier** panneau, ajoutez un bouton qui est responsable de l’effacement du contenu du document. L’ID de message pour ce bouton a déjà été défini dans la ressource de menu IDR_SCRIBBTYPE. Spécifiez `Clear All` comme texte du bouton et l’index de la bitmap qui décore le bouton. Ouvrez le **boîte à outils**, puis faites glisser un **bouton** à la **modifier** panneau. Cliquez sur le bouton et redéfinissez **légende** à `Clear All`, **ID** à `ID_EDIT_CLEAR_ALL`, **Index d’Image** à `0`, **Large Image Index**  à `0`.

4. Enregistrer les modifications, puis générer et exécuter l’application. L’application Scribble doit être affichée, et il doit avoir une barre de ruban en haut de la fenêtre au lieu d’une barre de menus. La barre du ruban doit avoir une seule catégorie, **accueil**, et **accueil** doit avoir un panneau, **modifier**. Les boutons de ruban que vous avez ajouté doivent être associés avec les gestionnaires d’événements existant et le **Open**, **fermer**, **enregistrer**, **Print**, et **Effacer tout** boutons devraient fonctionner comme prévu.

[[Sections](#top)]

##  <a name="setlook"></a> Définir l’apparence de l’Application

Un *Gestionnaire visuel* est un objet global qui contrôle tout le dessin pour une application. Étant donné que l’application Scribble d’origine utilise le style de l’interface (UI) d’utilisateur Office 2000, l’application peut paraître traditionnelle. Vous pouvez réinitialiser l’application pour utiliser le Gestionnaire visuel Office 2007 afin qu’il ressemble à une application Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Pour définir l’apparence de l’application

1. Dans le `CMainFrame::OnCreate` de fonction, tapez le code suivant pour modifier le Gestionnaire visuel par défaut et le style.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

2. Enregistrer les modifications, puis générer et exécuter l’application. L’interface utilisateur de l’application doit ressembler à l’interface utilisateur d’Office 2007.

[[Sections](#top)]

## <a name="next-steps"></a>Étapes suivantes

Vous avez modifié l’exemple Scribble des MFC 1.0 classique pour utiliser le Concepteur de ruban. Passez maintenant à [partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)  
[Procédure pas à pas : mise à jour de l’Application de Scribble MFC (partie 2)] (.. / mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)  
