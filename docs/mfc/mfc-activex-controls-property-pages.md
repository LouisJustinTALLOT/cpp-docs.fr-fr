---
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
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364568"
---
# <a name="mfc-activex-controls-property-pages"></a>Contrôles ActiveX MFC : pages de propriétés

Les pages de propriété permettent à un utilisateur de contrôle ActiveX de visualiser et de modifier les propriétés de contrôle ActiveX. Ces propriétés sont accessibles en invoquant une boîte de dialogue de propriétés de contrôle, qui contient une ou plusieurs pages de propriété qui fournissent une interface graphique personnalisée pour l’affichage et l’édition des propriétés de contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Les pages de propriété de contrôle ActiveX sont affichées de deux façons :

- Lorsque le verbe propriétés du contrôle **(OLEIVERB_PROPERTIES**) est invoqué, le contrôle ouvre une boîte de dialogue de propriété modale qui contient les pages de propriété du contrôle.

- Le conteneur peut afficher sa propre boîte de dialogue sans mode qui affiche les pages de propriété du contrôle sélectionné.

La boîte de dialogue des propriétés (illustrée dans la figure suivante) se compose d’une zone pour afficher la page de propriété actuelle, onglets pour passer entre les pages de propriété, et une collection de boutons qui exécutent des tâches communes telles que la fermeture de la page de propriété dialogue, l’annulation de toute modification apportée, ou l’application immédiate de toute modification au contrôle ActiveX.

![Boîte de dialogue Propriétés pour Circ3](../mfc/media/vc373i1.gif "Boîte de dialogue Propriétés pour Circ3") <br/>
Propriétés Dialog Box

Cet article couvre des sujets liés à l’utilisation des pages de propriété dans un contrôle ActiveX. notamment :

- [Mise en œuvre de la page de propriété par défaut pour un contrôle ActiveX](#_core_implementing_the_default_property_page)

- [Ajout de contrôles à une page de propriété](#_core_adding_controls_to_a_property_page)

- [Personnaliser la fonction DoDataExchange](#_core_customizing_the_dodataexchange_function)

Pour plus d’informations sur l’utilisation des pages de propriété dans un contrôle ActiveX, voir les articles suivants:

- [Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Pour obtenir de l’information sur l’utilisation de feuilles de propriété dans une application MFC autre qu’un contrôle ActiveX, voir [feuilles de propriété](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Mise en œuvre de la page des biens par défaut

Si vous utilisez l’Assistant de Contrôle ActiveX pour créer votre projet de contrôle, l’Assistant de Contrôle ActiveX fournit une classe de page de propriété par défaut pour le contrôle dérivé de [la classe COlePropertyPage](../mfc/reference/colepropertypage-class.md). Initialement, cette page de propriété est vide, mais vous pouvez ajouter n’importe quel contrôle de boîte de dialogue ou ensemble de contrôles à elle. Étant donné que l’Assistant de Contrôle ActiveX ne crée qu’une seule classe de pages de propriété par défaut, des cours supplémentaires de pages de propriété (également dérivés) `COlePropertyPage`doivent être créés en utilisant Class View. Pour plus d’informations sur cette procédure, voir [MFC ActiveX Controls: Adding Another Custom Property Page](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

La mise en œuvre d’une page de propriété (dans ce cas, par défaut) est un processus en trois étapes :

#### <a name="to-implement-a-property-page"></a>Mettre en œuvre une page de propriété

1. Ajoutez `COlePropertyPage`une classe dérivée au projet de contrôle. Si le projet a été créé à l’aide de l’ActiveX Control Wizard (comme dans ce cas), la classe de page de propriété par défaut existe déjà.

1. Utilisez l’éditeur de dialogue pour ajouter des contrôles au modèle de page de propriété.

1. Personnalisez `DoDataExchange` la `COlePropertyPage`fonction de la classe dérivée pour échanger des valeurs entre le contrôle de la page de propriété et le contrôle ActiveX.

À titre exemple, les procédures suivantes utilisent un contrôle simple (appelé « échantillon »). L’échantillon a été créé à l’aide de l’ActiveX Control Wizard et ne contient que la propriété caption stock.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Ajout de contrôles à une page de propriété

#### <a name="to-add-controls-to-a-property-page"></a>Pour ajouter des contrôles à une page de propriété

1. Avec votre projet de contrôle ouvert, ouvrez Resource View.

1. Double-cliquez sur l’icône **dialog** répertoire.

1. Ouvrez la boîte de dialogue IDD_PROPPAGE_SAMPLE.

   L’Assistant de Contrôle ActiveX joint le nom du projet à la fin de l’ID de dialogue, dans ce cas, Sample.

1. Faites glisser et laissez tomber le contrôle choisi de la boîte à outils sur la zone de la boîte de dialogue.

1. Pour cet exemple, un contrôle d’étiquette de texte "Caption :" et un contrôle de boîte de modification avec un identifiant IDC_CAPTION sont suffisants.

1. Cliquez **sur Enregistrer** sur la barre d’outils pour enregistrer vos modifications.

Maintenant que l’interface utilisateur a été modifiée, vous devez lier la boîte de modification avec la propriété Caption. Ceci est fait dans la `CSamplePropPage::DoDataExchange` section suivante en éditant la fonction.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Personnaliser la fonction DoDataExchange

Votre page de propriété [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) fonction vous permet de lier les valeurs de la page de propriété avec les valeurs réelles des propriétés dans le contrôle. Pour établir des liens, vous devez cartographier les champs de pages de propriété appropriés à leurs propriétés de contrôle respectives.

Ces cartes sont mises en œuvre à l’aide de la page de propriété **DDP_** fonctions. Les **fonctions DDP_** fonctionnent comme les fonctions **DDX_** utilisées dans les dialogues MFC standard, à une exception près. En plus de la référence à une variable membre, **DDP_** fonctions prennent le nom de la propriété de contrôle. Ce qui suit est `DoDataExchange` une entrée typique dans la fonction pour une page de propriété.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Cette fonction associe la variable *m_caption* membre de la page `DDP_TEXT` de propriété à la Légende, en utilisant la fonction.

Après avoir inséré le contrôle de la page de propriété, vous devez établir un lien entre le contrôle `DDP_Text` de la page de propriété, IDC_CAPTION, et la propriété de contrôle réelle, Caption, en utilisant la fonction décrite ci-dessus.

[Les pages de propriété](../mfc/reference/property-pages-mfc.md) sont disponibles pour d’autres types de contrôle de dialogue, tels que les cases à cocher, les boutons radio, et les boîtes de liste. Le tableau ci-dessous énumère l’ensemble de la page de propriété **DDP_** fonctions et leurs buts :

### <a name="property-page-functions"></a>Fonctions de page de propriété

|Nom de la fonction|Utilisez cette fonction pour lier|
|-------------------|-------------------------------|
|`DDP_CBIndex`|L’index de la chaîne sélectionnée dans une boîte combo avec une propriété de contrôle.|
|`DDP_CBString`|La chaîne sélectionnée dans une boîte combo avec une propriété de contrôle. La chaîne sélectionnée peut commencer avec les mêmes lettres que la valeur de la propriété, mais n’a pas besoin de l’égaler entièrement.|
|`DDP_CBStringExact`|La chaîne sélectionnée dans une boîte combo avec une propriété de contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Check`|Une case à cocher avec une propriété de contrôle.|
|`DDP_LBIndex`|L’index de la chaîne sélectionnée dans une boîte de liste avec une propriété de contrôle.|
|`DDP_LBString`|La chaîne sélectionnée dans une boîte de liste avec une propriété de contrôle. La chaîne sélectionnée peut commencer avec les mêmes lettres que la valeur de la propriété, mais n’a pas besoin de l’égaler entièrement.|
|`DDP_LBStringExact`|La chaîne sélectionnée dans une boîte de liste avec une propriété de contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|`DDP_Radio`|Un bouton radio avec une propriété de contrôle.|
|`DDP_Text`|Texte avec une propriété de contrôle.|

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage, classe](../mfc/reference/colepropertypage-class.md)
