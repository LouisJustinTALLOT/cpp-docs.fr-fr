---
title: 'Contrôles ActiveX MFC : Ajout d’une autre propriété personnalisée Page | Microsoft Docs'
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
ms.openlocfilehash: ce81436781a92c8d2c9156e1d1c02513c3816dc4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440054"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées

Parfois, un contrôle ActiveX ont plusieurs propriétés que peut contenir une seule page de propriétés. Dans ce cas, vous pouvez ajouter des pages de propriétés pour le contrôle ActiveX pour afficher ces propriétés.

Cet article traite de l’ajout de nouvelles pages de propriétés à un contrôle ActiveX qui possède déjà au moins une page de propriétés. Pour plus d’informations sur l’ajout de propriétés stock pages (police, image ou couleur), consultez l’article [contrôles ActiveX MFC : Pages de propriétés Stock à l’aide de](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Les procédures suivantes utilisent un exemple d’infrastructure de contrôle ActiveX créée par l’Assistant contrôle ActiveX. Par conséquent, les noms de classe et les identificateurs sont uniques pour cet exemple.

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : pages de propriétés](../mfc/mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Il est fortement recommandé cette nouvelle propriété pages adhèrent à la taille standard pour les pages de propriétés du contrôle ActiveX. La propriété stock de l’image et la couleur des unités de boîte de dialogue de mesure 250 x 62 (DLU) pages. La page de propriétés de police standard est de 250 x 110 DLU. La page de propriétés par défaut créée par l’Assistant contrôle ActiveX utilise la norme DLU 250 x 62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Pour insérer un nouveau modèle de page de propriété dans votre projet

1. Avec votre projet de contrôle ouvert, ouvrez l’affichage des ressources dans l’espace de travail du projet.

1. Avec le bouton droit dans l’affichage des ressources pour ouvrir le menu contextuel et cliquez sur **ajouter une ressource**.

1. Développez le **boîte de dialogue** nœud, puis sélectionnez **IDD_OLE_PROPPAGE_SMALL**.

1. Cliquez sur **New** pour ajouter la ressource à votre projet.

1. Sélectionnez le nouveau modèle de page de propriété pour actualiser la fenêtre Propriétés.

1. Entrez une nouvelle valeur pour le **ID** propriété. Cet exemple utilise **IDD_PROPPAGE_NEWPAGE**.

1. Cliquez sur **enregistrer** sur la barre d’outils.

### <a name="to-associate-the-new-template-with-a-class"></a>Pour associer le nouveau modèle à une classe

1. Ouvrez l’affichage de classes.

1. Avec le bouton droit dans l’affichage de classes pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une classe**.

     Cette opération ouvre le [ajouter une classe](../ide/add-class-dialog-box.md) boîte de dialogue.

1. Double-cliquez sur le **classe MFC** modèle.

1. Dans le **nom de la classe** zone le [Assistant classe MFC](../mfc/reference/mfc-add-class-wizard.md), tapez un nom pour la nouvelle classe de boîte de dialogue. (Dans cet exemple, `CAddtlPropPage`.)

1. Si vous souhaitez modifier les noms de fichiers, cliquez sur **modifier**. Tapez les noms de vos fichiers d’en-tête et d’implémentation, ou acceptez les noms par défaut.

1. Dans le **une classe de Base** boîte, sélectionnez `COlePropertyPage`.

1. Dans le **ID de la boîte de dialogue** boîte, sélectionnez **IDD_PROPPAGE_NEWPAGE**.

9. Cliquez sur **Terminer** pour créer la classe.

Pour autoriser les utilisateurs du contrôle l’accès à cette nouvelle page de propriétés, apportez les modifications suivantes à la section de la macro d’ID du contrôle propriété page (située dans le fichier d’implémentation) :

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Notez que vous devez augmenter le deuxième paramètre de la macro BEGIN_PROPPAGEIDS (le nombre de pages de propriété) à partir de 1 à 2.

Vous devez également modifier le fichier d’implémentation (. Fichier CPP) pour inclure l’en-tête (. H) du fichier de la nouvelle classe de page de propriété.

L’étape suivante implique la création de deux nouvelles ressources de chaîne qui fournissent un nom de type et une légende pour la nouvelle page de propriétés.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Pour ajouter de nouvelles ressources de chaîne à une page de propriétés

1. Avec votre projet de contrôle ouvert, ouvrez l’affichage des ressources.

1. Double-cliquez sur le **Table de chaînes** dossier et double-cliquez sur la chaîne existante de table à laquelle vous souhaitez ajouter une chaîne de ressource.

     La table de chaînes s’ouvre dans une fenêtre.

1. Sélectionnez la ligne vide à la fin de la table de chaînes et tapez le texte, ou la légende, de la chaîne : par exemple, « propriété Page supplémentaire. »

     Cette opération ouvre un **propriétés de chaîne** affichage de page **légende** et **ID** boîtes. Le **légende** zone contient la chaîne que vous avez tapé.

1. Dans le **ID** zone, sélectionnez ou tapez un ID pour la chaîne. Lorsque vous avez terminé, appuyez sur ENTRÉE.

     Cet exemple utilise **IDS_SAMPLE_ADDPAGE** pour le nom de la nouvelle page de propriété.

1. Répétez les étapes 3 et 4 à l’aide de **IDS_SAMPLE_ADDPPG_CAPTION** pour l’ID et la « Page de propriétés supplémentaires » pour la légende.

1. Dans le. Fichier CPP de votre nouvelle classe de page de propriété (dans cet exemple, `CAddtlPropPage`) modifier la `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` afin que IDS_SAMPLE_ADDPAGE est passé par [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), comme dans l’exemple suivant :

     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifiez le constructeur de `CAddtlPropPage` afin qu’IDS_SAMPLE_ADDPPG_CAPTION au `COlePropertyPage` constructeur, comme suit :

     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Une fois que vous avez effectué les modifications nécessaires pour régénérer votre projet et utiliser un conteneur de Test pour tester la nouvelle page de propriétés. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

