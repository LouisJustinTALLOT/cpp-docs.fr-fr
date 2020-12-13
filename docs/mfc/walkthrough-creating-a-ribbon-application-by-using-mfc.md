---
description: 'En savoir plus sur : procédure pas à pas : création d’une application de ruban à l’aide de MFC'
title: "Procédure pas à pas : création d'une application de ruban à l'aide de MFC"
ms.date: 09/09/2019
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon application (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: fa266900c52d7d8ca3460ca38b266571974d1563
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143063"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Procédure pas à pas : création d'une application de ruban à l'aide de MFC

Cette procédure pas à pas montre comment utiliser l' **Assistant Application MFC** pour créer une application qui a un ruban par défaut. Vous pouvez ensuite développer le ruban en ajoutant une catégorie de ruban **personnalisée** qui contient un panneau de ruban **favoris** , puis en ajoutant des commandes fréquemment utilisées au panneau.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas suppose que vous avez configuré Visual Studio pour utiliser les **paramètres de développement généraux**. Si vous utilisez des paramètres différents, certains éléments de l’interface utilisateur référencés dans les instructions suivantes peuvent ne pas s’afficher.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Pour créer une application MFC comportant un ruban

1. Utilisez l **'Assistant Application MFC** pour créer une application MFC qui possède un ruban. Consultez [procédure pas à pas : utilisation des nouveaux contrôles de l’interpréteur de commandes MFC](walkthrough-using-the-new-mfc-shell-controls.md) pour obtenir des instructions sur l’ouverture de l’Assistant pour votre version de Visual Studio.

1. Définissez les options suivantes dans l' **Assistant Application MFC**:

    1. Dans la section **type d’application** , sous **style visuel et couleurs**, sélectionnez **Office 2007 (thème Blue)**.

    1. Dans la section **prise en charge des documents composés** , assurez-vous qu' **aucun élément** n’est sélectionné.

    1. Dans la zone **extension de fichier** de la section Propriétés du **modèle de document** , tapez une extension de nom de fichier pour les documents créés par cette application, par exemple, *mfcrbnapp*.

    1. Dans la section **prise en charge de la base de données** (Visual Studio 2015 uniquement), assurez-vous qu' **aucun** n’est sélectionné.

    1. Dans la section fonctionnalités de l' **interface utilisateur** , assurez-vous que l’option **utiliser un ruban** est sélectionnée.

    1. Par défaut, l' **Assistant Application MFC** ajoute la prise en charge de plusieurs volets d’ancrage. Cette procédure pas à pas ne concernant que le ruban, vous pouvez supprimer ces options de l'application. Dans la section **fonctionnalités avancées** , désactivez toutes les options.

1. Cliquez sur **Terminer** pour créer l’application MFC.

1. Pour vérifier que l'application a été créée avec succès, générez-la et exécutez-la. Pour générer l’application, dans le menu **générer** , cliquez sur **générer la solution**. Si l’application est générée avec succès, exécutez-la en cliquant sur **Démarrer le débogage** dans le menu **Déboguer** .

    L’Assistant crée automatiquement un ruban qui a une catégorie de ruban nommée **page d’hébergement**. Ce ruban contient trois panneaux du ruban, nommés **presse-papiers**, **affichage** et **fenêtre**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Pour ajouter une catégorie et un volet au ruban

1. Pour ouvrir la ressource de ruban que l’Assistant a créée, dans le menu **affichage** , pointez sur **autres fenêtres** , puis cliquez sur **affichage des ressources**. Dans **affichage des ressources**, cliquez sur **ruban** , puis double-cliquez sur **IDR_RIBBON**.

1. Tout d’abord, ajoutez une catégorie personnalisée au ruban en double-cliquant sur **catégorie** dans la **boîte à outils**.

    Une catégorie avec la légende **Category1** est créée. Par défaut, la catégorie contient un seul volet.

    Cliquez avec le bouton droit sur **Category1** , puis cliquez sur **Propriétés**. Dans la fenêtre **Propriétés** , remplacez la **légende** par *personnalisé*.

    Les propriétés **grandes images** et **petites images** spécifient les bitmaps qui sont utilisées comme icônes pour les éléments de ruban dans cette catégorie. La création de bitmaps personnalisées n'entrant pas dans le cadre de cette procédure, réutilisez les bitmaps créées par l'Assistant. Les bitmaps de petite taille mesurent 16 pixels par 16 pixels. Pour les petites images, utilisez les bitmaps qui sont accessibles par l' `IDB_FILESMALL` ID de ressource. Les bitmaps de grande taille mesurent 32 pixels par 32 pixels. Pour les images de grande taille, utilisez les bitmaps qui sont accessibles par l' `IDB_FILELARGE` ID de ressource.

    > [!NOTE]
    > Sur les écrans HDPI (high dots per inch), les versions HDPI des images sont automatiquement utilisées.

1. Il vous appartient maintenant de personnaliser le volet. Les volets sont utilisés pour regrouper des éléments qui sont liés de façon logique les uns aux autres. Par exemple, sous l’onglet dossier de **démarrage** de cette application, les commandes **couper**, **copier** et **coller** se trouvent toutes dans le panneau **presse-papiers** . Pour personnaliser le volet, cliquez avec le bouton droit sur **Panel1** , puis cliquez sur **Propriétés**. Dans la fenêtre **Propriétés** , remplacez la **légende** par *favoris*.

    Vous pouvez spécifier l' **index d’image** pour le panneau. Ce nombre spécifie l’icône qui s’affiche si le panneau du ruban est ajouté à la **barre d’outils accès rapide**. L’icône ne s’affiche pas sur le panneau du ruban lui-même.

1. Pour vérifier que le volet et la catégorie de ruban ont été correctement créés, affichez un aperçu du contrôle de ruban. Dans la **barre d’outils** de l’éditeur de ruban, cliquez sur le bouton **tester le ruban** . Un onglet **personnalisé** et un volet **favoris** doivent s’afficher sur le ruban.

### <a name="to-add-elements-to-the-ribbon-panels"></a>Pour ajouter des éléments aux volets de ruban

1. Pour ajouter des éléments au panneau que vous avez créé au cours de la procédure précédente, faites glisser les contrôles de la section **éditeur de ruban** de la **boîte à outils** vers le volet en mode Design.

1. Tout d’abord, ajoutez un bouton **Imprimer** . Le bouton **Imprimer** contient un sous-menu contenant une commande d' **impression rapide** qui s’imprime en utilisant l’imprimante par défaut. Ces deux commandes sont déjà définies pour cette application. Ils sont situés dans le menu de l’application.

    Pour créer le bouton **Imprimer** , faites glisser un outil bouton sur le panneau.

    Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **ID** par **ID_FILE_PRINT**, qui doit déjà être définie. Remplacez la **légende** par *Imprimer*. Remplacez **index image** par *4*.

    Pour créer le bouton **impression rapide** , cliquez sur la colonne valeur de la propriété en regard de **éléments de menu**, puis cliquez sur les points de suspension (**...**). Dans l' **éditeur d’éléments**, cliquez sur le bouton **Ajouter** sans étiquette pour créer un élément de menu. Dans la fenêtre **Propriétés** , remplacez **la légende** par *impression rapide*, **ID** par *ID_FILE_PRINT_DIRECT* et **image** par *5*. La propriété image spécifie l’icône d' **impression rapide** dans la `IDB_FILESMALL` ressource bitmap.

1. Pour vérifier que les boutons ont été ajoutés au volet du ruban, générez l'application et exécutez-la. Pour générer l’application, dans le menu **générer** , cliquez sur **générer la solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **Démarrer le débogage** dans le menu **Déboguer** . Le bouton **Imprimer** et la zone de liste déroulante du panneau **favoris** de l’onglet **personnalisé** sur le ruban doivent s’afficher.

## <a name="next-steps"></a>Étapes suivantes

[Comment : personnaliser la barre d’outils accès rapide](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Comment : personnaliser le bouton de l’application](../mfc/how-to-customize-the-application-button.md)

Pour obtenir des exemples de bout en bout, consultez [exemples (Feature Pack MFC)](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Exemples (Feature Pack MFC)](../overview/visual-cpp-samples.md)
