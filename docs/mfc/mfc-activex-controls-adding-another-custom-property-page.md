---
title: "Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées"
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364741"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées

À l’occasion, un contrôle ActiveX aura plus de propriétés que ce qui peut raisonnablement s’adapter sur une page de propriété. Dans ce cas, vous pouvez ajouter des pages de propriété au contrôle ActiveX pour afficher ces propriétés.

Cet article traite de l’ajout de nouvelles pages de propriété à un contrôle ActiveX qui a déjà au moins une page de propriété. Pour plus d’informations sur l’ajout de pages de propriété stock (police, image, ou couleur), voir l’article [MFC ActiveX Controls: Using Stock Property Pages](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Les procédures suivantes utilisent un exemple de cadre de contrôle ActiveX créé par l’Assistant de Contrôle ActiveX. Par conséquent, les noms et les identificateurs de classe sont uniques à cet exemple.

Pour plus d’informations sur l’utilisation des pages de propriété dans un contrôle ActiveX, voir les articles suivants:

- [Contrôles ActiveX MFC : pages de propriétés](../mfc/mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Il est fortement recommandé que les nouvelles pages de propriété adhèrent à la norme de taille pour les pages de propriété de contrôle ActiveX. Les pages de l’image de stock et de la propriété de couleur mesurent 250x62 unités de dialogue (DLU). La page de propriété de police standard est 250x110 DLUs. La page propriété par défaut créée par l’ActiveX Control Wizard utilise la norme 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Pour insérer un nouveau modèle de page de propriété dans votre projet

1. Avec votre projet de contrôle ouvert, ouvrez Resource View dans l’espace de travail du projet.

1. Cliquez à droite dans Resource View pour ouvrir le menu raccourci et cliquez sur **Add Resource**.

1. Élargir le nœud **Dialog,** et sélectionner **IDD_OLE_PROPPAGE_SMALL**.

1. Cliquez **sur Nouveau** pour ajouter la ressource à votre projet.

1. Sélectionnez le nouveau modèle de page de propriété pour rafraîchir la fenêtre **propriété** (dans **Resource View**).

1. Entrez une nouvelle valeur pour la propriété **ID.** Cet exemple utilise **IDD_PROPPAGE_NEWPAGE**.

1. Cliquez sur **Save** dans la barre d'outils.

### <a name="to-associate-the-new-template-with-a-class"></a>Associer le nouveau modèle à une classe

1. Vue de classe ouverte.

1. Cliquez à droite dans Class View pour ouvrir le menu raccourci.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

   Cela ouvre la boîte de dialogue [Add Class.](../ide/add-class-dialog-box.md)

1. Double clic sur le modèle **de classe MFC.**

1. Dans la boîte **de nom de classe** dans le magicien de classe [MFC](../mfc/reference/mfc-add-class-wizard.md), tapez un nom pour la nouvelle classe de dialogue. (Dans cet `CAddtlPropPage`exemple, .)

1. Si vous souhaitez changer de nom de fichier, cliquez sur **Change**. Tapez les noms de vos fichiers d’implémentation et d’en-tête, ou acceptez les noms par défaut.

1. Dans la boîte de `COlePropertyPage`classe de **base,** sélectionnez .

1. Dans la boîte **d’identification Dialog,** sélectionnez **IDD_PROPPAGE_NEWPAGE**.

1. Cliquez sur **Finition** pour créer la classe.

Pour permettre aux utilisateurs du contrôle d’accéder à cette nouvelle page de propriété, apporter les modifications suivantes à la section macro des articles de propriété du contrôle (situé dans le fichier de mise en œuvre de contrôle) :

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Notez que vous devez augmenter le deuxième paramètre de la macro BEGIN_PROPPAGEIDS (le nombre de pages de propriété) de 1 à 2.

Vous devez également modifier le fichier de mise en œuvre de contrôle (. Fichier du RPC pour inclure l’en-tête (. H) fichier de la nouvelle classe de page de propriété.

L’étape suivante consiste à créer deux nouvelles ressources de chaîne qui fourniront un nom de type et une légende pour la nouvelle page de propriété.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Pour ajouter de nouvelles ressources de chaîne à une page de propriété

1. Avec votre projet de contrôle ouvert, ouvrez Resource View.

1. Double-cliquer sur le dossier **Table à cordes,** puis double-cliquez sur la ressource existante table de chaîne à laquelle vous souhaitez ajouter une chaîne.

   Cela ouvre la table de chaîne dans une fenêtre.

1. Sélectionnez la ligne blanche à la fin de la table à cordes et tapez le texte, ou la légende, de la chaîne : par exemple, « Page de propriété supplémentaire ».

   Cela ouvre une page **Propriétés à cordes** montrant des boîtes **de légende** et **d’identification.** La boîte **caption** contient la ficelle que vous avez tapée.

1. Dans la boîte **d’identification,** sélectionnez ou tapez un ID pour la chaîne. Appuyez sur Entrez lorsque vous avez terminé.

   Cet exemple utilise **IDS_SAMPLE_ADDPAGE** pour le nom de type de la nouvelle page de propriété.

1. Répétez les étapes 3 et 4 à **l’aide de IDS_SAMPLE_ADDPPG_CAPTION** pour l’ID et la « page de propriété supplémentaire » pour la légende.

1. Dans le . Le fichier du RPC de votre nouvelle `CAddtlPropPage`classe `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` de page de propriété (dans cet exemple, ) modifient le de sorte que IDS_SAMPLE_ADDPAGE soit passé par [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), comme dans l’exemple suivant :

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifier le constructeur `CAddtlPropPage` de sorte que IDS_SAMPLE_ADDPPG_CAPTION est `COlePropertyPage` passé au constructeur, comme suit:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Une fois que vous avez apporté les modifications nécessaires, reconstruisez votre projet et utilisez Test Container pour tester la nouvelle page de propriété. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
