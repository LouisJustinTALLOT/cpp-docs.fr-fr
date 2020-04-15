---
title: 'Contrôles ActiveX MFC : ajout de propriétés stock'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364661"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Contrôles ActiveX MFC : ajout de propriétés stock

Les propriétés boursières diffèrent des propriétés `COleControl`personnalisées en ce qu’elles sont déjà mises en œuvre par la classe. `COleControl`contient des fonctions prédéfinises des membres qui prennent en charge les propriétés communes pour le contrôle. Certaines propriétés courantes incluent la légende du contrôle et les couleurs de premier plan et de fond. Pour plus d’informations sur d’autres propriétés d’actions, voir [Stock Properties Supported by the Add Property Wizard](#_core_stock_properties_supported_by_classwizard) plus tard dans cet article. Les entrées de carte de répartition pour les propriétés stock sont toujours préfixées par DISP_STOCKPROP.

Cet article décrit comment ajouter une propriété stock (dans ce cas, caption) à un contrôle ActiveX à l’aide de l’Add Property Wizard et explique les modifications de code qui en résultent. Les sujets abordés sont les suivants :

- [Utilisation de l’Add Property Wizard pour ajouter une propriété en stock](#_core_using_classwizard_to_add_a_stock_property)

- [Ajouter des modifications de l’Assistant de propriété pour les propriétés des actions](#_core_classwizard_changes_for_stock_properties)

- [Propriétés d’actions prises en charge par l’Add Property Wizard](#_core_stock_properties_supported_by_classwizard)

- [Propriétés d’actions et notification](#_core_stock_properties_and_notification)

- [Propriétés de couleur](#_core_color_properties)

    > [!NOTE]
    >  Les commandes personnalisées Visual Basic ont généralement des propriétés telles que Top, Gauche, Largeur, Hauteur, Align, Tag, Nom, TabIndex, TabStop et Parent. Les conteneurs de contrôle ActiveX, cependant, sont responsables de la mise en œuvre de ces propriétés de contrôle et, par conséquent, les contrôles ActiveX ne devraient pas prendre en charge ces propriétés.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Utilisation de l’assistant de propriété Ajouter pour ajouter une propriété stock

L’ajout de propriétés stock nécessite moins de code que `COleControl`l’ajout de propriétés personnalisées parce que le support pour la propriété est géré automatiquement par . La procédure suivante démontre l’ajout de la propriété caption stock à un cadre de contrôle ActiveX et peut également être utilisé pour ajouter d’autres propriétés de stock. Remplacez le nom de propriété d’actions sélectionnée par caption.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété de légende de stock utilisant le Magicien de propriété d’ajouter

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le [Add Property Wizard](../ide/names-add-property-wizard.md).

1. Dans la boîte **nom de propriété,** cliquez sur **caption**.

1. Cliquez sur **Terminer**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Ajouter des changements de sorcier de propriété pour des propriétés d’actions

Parce `COleControl` que prend en charge les propriétés des actions, l’Assistant De propriété Add ne change pas la déclaration de classe en aucune façon; il ajoute la propriété à la carte d’expédition. Le Assistant De propriété Add ajoute la ligne suivante à la carte de répartition du contrôle, qui est situé dans la mise en œuvre (. Dossier du RPC :

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La ligne suivante est ajoutée à la description de l’interface de votre contrôle (. Fichier IDL) :

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Cette ligne attribue à la propriété caption une pièce d’identité spécifique. Notez que la propriété est liante et demandera la permission de la base de données avant de modifier la valeur.

Cela rend la propriété caption accessible aux utilisateurs de votre contrôle. Pour utiliser la valeur d’une propriété d’actions, `COleControl` accédez à une variable de membre ou à la fonction membre de la classe de base. Pour plus d’informations sur ces variables de membre et les fonctions des membres, voir la section suivante, Stock Properties Supported by the Add Property Wizard.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Propriétés d’actions soutenues par l’assistant de propriété d’ajouter

La `COleControl` classe fournit neuf propriétés de stock. Vous pouvez ajouter les propriétés que vous voulez en utilisant le Assistant De propriété Add.

|Propriété|Entrée de carte d’expédition|Comment accéder à la valeur|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE)|Valeur accessible `m_sAppearance`comme .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR)|Valeur accessible `GetBackColor`par appel .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE)|Valeur accessible `m_sBorderStyle`comme .|
|`Caption`|DISP_STOCKPROP_CAPTION)|Valeur accessible `InternalGetText`par appel .|
|`Enabled`|DISP_STOCKPROP_ENABLED)|Valeur accessible `m_bEnabled`comme .|
|`Font`|DISP_STOCKPROP_FONT)|Voir l’article [MFC ActiveX Controls: Using Polices](../mfc/mfc-activex-controls-using-fonts.md) for use.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR)|Valeur accessible `GetForeColor`par appel .|
|`hWnd`|DISP_STOCKPROP_HWND)|Valeur accessible `m_hWnd`comme .|
|`Text`|DISP_STOCKPROP_TEXT)|Valeur accessible `InternalGetText`par appel . Cette propriété est `Caption`la même que , sauf pour le nom de la propriété.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Valeur accessible `m_lReadyState` au fur et à mesure ou`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Propriétés et notification d’actions

La plupart des propriétés stock ont des fonctions de notification qui peuvent être annulées. Par exemple, `BackColor` chaque fois que `OnBackColorChanged` la propriété est modifiée, la fonction (fonction membre de la classe de contrôle) est appelée. La implémentation par défaut (dans `COleControl`) appels `InvalidateControl`. Remplacez cette fonction si vous souhaitez prendre des mesures supplémentaires en réponse à cette situation.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Propriétés de couleur

Vous pouvez utiliser `ForeColor` `BackColor` le stock et les propriétés, ou vos propres propriétés de couleur personnalisées, lors de la peinture du contrôle. Pour utiliser une propriété de couleur, appelez la fonction de membre [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) membre. Les paramètres de cette fonction sont la valeur de la propriété de couleur et une poignée de palette facultative. La valeur de retour est une valeur **COLORREF** qui peut `SetTextColor` `CreateSolidBrush`être transmise aux fonctions GDI, telles que et .

Les valeurs de `ForeColor` couleur `BackColor` pour le stock et `GetForeColor` les `GetBackColor` propriétés sont accessibles en appelant soit la fonction ou la fonction, respectivement.

L’exemple suivant montre l’utilisation de ces deux propriétés de couleur lors de la peinture d’un contrôle. Il est parascatifatif d’une variable **COLORREF** temporaire et d’un `CBrush` objet avec des appels `TranslateColor`à : l’un utilisant la `ForeColor` propriété et l’autre à l’aide de la `BackColor` propriété. Un `CBrush` objet temporaire est ensuite utilisé pour peindre le rectangle du `ForeColor` contrôle, et la couleur du texte est définie à l’aide de la propriété.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
