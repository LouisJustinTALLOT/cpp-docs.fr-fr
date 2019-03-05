---
title: 'Contrôles ActiveX MFC : Pages de propriétés'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 3fe092e412cf11f7bf8600e8d0d7d43abb0e11c7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303896"
---
# <a name="mfc-activex-controls-property-pages"></a>Contrôles ActiveX MFC : Pages de propriétés

Pages de propriétés permettent à un utilisateur du contrôle ActiveX afficher et modifier les propriétés du contrôle ActiveX. Ces propriétés sont accessibles en appelant une boîte de dialogue Propriétés du contrôle, qui contient un ou plusieurs pages de propriétés qui fournissent une interface graphique personnalisée pour afficher et modifier les propriétés du contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Pages de propriétés du contrôle ActiveX sont affichés de deux manières :

- Lors de verbe de propriétés du contrôle (**OLEIVERB_PROPERTIES**) est appelé, le contrôle ouvre une boîte de dialogue de propriétés modale qui contient les pages de propriétés du contrôle.

- Le conteneur peut afficher sa propre boîte de dialogue non modale qui affiche les pages de propriétés du contrôle sélectionné.

La boîte de dialogue de propriétés (illustrée dans la figure suivante) se compose d’une zone pour afficher des onglets pour basculer entre les pages de propriétés et une collection de boutons qui effectuent des tâches courantes telles que la fermeture de la boîte de dialogue page de propriété, la page de propriétés en cours, annulation des modifications effectuées, ou appliquer immédiatement des modifications au contrôle ActiveX.

![Boîte de dialogue de propriétés pour Circ3](../mfc/media/vc373i1.gif "boîte de dialogue de propriétés pour Circ3") <br/>
Boîte de dialogue Propriétés

Cet article traite des rubriques liées à l’utilisation des pages de propriétés dans un contrôle ActiveX. Elles incluent notamment :

- [Implémentation de la page de propriété par défaut pour un contrôle ActiveX](#_core_implementing_the_default_property_page)

- [Ajout de contrôles à une page de propriétés](#_core_adding_controls_to_a_property_page)

- [Personnalisation de la fonction DoDataExchange](#_core_customizing_the_dodataexchange_function)

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : Ajout d’une autre Page de propriétés personnalisées](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [Contrôles ActiveX MFC : À l’aide des Pages de propriétés Stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Pour plus d’informations sur l’utilisation des feuilles de propriétés dans une application MFC autre qu’un contrôle ActiveX, consultez [feuilles de propriétés](../mfc/property-sheets-mfc.md).

##  <a name="_core_implementing_the_default_property_page"></a> Implémentation de la Page de propriété par défaut

Si vous utilisez l’Assistant contrôle ActiveX pour créer votre projet de contrôle, l’Assistant contrôle ActiveX fournit une classe de page de propriétés par défaut pour le contrôle dérivé [COlePropertyPage, classe](../mfc/reference/colepropertypage-class.md). Initialement, cette page de propriétés est vide, mais vous pouvez ajouter n’importe quel contrôle de boîte de dialogue ou un ensemble de contrôles à ce dernier. Étant donné que l’Assistant contrôle ActiveX crée la classe de page qu’une seule propriété par défaut, les classes de page de propriété supplémentaires (également dérivée de `COlePropertyPage`) doit être créé à l’aide d’affichage de classes. Pour plus d’informations sur cette procédure, consultez [contrôles ActiveX MFC : Ajout d’une autre Page de propriété personnalisée](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

Implémentation d’une propriété page (dans ce cas, la valeur par défaut) est un processus en trois étapes :

#### <a name="to-implement-a-property-page"></a>Pour implémenter une page de propriétés

1. Ajouter un `COlePropertyPage`-classe dérivée au projet de contrôle. Si le projet a été créé à l’aide de l’Assistant contrôle ActiveX (comme dans ce cas), la classe de page de propriété par défaut existe déjà.

1. Utilisez l’éditeur de boîtes de dialogue pour ajouter des contrôles au modèle de page de propriété.

1. Personnaliser le `DoDataExchange` fonction de la `COlePropertyPage`-classe pour échanger des valeurs entre le contrôle de page de propriété et le contrôle ActiveX dérivée.

Par exemple à des fins, les procédures suivantes utilisent un contrôle simple (nommé « Exemple »). Exemple a été créé à l’aide de l’Assistant contrôle ActiveX et contient uniquement la propriété Caption de stock.

##  <a name="_core_adding_controls_to_a_property_page"></a> Ajout de contrôles à une Page de propriétés

#### <a name="to-add-controls-to-a-property-page"></a>Pour ajouter des contrôles à une page de propriétés

1. Avec votre projet de contrôle ouvert, ouvrez l’affichage des ressources.

1. Double-cliquez sur le **boîte de dialogue** icône directory.

1. Ouvrez la boîte de dialogue IDD_PROPPAGE_SAMPLE.

   L’Assistant contrôle ActiveX ajoute le nom du projet à la fin de l’ID de boîte de dialogue, dans ce cas, un exemple.

1. Glisser -déplacer le contrôle sélectionné à partir de la boîte à outils vers la zone de la boîte de dialogue.

1. Pour cet exemple, un texte de contrôle de l’étiquette « Caption : » et un contrôle de zone d’édition avec un identificateur IDC_CAPTION suffisent.

1. Cliquez sur **enregistrer** sur la barre d’outils pour enregistrer vos modifications.

Maintenant que l’interface utilisateur a été modifié, vous devez lier la zone d’édition avec la propriété de légende. Cela est effectué dans la section suivante en modifiant le `CSamplePropPage::DoDataExchange` (fonction).

##  <a name="_core_customizing_the_dodataexchange_function"></a> Personnalisation de la fonction DoDataExchange

Votre page de propriétés [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) fonction vous permet de lier les valeurs de page de propriété avec les valeurs réelles des propriétés dans le contrôle. Pour établir des liens, vous devez mapper les champs de page de propriété appropriée à leurs propriétés de contrôle respectif.

Ces mappages sont implémentées à l’aide de la page de propriétés **DDP_** fonctions. Le **DDP_** fonctions fonctionnent comme le **DDX_** fonctions utilisées dans des boîtes de dialogue MFC standard, à une exception près. En plus de la référence à une variable membre, **DDP_** fonctions acceptent le nom de la propriété du contrôle. Ce qui suit est une entrée de type dans le `DoDataExchange` (fonction) pour une page de propriétés.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Cette fonction associe la page de propriétés *m_caption* variable de membre avec la légende, à l’aide de la `DDP_TEXT` (fonction).

Après avoir configuré le contrôle de page de propriété inséré, vous devez établir un lien entre le contrôle de page de propriétés, IDC_CAPTION et la propriété du contrôle réel, à l’aide de la légende du `DDP_Text` fonctionne comme décrit ci-dessus.

[Pages de propriétés](../mfc/reference/property-pages-mfc.md) sont disponibles pour d’autres types de contrôle de boîte de dialogue, telles que les cases à cocher, cases d’option et les zones de liste. Le tableau ci-dessous répertorie l’ensemble de la page de propriétés **DDP_** fonctions et leurs objectifs :

### <a name="property-page-functions"></a>Fonctions de Page de propriétés

|Nom de la fonction|Cette fonction permet de lier|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Index de la chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle.|
|`DDP_CBString`|La chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais n’est pas forcément il entièrement.|
|`DDP_CBStringExact`|La chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Check`|Une case à cocher avec une propriété du contrôle.|
|`DDP_LBIndex`|Index de la chaîne sélectionnée dans une zone de liste avec une propriété du contrôle.|
|`DDP_LBString`|La chaîne sélectionnée dans une zone de liste avec une propriété du contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais n’est pas forcément il entièrement.|
|`DDP_LBStringExact`|La chaîne sélectionnée dans une zone de liste avec une propriété du contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Radio`|Un bouton radio avec une propriété du contrôle.|
|`DDP_Text`|Texte avec une propriété du contrôle.|

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage, classe](../mfc/reference/colepropertypage-class.md)
