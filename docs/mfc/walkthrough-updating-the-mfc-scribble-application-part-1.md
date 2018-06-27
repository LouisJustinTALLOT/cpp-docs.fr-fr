---
title: 'Procédure pas à pas : Mise à jour de l’Application de Scribble MFC (partie 1) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cfe91812d178618b1707f99aa10d6bd492109069
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956793"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Procédure pas à pas : Mise à jour de l’Application de Scribble MFC (partie 1)
Cette procédure pas à pas montre comment modifier une application MFC existante à utiliser l’interface utilisateur du ruban. Visual Studio prend en charge le ruban Office 2007 et le ruban paysages de Windows 7. Pour plus d’informations sur l’interface utilisateur du ruban, consultez [rubans](http://go.microsoft.com/fwlink/p/?linkid=129233) sur le site Web MSDN.  
  
 Cette procédure pas à pas modifie l’exemple MFC de 1.0 Scribble classique qui vous permet d’utiliser la souris pour créer des dessins de ligne. Cette partie de la procédure pas à pas montre comment modifier l’exemple Scribble afin qu’il affiche une barre de ruban. [Partie 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) ajoute plus de boutons de la barre du ruban.  
  
## <a name="prerequisites"></a>Prérequis  
 [Exemples Visual C++](../visual-cpp-samples.md)  
  
 [Exemples Visual C++](../visual-cpp-samples.md)  
  
##  <a name="top"></a> Sections  
 Cette partie de la procédure pas à pas comporte les sections suivantes :  
  
- [En remplaçant les Classes de Base](#replaceclass)  
  
- [Ajout d’images bitmap au projet](#addbitmap)  
  
- [Ajout d’une ressource de ruban au projet](#addribbon)  
  
- [Création d’une Instance de la barre du ruban](#createinstance)  
  
- [Ajout d’une catégorie de ruban](#addcategory)  
  
- [Définir l’apparence de l’Application](#setlook)  
  
##  <a name="replaceclass"></a> En remplaçant les Classes de Base  
 Pour convertir une application qui prend en charge un menu à une application qui prend en charge d’un ruban, vous devez dériver l’application, fenêtre frame et classes de barre d’outils à partir de classes de base de mise à jour. (Nous vous suggérons de que vous ne faire pas modifier l’exemple Scribble d’origine ; au lieu de cela, nettoyer le projet Scribble, copiez-le dans un autre répertoire et ensuite modifier la copie.)  
  
#### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Pour remplacer les classes de base dans l’application Scribble  
  
1.  Dans scribble.cpp, vérifiez que `CScribbleApp::InitInstance` inclut un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).  
  
2.  Ajoutez le code suivant dans le fichier stdafx.h.  
  
 ```  
    #include <afxcontrolbars.h>  
 ```  
  
3.  Dans scribble.h, modifiez la définition pour le `CScribbleApp` afin qu’il est dérivé de la classe [CWinAppEx classe](../mfc/reference/cwinappex-class.md).  
  
 ```  
    class CScribbleApp: public CWinAppEx  
 ```  
  
4.  Scribble 1.0 a été écrite lorsque les applications Windows utilisé un fichier d’initialisation (.ini) pour enregistrer les données de préférence utilisateur. Au lieu d’un fichier d’initialisation, modifiez le dessin à main levée pour stocker les préférences de l’utilisateur dans le Registre. Pour définir la clé de Registre et la base, tapez le code suivant dans `CScribbleApp::InitInstance` après la `LoadStdProfileSettings()` instruction.  
  
 ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));

 SetRegistryBase(_T("Settings"));

 ```  
  
5.  Le frame principal pour une application d’interface (multidocument MDI) document plusieurs dérivé n’est plus la `CMDIFrameWnd` classe. Au lieu de cela, elle est dérivée de la [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) classe.  
  
     Dans les fichiers mainfrm.h et mainfrm.cpp, remplacez toutes les références à `CMDIFrameWnd` avec `CMDIFrameWndEx`.  
  
6.  Dans les fichiers childfrm.h et childfrm.cpp, remplacez `CMDIChildWnd` avec `CMDIChildWndEx`.  
  
     Dans le childfrm. fichier h, remplacez `CSplitterWnd` avec `CSplitterWndEx`.  
  
7.  Modifier les barres d’outils et les barres d’état à utiliser les nouvelles classes MFC.  
  
     Dans le fichier mainfrm.h :  
  
    1.  Remplacez `CToolBar` par `CMFCToolBar`.  
  
    2.  Remplacez `CStatusBar` par `CMFCStatusBar`.  
  
8.  Dans le fichier mainfrm.cpp :  
  
    1.  Remplacez `m_wndToolBar.SetBarStyle` avec `m_wndToolBar.SetPaneStyle`  
  
    2.  Remplacez `m_wndToolBar.GetBarStyle` avec `m_wndToolBar.GetPaneStyle`  
  
    3.  Remplacez `DockControlBar(&m_wndToolBar)` avec `DockPane(&m_wndToolBar)`  
  
9. Dans le fichier ipframe.cpp, commentez les trois lignes de code suivantes.  
  
 ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);

 pWndFrame->EnableDocking(CBRS_ALIGN_ANY);

    pWndFrame->DockPane(&m_wndToolBar);

 ```  
  
10. Si vous souhaitez lier statiquement de votre application, ajoutez le code suivant au début du fichier de ressources (.rc) du projet.  
  
 ```  
    #include "afxribbon.rc"  
 ```  
  
     Le fichier afxribbon.rc contient des ressources qui sont requises au moment de l’exécution. Le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md) inclut ce fichier automatiquement lorsque vous créez une application.  
  
11. Enregistrer les modifications puis générer et exécuter l’application.  
  
 [[Sections](#top)]  
  
##  <a name="addbitmap"></a> Ajout d’images bitmap au projet  
 Les quatre étapes de cette procédure pas à pas nécessitent des ressources de l’image bitmap. Vous pouvez obtenir des bitmaps appropriés de différentes manières :  
  
-   Utilisez le [éditeurs de ressources](../windows/resource-editors.md) inventer votre propre bitmaps. Ou permet d’assembler des bitmaps à partir des images portable network graphics (.png) qui sont inclus dans les éditeurs de ressources [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Ces images sont dans le `VS2008ImageLibrary` active.  
  
     Toutefois, l’interface utilisateur du ruban requiert que certaines bitmaps prennent en charge les images transparentes. Bitmaps transparentes utilisent des pixels de 32 bits, 24 bits spécifier les composants rouges, verts et bleus de la couleur, alors que 8 bits définissent un *canal alpha* qui spécifie la transparence de la couleur. Les éditeurs de ressources en cours, vous peuvent afficher, mais pas modifier les bitmaps de pixels de 32 bits. Par conséquent, utilisez un éditeur d’image externe à la place les éditeurs de ressources pour manipuler des bitmaps transparentes.  
  
-   Copier un fichier de ressources approprié à partir d’une autre application à votre projet, puis importer les bitmaps de ce fichier.  
  
 Cette procédure copie les fichiers de ressources à partir d’une application dans le répertoire d’exemples.  
  
#### <a name="to-add-bitmaps-to-the-project"></a>Pour ajouter des images bitmap au projet  
  
1.  Utilisez l’Explorateur de fichiers pour copier les fichiers .bmp suivants à partir du répertoire de ressources (`res`) de l’exemple RibbonGadgets :  
  
    1.  Copiez main.bmp à votre projet Scribble.  
  
    2.  Copiez filesmall.bmp et filelarge.bmp à votre projet Scribble.  
  
    3.  Rendre les nouvelles copies des fichiers filelarge.bmp et filesmall.bmp, mais enregistrer les copies dans l’exemple RibbonGadgets. Renommez les copies homesmall.bmp homelarge.bmp, puis déplacez les copies à votre projet Scribble.  
  
    4.  Faites une copie du fichier toolbar.bmp, mais enregistrer la copie dans l’exemple RibbonGadgets. Renommer la copie panelicons.bmp, puis déplacez la copie à votre projet Scribble.  
  
2.  Importer l’image bitmap pour une application MFC. Dans **affichage des ressources**, double-cliquez sur le **scribble.rc** nœud, double-cliquez sur le **Bitmap** nœud, puis cliquez sur **ajouter une ressource**. Dans la boîte de dialogue qui s’affiche, cliquez sur **importation**. Accédez à la `res` répertoire, sélectionnez le fichier main.bmp, puis cliquez sur **ouvrir**.  
  
     L’image bitmap main.bmp contient une image de 26 x 26. Modifiez l’ID de l’image bitmap à IDB_RIBBON_MAIN.  
  
3.  Importez les bitmaps pour le menu fichier qui est attaché au bouton Application.  
  
    1.  Importez le fichier filesmall.bmp, qui contient les dix 16 x 16 (16 x 160) les images. Étant donné que nous avons ne besoin que huit 16 x 16 images (16 x 128), utilisez la **affichage des ressources** pour modifier la largeur de cette bitmap de 160 à 128. Modifiez l’ID de l’image bitmap à IDB_RIBBON_FILESMALL.  
  
    2.  Importer le filelarge.bmp, qui contient les huit 32 x 32 (32 x 256) les images. Modifiez l’ID de l’image bitmap à IDB_RIBBON_FILELARGE.  
  
4.  Importez les bitmaps pour les catégories de ruban et les panneaux. Chaque onglet de la barre du ruban est une catégorie et se compose d’une étiquette de texte et image facultative.  
  
    1.  Importer l’image bitmap homesmall.bmp, qui contient les huit 16 x 16 images bitmaps de petit bouton. Modifiez l’ID de l’image bitmap à IDB_RIBBON_HOMESMALL.  
  
    2.  Importer l’image bitmap homelarge.bmp, qui contient les huit 32 x 32 images bitmaps des boutons de grande taille. Modifiez l’ID de l’image bitmap à IDB_RIBBON_HOMELARGE.  
  
5.  Importez les bitmaps pour les volets de ruban redimensionné. Ces fichiers bitmap ou des icônes du Panneau de configuration, sont utilisés après une opération de redimensionnement si le ruban est trop petit pour afficher le panneau tout entier.  
  
    1.  Importer l’image bitmap panelicons.bmp, qui contient les huit 16 x 16 images. Dans le **propriétés** fenêtre de la **éditeur de bitmaps**, ajustez la largeur de la bitmap à 64 (16 x 64). Modifiez l’ID de l’image bitmap à IDB_PANEL_ICONS.  
  
 [[Sections](#top)]  
  
##  <a name="addribbon"></a> Ajout d’une ressource de ruban au projet  
 Lorsque vous convertissez une application qui utilise des menus pour une application qui utilise un ruban, il est inutile supprimer ou désactiver les menus existants. Au lieu de cela, vous créez une ressource de ruban, ajoutez des boutons de ruban et l’associez les nouveaux boutons les éléments de menu existant. Bien que les menus ne sont plus visibles, les messages à partir de la barre du ruban sont routées via les menus. En outre, les raccourcis du menu continuent à travailler.  
  
 Un ruban comprend le bouton d’Application, qui est le grand bouton dans le coin supérieur gauche du ruban, et un ou plusieurs onglets de catégorie. Chaque onglet de catégorie contient un ou plusieurs panneaux qui agissent comme conteneurs pour les contrôles et les boutons du ruban. La procédure suivante montre comment créer une ressource de ruban, puis personnalisez le bouton d’Application.  
  
#### <a name="to-add-a-ribbon-resource-to-the-project"></a>Pour ajouter une ressource de ruban au projet  
  
1.  Sur le **projet** menu, cliquez sur **ajouter une ressource**.  
  
2.  Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **ruban** puis cliquez sur **nouveau**.  
  
     Visual Studio crée une ressource de ruban et s’ouvre dans la vue de conception. L’ID de ressource de ruban est IDR_RIBBON1, qui est affichée dans **affichage des ressources**. Le ruban contient une catégorie et un panneau.  
  
3.  Vous pouvez personnaliser le bouton d’Application en modifiant ses propriétés. Les ID de message utilisés dans ce code sont déjà définis dans le menu pour 1.0 de dessin à main levée.  
  
4.  Dans la vue conception, cliquez sur le bouton d’Application pour afficher ses propriétés. Modifier les valeurs de propriété comme suit : **Image** à *IDB_RIBBON_MAIN*, **invite** à *fichier*, **clés** pour *f*, **grandes Images** à *IDB_RIBBON_FILELARGE*, et **petites Images** à *IDB_RIBBON_ FILESMALL*.  
  
5.  Les modifications suivantes créer le menu qui s’affiche lorsque l’utilisateur clique sur le bouton d’Application. Cliquez sur le bouton de sélection (**...** ) à côté **principal éléments** pour ouvrir le **Éditeur d’éléments**.  
  
    1.  Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à *& nouveau*, **ID** à *ID_FILE_NEW*, **Image** à *0*, **Image grande** à *0*.  
  
    2.  Cliquez sur **ajouter** pour ajouter un deuxième bouton. Modification **légende** à *& Enregistrer*, **ID** à *ID_FILE_SAVE*, **Image** à *2* , et **Image grande** à *2*.  
  
    3.  Cliquez sur **ajouter** pour ajouter un bouton de tiers. Modification **légende** à *en & registrer sous*, **ID** à *ID_FILE_SAVE_AS*, **Image** à *3*, et **Image grande** à *3*.  
  
    4.  Cliquez sur **ajouter** pour ajouter un quatrième bouton. Modification **légende** à *& Imprimer*, **ID** à *ID_FILE_PRINT*, **Image** à *4* , et **Image grande** à *4*.  
  
    5.  Modifier la **élément** type **séparateur** puis cliquez sur **ajouter**.  
  
    6.  Modifier la **élément** type **bouton**. Cliquez sur **ajouter** pour ajouter un cinquième bouton. Modification **légende** à *& fermer*, **ID** à *ID_FILE_CLOSE*, **Image** à *5* , et **Image grande** à *5*.  
  
6.  Les modifications suivantes créer un sous-menu sous le bouton d’impression que vous avez créé à l’étape précédente.  
  
    1.  Cliquez sur le **impression** bouton, remplacez le **élément** type **étiquette**, puis cliquez sur **insérer**. Modification **légende** à *afficher un aperçu et imprimer le document*.  
  
    2.  Cliquez sur le **impression** bouton, remplacez le **élément** type **bouton**et cliquez sur **insérer**. Modification **légende** à *& Imprimer*, **ID** à *ID_FILE_PRINT*, **Image** à *4* , et **Image grande** à *4*.  
  
    3.  Cliquez sur le **impression** puis cliquez sur **insérer** pour ajouter un bouton. Modification **légende** à *& rapide impression*, **ID** à *ID_FILE_PRINT_DIRECT*, **Image** à *7*, et **Image grande** à *7*.  
  
    4.  Cliquez sur le **impression** puis cliquez sur **insérer** pour ajouter un autre bouton. Modification **légende** à *impression Aperç & u*, **ID** à *ID_FILE_PRINT_PREVIEW*, **Image** à *6*, et **Image grande** à *6*.  
  
    5.  Vous avez modifié le **principal éléments**. Cliquez sur **fermer** pour quitter le **Éditeur d’éléments**.  
  
7.  La modification suivante crée un bouton de sortie qui s’affiche en bas du menu bouton Application.  
  
    1.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) à côté **bouton** pour ouvrir le **Éditeur d’éléments**.  
  
    2.  Cliquez sur **ajouter** pour ajouter un bouton. Modification **légende** à *& quitter*, **ID** à *ID_APP_EXIT*, **Image** à *8* .  
  
 [[Sections](#top)]  
  
##  <a name="createinstance"></a> Création d’une Instance de la barre du ruban  
 Les étapes suivantes montrent comment créer une instance de la barre du ruban au démarrage de votre application. Pour ajouter une barre de ruban à une application, déclarez la barre du ruban dans le fichier mainfrm.h. Puis, dans le fichier mainfrm.cpp, écrire du code pour charger la ressource de ruban.  
  
#### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Pour créer une instance de la barre du ruban  
  
1.  Dans le fichier mainfrm.h, ajouter un membre de données à la section protégée de `CMainFrame`, la définition de classe pour le frame principal. Ce membre représente la barre du ruban.  
  
 ''' * / / Ruban barre d’application  
    CMFCRibbonBar m_wndRibbonBar ;  
 ```  
  
2.  In the mainfrm.cpp file, add the following code before the final **return** statement at the end of the `CMainFrame::OnCreate` function. This creates an instance of the ribbon bar.  
  
 ``` *// Create the ribbon bar  
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
>  Cette procédure pas à pas utilise la même icône du Panneau de configuration pour tous les panneaux. Toutefois, vous pouvez utiliser tout autre index de liste d’images pour afficher d’autres icônes.  
  
#### <a name="to-add-a-home-category-and-edit-panel"></a>Pour ajouter une catégorie d’accueil et de modifier le panneau de configuration  
  
1.  Le programme de dessin à main levée ne requiert qu’une seule catégorie. Dans la vue de conception, cliquez sur **catégorie** pour afficher ses propriétés. Modifier les valeurs de propriété comme suit : **légende** à *& accueil*, **grandes Images** à *IDB_RIBBON_HOMELARGE*,  **Petites Images** à *IDB_RIBBON_HOMESMALL*.  
  
2.  Chaque catégorie de ruban s’articule autour des panneaux nommées. Chaque panneau contient un ensemble de contrôles qui effectuent des opérations connexes. Cette catégorie contient un panneau de configuration. Cliquez sur **panneau**, puis modifiez **légende** à *modifier* et **Index d’images** à *0*.  
  
3.  Pour le **modifier** du panneau, ajouter un bouton qui est responsable de l’effacement du contenu du document. L’ID de message pour ce bouton a déjà été défini dans la ressource de menu IDR_SCRIBBTYPE. Spécifiez *Effacer tout* comme texte du bouton et de l’index de la bitmap qui décore le bouton. Ouvrez le **boîte à outils**, puis faites glisser un **bouton** à la **modifier** Panneau de configuration. Cliquez sur le bouton et redéfinissez **légende** à *Effacer tout*, **ID** à *ID_EDIT_CLEAR_ALL*, **Indexd’images** à *0*, **grande Image Index** à *0*.  
  
4.  Enregistrer les modifications, puis créer et exécuter l’application. L’application Scribble doit être affichée, et elle doit avoir une barre de ruban en haut de la fenêtre au lieu d’une barre de menus. La barre du ruban doit avoir une catégorie, **accueil**, et **accueil** doit avoir un panneau de configuration, **modifier**. Les boutons de ruban que vous avez ajoutés doivent être associées avec les gestionnaires d’événements existants et le **ouvrir**, **fermer**, **enregistrer**, **Print**, et **Effacer tout** boutons doivent fonctionner comme prévu.  
  
 [[Sections](#top)]  
  
##  <a name="setlook"></a> Définir l’apparence de l’Application  
 A *Gestionnaire visuel* est un objet global qui contrôle tout le dessin d’une application. Étant donné que l’application Scribble d’origine utilise le style d’interface utilisateur d’utilisateur Office 2000, l’application peut ressembler traditionnelle. Vous pouvez réinitialiser l’application pour utiliser le Gestionnaire visuel Office 2007 afin qu’il ressemble à une application Office 2007.  
  
#### <a name="to-set-the-look-of-the-application"></a>Pour définir l’apparence de l’application  
  
1.  Dans la `CMainFrame::OnCreate` de fonction, tapez le code suivant pour modifier la valeur par défaut Gestionnaire visuel et le style.  
  
 ''' * / / Définir le gestionnaire par défaut pour Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007)) ;

 CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue) ;

 ```  
  
2.  Save the changes, and then build and run the application. The application UI should resemble the Office 2007 UI.  
  
 [[Sections](#top)]  
  
## Next Steps  
 You have modified the classic Scribble 1.0 MFC sample to use the Ribbon Designer. Now go to [Part 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)

