---
title: 'Procédure pas à pas : Création d’une Application de ruban à l’aide de MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f715830c110f03811202d2e98dc097bfe712208
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Procédure pas à pas : création d'une application de ruban à l'aide de MFC
Cette procédure pas à pas montre comment utiliser le **Assistant Application MFC** pour créer une application comportant un ruban par défaut. Vous pouvez ensuite développer le ruban en ajoutant un **personnalisé** catégorie de ruban qui a un **favoris** ruban du Panneau de configuration et en ajoutant ensuite quelques unes des commandes pour le panneau de configuration les plus utilisées.  
  
## <a name="prerequisites"></a>Prérequis  
 Cette procédure pas à pas suppose que vous avez défini [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] à utiliser **paramètres de développement généraux**. Si vous utilisez des paramètres différents, certains éléments de l'interface utilisateur qui sont référencés dans les instructions suivantes peuvent ne pas s'afficher. Pour plus d’informations sur la modification des paramètres, consultez [Comment : réinitialiser vos paramètres](http://msdn.microsoft.com/en-us/c95c51be-e609-4769-abba-65e6beedec76).  
  
### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Pour créer une application MFC comportant un ruban  
  
1.  Utilisez le **Assistant Application MFC** pour créer une application MFC comportant un ruban. Pour exécuter l’Assistant, dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C++** nœud sous **modèles installés**, sélectionnez **MFC**, puis sélectionnez  **Application MFC**. Tapez un nom pour le projet, par exemple, `MFCRibbonApp`, puis cliquez sur **OK**.  
  
3.  Sur la première page de la **Assistant Application MFC**, cliquez sur **suivant**.  
  
4.  Sur le **Type d’Application** sous **style visuel et couleurs**, sélectionnez **Office 2007 (thème Blue)**. Laissez les valeurs des autres paramètres inchangées. Cliquez sur **Suivant**.  
  
5.  Sur le **prise en charge des documents composés** , assurez-vous que **aucun** est sélectionné, puis cliquez sur **suivant**.  
  
6.  Sur le **propriétés du modèle de Document** page, dans le **extension de fichier** , tapez une extension de nom de fichier pour les documents créés par cette application, par exemple, `mfcrbnapp`. Cliquez sur **Suivant**.  
  
7.  Sur le **prise en charge de la base de données** , assurez-vous que **aucun** est sélectionné, puis cliquez sur **suivant**.  
  
8.  Sur le **fonctionnalités d’Interface utilisateur** , assurez-vous que **utilise un ruban** est sélectionnée. Cliquez sur **Suivant**.  
  
9. Par défaut, le **Assistant Application MFC** ajoute la prise en charge de plusieurs volets d’ancrage. Cette procédure pas à pas ne concernant que le ruban, vous pouvez supprimer ces options de l'application. Sur le **fonctionnalités avancées** page, effacez toutes les options. Cliquez sur **Suivant**.  
  
10. Sur le **Classes générées** , cliquez sur **Terminer** pour créer l’application MFC.  
  
11. Pour vérifier que l'application a été créée avec succès, générez-la et exécutez-la. Pour générer l’application, dans le **générer** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez-la en cliquant sur **démarrer le débogage** sur la **déboguer** menu.  
  
     L’Assistant crée automatiquement un ruban comportant une catégorie de ruban nommée **accueil**. Ce ruban contient trois volets de ruban qui sont nommées **Presse-papiers**, **vue**, et **fenêtre**.  
  
### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Pour ajouter une catégorie et un volet au ruban  
  
1.  Pour ouvrir la ressource de ruban que l’Assistant a créé, dans le **vue** menu, pointez sur **autres fenêtres** puis cliquez sur **affichage des ressources**. Dans **affichage des ressources**, cliquez sur **ruban** , puis double-cliquez sur **IDR_RIBBON**.  
  
2.  Tout d’abord, ajoutez une catégorie personnalisée au ruban en double-cliquant sur **catégorie** dans les **boîte à outils**.  
  
     Une catégorie qui a la légende **Category1** est créé. Par défaut, la catégorie contient un seul volet.  
  
     Avec le bouton droit **Category1** puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, modification **légende** à `Custom`.  
  
     Le **grandes Images** et **petites Images** propriétés spécifient les bitmaps qui sont utilisés comme icônes pour les éléments de ruban dans cette catégorie. La création de bitmaps personnalisées n'entrant pas dans le cadre de cette procédure, réutilisez les bitmaps créées par l'Assistant. Les bitmaps de petite taille mesurent 16 pixels par 16 pixels. Pour les petites images, utilisez les bitmaps qui sont accessibles par l'ID de ressource IDB_FILESMALL. Les bitmaps de grande taille mesurent 32 pixels par 32 pixels. Pour les grandes images, utilisez les bitmaps qui sont accessibles par l'ID de ressource IDB_FILELARGE.  
  
    > [!NOTE]
    >  Sur les écrans HDPI (high dots per inch), les versions HDPI des images sont automatiquement utilisées.  
  
3.  Il vous appartient maintenant de personnaliser le volet. Les volets sont utilisés pour regrouper des éléments qui sont liés de façon logique les uns aux autres. Par exemple, sur le **accueil** onglet de cette application, le **couper**, **copie**, et **coller** commandes se trouvent sur le  **Presse-papiers** Panneau de configuration. Pour personnaliser le panneau de configuration, avec le bouton droit **Panel1** puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, modification **légende** à `Favorites`.  
  
     Vous pouvez spécifier le **Index d’images** pour le panneau de configuration. Ce nombre indique l’icône qui s’affiche si le volet du ruban est ajouté à la **une barre d’outils Accès rapide**. L'icône n'est pas affichée sur le volet du ruban.  
  
4.  Pour vérifier que le volet et la catégorie de ruban ont été correctement créés, affichez un aperçu du contrôle de ruban. Sur le **barre d’outils Éditeur Ribbon**, cliquez sur le **Test ruban** bouton. A **personnalisé** onglet et **favoris** Panneau de configuration doit être affichée sur le ruban.  
  
### <a name="to-add-elements-to-the-ribbon-panels"></a>Pour ajouter des éléments aux volets de ruban  
  
1.  Pour ajouter des éléments dans le panneau de configuration que vous avez créé dans la procédure précédente, faites glisser les contrôles à partir de la **éditeur Ribbon** section de la **boîte à outils** pour le panneau de configuration en mode design.  
  
2.  Tout d’abord, ajoutez un **impression** bouton. Le **impression** bouton comporte un sous-menu contenant un **impression rapide** commande à l’aide de l’imprimante par défaut. Ces deux commandes sont déjà définies pour cette application. Elles se trouvent dans le menu de l'application.  
  
     Pour créer le **impression** bouton, faites glisser un outil bouton vers le panneau.  
  
     Dans le **propriétés** fenêtre, de modifier le **ID** propriété **ID_FILE_PRINT**, qui doit être défini. Modification **légende** à `Print`. Modification **Index de l’Image** à `4`.  
  
     Pour créer le **impression rapide** bouton, cliquez sur la colonne de valeur de propriété en regard **des éléments de Menu**, puis cliquez sur le bouton de sélection (**...** ). Dans le **Éditeur d’éléments**, cliquez sur le sans étiquette **ajouter** bouton permettant de créer un élément de menu. Dans le **propriétés** fenêtre, modification **légende** à `Quick Print`, **ID** à `ID_FILE_PRINT_DIRECT`, et **Image** à `5` . La propriété de l'image spécifie l'icône Impression rapide dans la ressource de bitmap IDB_FILESMALL.  
  
3.  Pour vérifier que les boutons ont été ajoutés au volet du ruban, générez l'application et exécutez-la. Pour générer l’application, dans le **générer** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez-la en cliquant sur **démarrer le débogage** sur la **déboguer** menu. Le **impression** bouton et la liste déroulante de zone sur le **favoris** panneau sur le **personnalisé** onglet du ruban doit être affiché.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Guide pratique pour personnaliser la barre d’outils Accès rapide](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Guide pratique pour personnaliser le bouton Application](../mfc/how-to-customize-the-application-button.md)  
  
 Pour obtenir des exemples de bout en bout, consultez [exemples (MFC Feature Pack)](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas](../mfc/walkthroughs-mfc.md)   
 [Exemples (MFC Feature Pack)](../visual-cpp-samples.md)

