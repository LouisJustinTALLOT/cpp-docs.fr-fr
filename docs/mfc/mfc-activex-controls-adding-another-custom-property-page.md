---
description: 'En savoir plus sur : contrôles ActiveX MFC : ajout d’une autre page de propriétés personnalisée'
title: "Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées"
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 3802a32ed86536850e3a15ae9ce4bb53feb1ff1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203027"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées

Il arrive parfois qu’un contrôle ActiveX ait plus de propriétés que ne le contienne raisonnablement sur une page de propriétés. Dans ce cas, vous pouvez ajouter des pages de propriétés au contrôle ActiveX pour afficher ces propriétés.

Cet article explique comment ajouter de nouvelles pages de propriétés à un contrôle ActiveX qui possède déjà au moins une page de propriétés. Pour plus d’informations sur l’ajout de pages de propriétés stock (police, image ou couleur), consultez l’article [contrôles ActiveX MFC : utilisation des pages de propriétés stock](mfc-activex-controls-using-stock-property-pages.md).

Les procédures suivantes utilisent un exemple d’infrastructure de contrôle ActiveX créé par l’Assistant contrôle ActiveX. Par conséquent, les noms et les identificateurs de classe sont uniques à cet exemple.

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : pages de propriétés](mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Il est fortement recommandé que les nouvelles pages de propriétés adhèrent à la norme de taille pour les pages de propriétés de contrôle ActiveX. Les pages de propriétés image stock et couleur mesurent les unités de la boîte de dialogue 250x62 (DLU). La page de propriétés de police standard est 250x110. La page de propriétés par défaut créée par l’Assistant contrôle ActiveX utilise la norme 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Pour insérer un nouveau modèle de page de propriétés dans votre projet

1. Une fois votre projet de contrôle ouvert, ouvrez Affichage des ressources dans l’espace de travail du projet.

1. Cliquez avec le bouton droit dans Affichage des ressources pour ouvrir le menu contextuel, puis cliquez sur **Ajouter une ressource**.

1. Développez le nœud **boîte de dialogue** , puis sélectionnez **IDD_OLE_PROPPAGE_SMALL**.

1. Cliquez sur **nouveau** pour ajouter la ressource à votre projet.

1. Sélectionnez le nouveau modèle de page de propriétés pour actualiser la fenêtre **Propriétés** (dans **affichage des ressources**).

1. Entrez une nouvelle valeur pour la propriété **ID** . Cet exemple utilise **IDD_PROPPAGE_NEWPAGE**.

1. Cliquez sur **Save** dans la barre d'outils.

### <a name="to-associate-the-new-template-with-a-class"></a>Pour associer le nouveau modèle à une classe

1. Ouvrez Affichage de classes.

1. Cliquez avec le bouton droit dans Affichage de classes pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

   La boîte de dialogue [Ajouter une classe](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) s’ouvre.

1. Double-cliquez sur le modèle de **classe MFC** .

1. Dans la zone nom de la **classe** de l' [Assistant classe MFC](reference/mfc-add-class-wizard.md), tapez un nom pour la nouvelle classe de boîte de dialogue. (Dans cet exemple, `CAddtlPropPage` .)

1. Si vous souhaitez modifier les noms de fichiers, cliquez sur **modifier**. Tapez les noms de votre implémentation et des fichiers d’en-tête, ou acceptez les noms par défaut.

1. Dans la zone **classe de base** , sélectionnez `COlePropertyPage` .

1. Dans la zone **ID de boîte de dialogue** , sélectionnez **IDD_PROPPAGE_NEWPAGE**.

1. Cliquez sur **Terminer** pour créer la classe.

Pour autoriser les utilisateurs du contrôle à accéder à cette nouvelle page de propriétés, apportez les modifications suivantes à la section macro ID de la page de propriétés du contrôle (située dans le fichier d’implémentation du contrôle) :

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Notez que vous devez augmenter le deuxième paramètre de la macro BEGIN_PROPPAGEIDS (le nombre de pages de propriétés) de 1 à 2.

Vous devez également modifier le fichier d’implémentation du contrôle (. CPP) pour inclure l’en-tête (. H) de la nouvelle classe de page de propriétés.

L’étape suivante consiste à créer deux nouvelles ressources de type chaîne qui fourniront un nom de type et une légende pour la nouvelle page de propriétés.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Pour ajouter de nouvelles ressources de type chaîne à une page de propriétés

1. Une fois votre projet de contrôle ouvert, ouvrez Affichage des ressources.

1. Double-cliquez sur le dossier de la **table de chaînes** , puis double-cliquez sur la ressource de table de chaînes existante à laquelle vous souhaitez ajouter une chaîne.

   La table de chaînes est alors ouverte dans une fenêtre.

1. Sélectionnez la ligne vide à la fin de la table de chaînes et tapez le texte ou la légende de la chaîne : par exemple, « page de propriétés supplémentaire ».

   Cela ouvre une page de **Propriétés de chaîne** qui affiche des zones de **légende** et d' **ID** . La zone **légende** contient la chaîne que vous avez tapée.

1. Dans la zone **ID** , sélectionnez ou tapez un ID pour la chaîne. Appuyez sur entrée lorsque vous avez terminé.

   Cet exemple utilise **IDS_SAMPLE_ADDPAGE** pour le nom de type de la nouvelle page de propriétés.

1. Répétez les étapes 3 et 4 en utilisant **IDS_SAMPLE_ADDPPG_CAPTION** pour l’ID et la « page de propriétés supplémentaire » pour la légende.

1. Dans le. Fichier CPP de votre nouvelle classe de page de propriétés (dans cet exemple, `CAddtlPropPage` ) modifiez le `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` afin que IDS_SAMPLE_ADDPAGE soit passé par [AfxOleRegisterPropertyPageClass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass), comme dans l’exemple suivant :

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifiez le constructeur de `CAddtlPropPage` afin que IDS_SAMPLE_ADDPPG_CAPTION soit passé au `COlePropertyPage` constructeur, comme suit :

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Une fois que vous avez effectué les modifications nécessaires, régénérez votre projet et utilisez le conteneur de test pour tester la nouvelle page de propriétés. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
