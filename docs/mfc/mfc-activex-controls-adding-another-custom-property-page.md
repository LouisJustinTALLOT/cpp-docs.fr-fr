---
title: 'Contrôles ActiveX MFC : Ajout d’une autre propriété personnalisée Page | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9c3d9f4744ae01a7e251387bd342b77292d1c0d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931607"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées
Parfois, un contrôle ActiveX aura plus de propriétés que peut contenir une page de propriétés. Dans ce cas, vous pouvez ajouter des pages de propriétés pour le contrôle ActiveX pour afficher ces propriétés.  
  
 Cet article traite de l’ajout de nouvelles pages de propriétés à un contrôle ActiveX qui possède déjà au moins une page de propriétés. Pour plus d’informations sur l’ajout de propriétés stock pages (police, image ou couleur), consultez l’article [contrôles ActiveX MFC : Pages de propriétés Stock à l’aide de](../mfc/mfc-activex-controls-using-stock-property-pages.md).  
  
 Les procédures suivantes utilisent une infrastructure de contrôle ActiveX exemple créée par l’Assistant contrôle ActiveX. Par conséquent, les noms de classe et les identificateurs sont uniques à cet exemple.  
  
 Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :  
  
-   [Contrôles ActiveX MFC : pages de propriétés](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  Il est fortement recommandé que nouvelle propriété pages est conforme à la taille standard pour les pages de propriétés du contrôle ActiveX. Unités de boîte de dialogue mesure 250 x 62 (DLU) des pages de la propriété stock de couleurs et des images. La page de propriétés de police standard est 250 x 110 DLU. La page de propriétés par défaut créée par l’Assistant contrôle ActiveX utilise la norme DLU 250 x 62.  
  
### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Pour insérer un nouveau modèle de page de propriétés dans votre projet  
  
1.  Avec votre projet de contrôle ouvert, ouvrez l’affichage des ressources dans l’espace de travail du projet.  
  
2.  Avec le bouton droit dans l’affichage des ressources pour ouvrir le menu contextuel et cliquez sur **ajouter une ressource**.  
  
3.  Développez le **boîte de dialogue** nœud et sélectionnez **IDD_OLE_PROPPAGE_SMALL**.  
  
4.  Cliquez sur **nouveau** pour ajouter la ressource à votre projet.  
  
5.  Sélectionnez le nouveau modèle de page de propriété pour actualiser la fenêtre Propriétés.  
  
6.  Entrez une nouvelle valeur pour le **ID** propriété. Cet exemple utilise **IDD_PROPPAGE_NEWPAGE**.  
  
7.  Cliquez sur **enregistrer** sur la barre d’outils.  
  
### <a name="to-associate-the-new-template-with-a-class"></a>Pour associer le nouveau modèle à une classe  
  
1.  Ouvrez l’affichage de classes.  
  
2.  Avec le bouton droit dans l’affichage de classes pour ouvrir le menu contextuel.  
  
3.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une classe**.  
  
     Cette opération ouvre le [ajouter une classe](../ide/add-class-dialog-box.md) boîte de dialogue.  
  
4.  Double-cliquez sur le **classe MFC** modèle.  
  
5.  Dans le **nom de la classe** zone le [Assistant classe MFC](../mfc/reference/mfc-add-class-wizard.md), tapez un nom pour la nouvelle classe de boîte de dialogue. (Dans cet exemple, `CAddtlPropPage`.)  
  
6.  Si vous souhaitez modifier les noms de fichiers, cliquez sur **modifier**. Tapez les noms de vos fichiers d’en-tête et d’implémentation, ou acceptez les noms par défaut.  
  
7.  Dans le **une classe de Base** boîte, sélectionnez `COlePropertyPage`.  
  
8.  Dans le **ID de la boîte de dialogue** boîte, sélectionnez **IDD_PROPPAGE_NEWPAGE**.  
  
9. Cliquez sur **Terminer** pour créer la classe.  
  
 Pour autoriser les utilisateurs du contrôle l’accès à cette nouvelle page de propriétés, apportez les modifications suivantes à la section de la macro d’ID du contrôle propriété page (située dans le fichier d’implémentation) :  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 Notez que vous devez augmenter le deuxième paramètre de la macro BEGIN_PROPPAGEIDS (le nombre de pages de propriétés) à partir de 1 à 2.  
  
 Vous devez également modifier le fichier d’implémentation (. Fichier CPP) d’inclure l’en-tête (. H) du fichier de la nouvelle classe de page de propriété.  
  
 L’étape suivante implique la création de deux nouvelles ressources de chaîne qui fourniront un nom de type et une légende de la nouvelle page de propriétés.  
  
#### <a name="to-add-new-string-resources-to-a-property-page"></a>Pour ajouter de nouvelles ressources de chaînes à une page de propriétés  
  
1.  Ouvrez votre projet de contrôle, ouvrez l’affichage des ressources.  
  
2.  Double-cliquez sur le **Table de chaînes** dossier et double-cliquez sur la chaîne existante de table à laquelle vous souhaitez ajouter une chaîne de ressource.  
  
     La table de chaînes s’ouvre dans une fenêtre.  
  
3.  Sélectionnez la ligne vierge à la fin de la table de chaînes et tapez le texte ou la légende, de la chaîne : par exemple, « nouvelle Page de propriétés. »  
  
     S’ouvre un **propriétés de chaîne** affichage de page **légende** et **ID** cases. Le **légende** zone contient la chaîne que vous avez tapé.  
  
4.  Dans le **ID** zone, sélectionnez ou tapez un ID pour la chaîne. Lorsque vous avez terminé, appuyez sur ENTRÉE.  
  
     Cet exemple utilise **IDS_SAMPLE_ADDPAGE** pour le nom de la nouvelle page de propriétés.  
  
5.  Répétez les étapes 3 et 4 à l’aide de **IDS_SAMPLE_ADDPPG_CAPTION** pour l’ID et le « Page de propriété supplémentaires » pour la légende.  
  
6.  Dans le. Cpp de votre nouvelle classe de page de propriétés (dans cet exemple, `CAddtlPropPage`) modifier les `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` afin que IDS_SAMPLE_ADDPAGE est passé par [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), comme dans l’exemple suivant :  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  Modifiez le constructeur de `CAddtlPropPage` afin qu’IDS_SAMPLE_ADDPPG_CAPTION au `COlePropertyPage` constructeur, comme suit :  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 Après avoir apporté les modifications nécessaires régénérez votre projet et utilisez le conteneur de Test pour tester la nouvelle page de propriétés. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

