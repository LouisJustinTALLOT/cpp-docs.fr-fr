---
title: "Procédure pas à pas : création d'une application de ruban à l'aide de MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: 16413b6027a36ec550ae2bf3e04604b32a8454c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557489"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Procédure pas à pas : création d'une application de ruban à l'aide de MFC

Cette procédure pas à pas montre comment utiliser le **Assistant Application MFC** pour créer une application comportant un ruban par défaut. Vous pouvez ensuite développer le ruban en ajoutant un **personnalisé** catégorie de ruban qui a un **favoris** ruban du Panneau de configuration et l’ajout de certaines commandes au panneau fréquemment utilisées.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas suppose que vous avez défini Visual Studio à utiliser **paramètres de développement généraux**. Si vous utilisez des paramètres différents, il se peut que certains éléments de l’utilisateur interface (UI) qui sont référencés dans les instructions suivantes peuvent ne pas afficher.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Pour créer une application MFC comportant un ruban

1. Utilisez le **Assistant Application MFC** pour créer une application MFC comportant un ruban. Pour exécuter l’Assistant, dans le **fichier** menu, pointez sur **New**, puis cliquez sur **projet**.

1. Dans le **nouveau projet** boîte de dialogue, développez le **Visual C++** nœud sous **modèles installés**, sélectionnez **MFC**, puis sélectionnez  **Application MFC**. Tapez un nom pour le projet, par exemple, *MFCRibbonApp*, puis cliquez sur **OK**.

1. Définir les options suivantes le **Assistant Application MFC**:

    1. Dans le **Type d’Application** section sous **style visuel et couleurs**, sélectionnez **Office 2007 (thème Blue)**.

    1. Dans le **prise en charge des documents composés** section, assurez-vous que l’option **aucun** est sélectionné.

    1. Dans le **propriétés du modèle de Document** section, dans le **extension de fichier** , tapez une extension de nom de fichier pour les documents créés par cette application, par exemple, *mfcrbnapp*.

    1. Dans le **prise en charge de la base de données** section, assurez-vous que l’option **aucun** est sélectionné.

    1. Dans le **fonctionnalités d’Interface utilisateur** section, assurez-vous que l’option **utiliser un ruban** est sélectionné.

    1. Par défaut, le **Assistant Application MFC** ajoute la prise en charge de plusieurs volets d’ancrage. Cette procédure pas à pas ne concernant que le ruban, vous pouvez supprimer ces options de l'application. Dans le **fonctionnalités avancées** section, désactivez toutes les options.

1. Cliquez sur **Terminer** pour créer l’application MFC.

1. Pour vérifier que l'application a été créée avec succès, générez-la et exécutez-la. Pour générer l’application, dans le **Build** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez-la en cliquant sur **démarrer le débogage** sur le **déboguer** menu.

    L’Assistant crée automatiquement un ruban comportant une catégorie de ruban nommée **accueil**. Ce ruban contient trois volets de ruban, qui sont nommés **Presse-papiers**, **vue**, et **fenêtre**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Pour ajouter une catégorie et un volet au ruban

1. Pour ouvrir la ressource de ruban créée par l’Assistant, dans le **vue** menu, pointez sur **Windows autres** puis cliquez sur **affichage des ressources**. Dans **affichage des ressources**, cliquez sur **ruban** , puis double-cliquez sur **IDR_RIBBON**.

1. Tout d’abord, ajoutez une catégorie personnalisée au ruban en double-cliquant sur **catégorie** dans le **boîte à outils**.

    A catégorie comportant la légende **Category1** est créé. Par défaut, la catégorie contient un seul volet.

    Avec le bouton droit **Category1** puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, modification **légende** à *personnalisé*.

    Le **grandes Images** et **petites Images** propriétés spécifient les bitmaps qui sont utilisés comme icônes pour les éléments de ruban dans cette catégorie. La création de bitmaps personnalisées n'entrant pas dans le cadre de cette procédure, réutilisez les bitmaps créées par l'Assistant. Les bitmaps de petite taille mesurent 16 pixels par 16 pixels. Pour les petites images, utilisez les bitmaps qui sont accessibles par le `IDB_FILESMALL` ID de ressource. Les bitmaps de grande taille mesurent 32 pixels par 32 pixels. Pour les grandes images, utilisez les bitmaps qui sont accessibles par le `IDB_FILELARGE` ID de ressource.

    > [!NOTE]
    > Sur les écrans HDPI (high dots per inch), les versions HDPI des images sont automatiquement utilisées.

1. Il vous appartient maintenant de personnaliser le volet. Les volets sont utilisés pour regrouper des éléments qui sont liés de façon logique les uns aux autres. Par exemple, sur le **accueil** onglet de cette application, le **couper**, **copie**, et **coller** commandes se trouvent sur le  **Presse-papiers** Panneau de configuration. Pour personnaliser le panneau de configuration, avec le bouton droit **Panel1** puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, modification **légende** à *favoris*.

    Vous pouvez spécifier le **Index d’Image** pour le panneau. Ce nombre spécifie l’icône qui s’affiche si le volet du ruban est ajouté à la **une barre d’outils Accès rapide**. L’icône n’est pas affichée dans le panneau de ruban lui-même.

1. Pour vérifier que le volet et la catégorie de ruban ont été correctement créés, affichez un aperçu du contrôle de ruban. Sur le **barre d’outils Éditeur Ribbon**, cliquez sur le **Test ruban** bouton. Un **personnalisé** onglet et **favoris** panneau doit être affiché sur le ruban.

### <a name="to-add-elements-to-the-ribbon-panels"></a>Pour ajouter des éléments aux volets de ruban

1. Pour ajouter des éléments au panneau que vous avez créé dans la procédure précédente, faites glisser des contrôles à partir de la **éditeur Ribbon** section de la **boîte à outils** au panneau en mode design.

1. Tout d’abord, ajoutez un **impression** bouton. Le **impression** bouton aura un sous-menu contenant un **impression rapide** commande à l’aide de l’imprimante par défaut. Ces deux commandes sont déjà définies pour cette application. Ils se trouvent dans le menu de l’application.

    Pour créer le **impression** bouton, faites glisser un outil bouton vers le panneau.

    Dans le **propriétés** fenêtre, modifier le **ID** propriété **ID_FILE_PRINT**, qui doit déjà être définis. Modification **légende** à *impression*. Modification **Image Index** à *4*.

    Pour créer le **impression rapide** bouton, cliquez sur la colonne de valeur de propriété en regard **des éléments de Menu**, puis cliquez sur le bouton de sélection (**...** ). Dans le **Éditeur d’éléments**, cliquez sur le sans étiquette **ajouter** bouton pour créer un élément de menu. Dans le **propriétés** fenêtre, modification **légende** à *impression rapide*, **ID** à *ID_FILE_PRINT_DIRECT*, et **Image** à *5*. Spécifie la propriété image le **impression rapide** icône dans le `IDB_FILESMALL` bitmap de ressource.

1. Pour vérifier que les boutons ont été ajoutés au volet du ruban, générez l'application et exécutez-la. Pour générer l’application, dans le **Build** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **démarrer le débogage** sur le **déboguer** menu. Le **impression** bouton et la liste déroulante zone sur le **favoris** panneau sur le **personnalisé** onglet sur le ruban doit être affiché.

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique pour personnaliser la barre d’outils Accès rapide](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Guide pratique pour personnaliser le bouton Application](../mfc/how-to-customize-the-application-button.md)

Pour obtenir des exemples de bout en bout, consultez [exemples (MFC Feature Pack)](../visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Exemples (MFC Feature Pack)](../visual-cpp-samples.md)
