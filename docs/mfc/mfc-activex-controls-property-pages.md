---
description: 'En savoir plus sur : contrôles ActiveX MFC : pages de propriétés'
title: 'Contrôles ActiveX MFC : pages de propriétés'
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
ms.openlocfilehash: 40267857b12b2f23c07f03d0ee77b2ae8e6bf1a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206147"
---
# <a name="mfc-activex-controls-property-pages"></a>Contrôles ActiveX MFC : pages de propriétés

Les pages de propriétés permettent à un utilisateur de contrôle ActiveX d’afficher et de modifier les propriétés d’un contrôle ActiveX. Ces propriétés sont accessibles en appelant une boîte de dialogue des propriétés du contrôle, qui contient une ou plusieurs pages de propriétés qui fournissent une interface graphique personnalisée pour l’affichage et la modification des propriétés du contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Les pages de propriétés du contrôle ActiveX s’affichent de deux manières :

- Quand le verbe des propriétés du contrôle (**OLEIVERB_PROPERTIES**) est appelé, le contrôle ouvre une boîte de dialogue de propriétés modale qui contient les pages de propriétés du contrôle.

- Le conteneur peut afficher sa propre boîte de dialogue non modale qui affiche les pages de propriétés du contrôle sélectionné.

La boîte de dialogue Propriétés (illustrée dans la figure suivante) se compose d’une zone permettant d’afficher la page de propriétés actuelle, d’onglets pour basculer entre les pages de propriétés, et d’une collection de boutons qui effectuent des tâches courantes, telles que la fermeture de la boîte de dialogue de la page de propriétés, l’annulation des modifications apportées ou l’application immédiate des modifications

![Boîte de dialogue Propriétés pour Circ3](../mfc/media/vc373i1.gif "Boîte de dialogue Propriétés pour Circ3") <br/>
Boîte de dialogue Propriétés

Cet article aborde les rubriques relatives à l’utilisation des pages de propriétés dans un contrôle ActiveX. notamment :

- [Implémentation de la page de propriétés par défaut pour un contrôle ActiveX](#_core_implementing_the_default_property_page)

- [Ajout de contrôles à une page de propriétés](#_core_adding_controls_to_a_property_page)

- [Personnalisation de la fonction DoDataExchange](#_core_customizing_the_dodataexchange_function)

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : ajout d’une autre page de propriétés personnalisée](mfc-activex-controls-adding-another-custom-property-page.md)

- [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](mfc-activex-controls-using-stock-property-pages.md)

Pour plus d’informations sur l’utilisation des feuilles de propriétés dans une application MFC autre qu’un contrôle ActiveX, consultez [feuilles de propriétés](property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a> Implémentation de la page de propriétés par défaut

Si vous utilisez l’Assistant contrôle ActiveX pour créer votre projet de contrôle, l’Assistant contrôle ActiveX fournit une classe de page de propriétés par défaut pour le contrôle dérivé de la [classe COlePropertyPage](reference/colepropertypage-class.md). Initialement, cette page de propriétés est vide, mais vous pouvez y ajouter n’importe quel contrôle de boîte de dialogue ou ensemble de contrôles. Étant donné que l’Assistant contrôle ActiveX ne crée qu’une seule classe de page de propriétés par défaut, des classes de page de propriétés supplémentaires (également dérivées de `COlePropertyPage` ) doivent être créées à l’aide de affichage de classes. Pour plus d’informations sur cette procédure, consultez [contrôles ActiveX MFC : ajout d’une autre page de propriétés personnalisée](mfc-activex-controls-adding-another-custom-property-page.md).

L’implémentation d’une page de propriétés (dans ce cas, la valeur par défaut) est un processus en trois étapes :

#### <a name="to-implement-a-property-page"></a>Pour implémenter une page de propriétés

1. Ajoutez une `COlePropertyPage` classe dérivée de au projet de contrôle. Si le projet a été créé à l’aide de l’Assistant contrôle ActiveX (comme dans le cas présent), la classe de la page de propriétés par défaut existe déjà.

1. Utilisez l’éditeur de boîtes de dialogue pour ajouter des contrôles au modèle de page de propriétés.

1. Personnaliser la `DoDataExchange` fonction de la `COlePropertyPage` classe dérivée de pour échanger des valeurs entre le contrôle de page de propriétés et le contrôle ActiveX.

À titre d’exemple, les procédures suivantes utilisent un contrôle simple (nommé « Sample »). L’exemple a été créé à l’aide de l’Assistant contrôle ActiveX et contient uniquement la propriété stock Caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a> Ajout de contrôles à une page de propriétés

#### <a name="to-add-controls-to-a-property-page"></a>Pour ajouter des contrôles à une page de propriétés

1. Une fois votre projet de contrôle ouvert, ouvrez Affichage des ressources.

1. Double-cliquez sur l’icône du répertoire de **boîte de dialogue** .

1. Ouvrez la boîte de dialogue IDD_PROPPAGE_SAMPLE.

   L’Assistant contrôle ActiveX ajoute le nom du projet à la fin de l’ID de boîte de dialogue, dans le cas présent, Sample.

1. Glissez-déplacez le contrôle sélectionné de la boîte à outils vers la zone de boîte de dialogue.

1. Pour cet exemple, un contrôle d’étiquette de texte « Caption : » et un contrôle de zone d’édition avec un identificateur de IDC_CAPTION sont suffisants.

1. Cliquez sur **Enregistrer** dans la barre d’outils pour enregistrer vos modifications.

Maintenant que l’interface utilisateur a été modifiée, vous devez lier la zone d’édition à la propriété Caption. Pour ce faire, vous modifiez la fonction à l’aide de la section suivante `CSamplePropPage::DoDataExchange` .

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a> Personnalisation de la fonction DoDataExchange

Votre page de propriétés [CWnd ::D fonction odataexchange](reference/cwnd-class.md#dodataexchange) vous permet de lier des valeurs de page de propriétés avec les valeurs réelles des propriétés dans le contrôle. Pour établir des liens, vous devez mapper les champs de page de propriétés appropriés à leurs propriétés respectives de contrôle.

Ces mappages sont implémentés à l’aide de la page de propriétés **DDP_** fonctions. Les fonctions **DDP_** fonctionnent comme les fonctions **DDX_** utilisées dans les boîtes de dialogue MFC standard, à une exception près. En plus de la référence à une variable membre, **DDP_** fonctions prennent le nom de la propriété du contrôle. Voici une entrée type dans la `DoDataExchange` fonction d’une page de propriétés.

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Cette fonction associe la variable membre *m_caption* de la page de propriétés à la légende, à l’aide de la `DDP_TEXT` fonction.

Une fois le contrôle de page de propriétés inséré, vous devez établir un lien entre le contrôle de page de propriétés, IDC_CAPTION et la propriété de contrôle réelle, Caption, à l’aide de la `DDP_Text` fonction décrite ci-dessus.

Les [pages de propriétés](reference/property-pages-mfc.md) sont disponibles pour d’autres types de contrôles de boîte de dialogue, tels que les cases à cocher, les cases d’option et les zones de liste. Le tableau ci-dessous répertorie la totalité de l’ensemble de la page de propriétés **DDP_** fonctions et leurs objectifs :

### <a name="property-page-functions"></a>Fonctions de page de propriétés

|Nom de la fonction|Utilisez cette fonction pour créer un lien|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Index de la chaîne sélectionnée dans une zone de liste déroulante avec une propriété de contrôle.|
|`DDP_CBString`|Chaîne sélectionnée dans une zone de liste déroulante avec une propriété de contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de la propriété, mais elle n’a pas besoin d’être entièrement identique.|
|`DDP_CBStringExact`|Chaîne sélectionnée dans une zone de liste déroulante avec une propriété de contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Check`|Case à cocher avec une propriété de contrôle.|
|`DDP_LBIndex`|Index de la chaîne sélectionnée dans une zone de liste avec une propriété de contrôle.|
|`DDP_LBString`|Chaîne sélectionnée dans une zone de liste avec une propriété de contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de la propriété, mais elle n’a pas besoin d’être entièrement identique.|
|`DDP_LBStringExact`|Chaîne sélectionnée dans une zone de liste avec une propriété de contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Radio`|Case d’option avec une propriété de contrôle.|
|`DDP_Text`|Texte avec une propriété de contrôle.|

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[COlePropertyPage (classe)](reference/colepropertypage-class.md)
