---
description: 'En savoir plus sur : contrôles ActiveX MFC : ajout de propriétés stock'
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
ms.openlocfilehash: 1bcfc69fe5fd7cdcadcd641fb831c07bde79bbfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202819"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Contrôles ActiveX MFC : ajout de propriétés stock

Les propriétés stock diffèrent des propriétés personnalisées dans le fait qu’elles sont déjà implémentées par la classe `COleControl` . `COleControl` contient des fonctions membres prédéfinies qui prennent en charge des propriétés communes pour le contrôle. Certaines propriétés communes incluent la légende du contrôle, ainsi que les couleurs de premier plan et d’arrière-plan. Pour plus d’informations sur les autres propriétés stock, consultez [propriétés stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard) plus loin dans cet article. Les entrées de la table de dispatch pour les propriétés stock sont toujours précédées de DISP_STOCKPROP.

Cet article explique comment ajouter une propriété stock (en l’occurrence, Caption) à un contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résultent. Les sujets abordés sont les suivants :

- [Utilisation de l’Assistant Ajout de propriété pour ajouter une propriété stock](#_core_using_classwizard_to_add_a_stock_property)

- [Modifications de l’Assistant Ajout de propriété pour les propriétés stock](#_core_classwizard_changes_for_stock_properties)

- [Propriétés stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard)

- [Propriétés et notification stock](#_core_stock_properties_and_notification)

- [Propriétés de couleur](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic contrôles personnalisés ont en général des propriétés telles que haut, gauche, largeur, hauteur, aligner, balise, nom, TabIndex, ArrêtTabulation et parent. Toutefois, les conteneurs de contrôles ActiveX sont responsables de l’implémentation de ces propriétés de contrôle. par conséquent, les contrôles ActiveX ne doivent pas prendre en charge ces propriétés.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a> Utilisation de l’Assistant Ajout de propriété pour ajouter une propriété stock

L’ajout de propriétés stock requiert moins de code que l’ajout de propriétés personnalisées, car la prise en charge de la propriété est gérée automatiquement par `COleControl` . La procédure suivante montre comment ajouter la propriété stock Caption à une infrastructure de contrôle ActiveX et peut également être utilisée pour ajouter d’autres propriétés stock. Remplacez la légende par le nom de la propriété stock sélectionnée.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété stock Caption à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L' [Assistant Ajouter une propriété](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)s’ouvre.

1. Dans la zone nom de la **propriété** , cliquez sur **légende**.

1. Cliquez sur **Terminer**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a> Modifications de l’Assistant Ajout de propriété pour les propriétés stock

Étant donné que `COleControl` prend en charge les propriétés stock, l’Assistant Ajout de propriété ne modifie en aucune façon la déclaration de classe ; il ajoute la propriété à la table de dispatch. L’Assistant Ajout de propriété ajoute la ligne suivante à la table de dispatch du contrôle, qui se trouve dans l’implémentation (. CPP) :

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La ligne suivante est ajoutée à la description de l’interface de votre contrôle (. Fichier IDL) :

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Cette ligne affecte un ID spécifique à la propriété Caption. Notez que la propriété peut être liée et qu’elle demande l’autorisation à la base de données avant de modifier la valeur.

La propriété Caption est alors disponible pour les utilisateurs de votre contrôle. Pour utiliser la valeur d’une propriété stock, accédez à une variable membre ou à une fonction membre de la `COleControl` classe de base. Pour plus d’informations sur ces variables membres et fonctions membres, consultez la section suivante, propriétés stock prises en charge par l’Assistant Ajout de propriété.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a> Propriétés stock prises en charge par l’Assistant Ajout de propriété

La `COleControl` classe fournit neuf propriétés stock. Vous pouvez ajouter les propriétés souhaitées à l’aide de l’Assistant Ajout d’une propriété.

|Propriété|Entrée de la table de dispatch|Comment accéder à la valeur|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ()|Valeur accessible en tant que `m_sAppearance` .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ()|Valeur accessible en appelant `GetBackColor` .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ()|Valeur accessible en tant que `m_sBorderStyle` .|
|`Caption`|DISP_STOCKPROP_CAPTION ()|Valeur accessible en appelant `InternalGetText` .|
|`Enabled`|DISP_STOCKPROP_ENABLED ()|Valeur accessible en tant que `m_bEnabled` .|
|`Font`|DISP_STOCKPROP_FONT ()|Consultez l’article [contrôles ActiveX MFC : utilisation des polices](mfc-activex-controls-using-fonts.md) pour l’utilisation.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ()|Valeur accessible en appelant `GetForeColor` .|
|`hWnd`|DISP_STOCKPROP_HWND ()|Valeur accessible en tant que `m_hWnd` .|
|`Text`|DISP_STOCKPROP_TEXT ()|Valeur accessible en appelant `InternalGetText` . Cette propriété est la même que `Caption` , à l’exception du nom de la propriété.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ()|Valeur accessible en tant que `m_lReadyState` ou `GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a> Propriétés et notification stock

La plupart des propriétés stock ont des fonctions de notification qui peuvent être remplacées. Par exemple, chaque fois que la `BackColor` propriété est modifiée, la `OnBackColorChanged` fonction (une fonction membre de la classe de contrôle) est appelée. L’implémentation par défaut (dans `COleControl` ) appelle `InvalidateControl` . Remplacez cette fonction si vous souhaitez effectuer des actions supplémentaires en réponse à cette situation.

## <a name="color-properties"></a><a name="_core_color_properties"></a> Propriétés de couleur

Vous pouvez utiliser la stock `ForeColor` et les `BackColor` Propriétés, ou vos propres propriétés de couleur personnalisées, lorsque vous peignez le contrôle. Pour utiliser une propriété Color, appelez la fonction membre [COleControl :: TranslateColor](reference/colecontrol-class.md#translatecolor) . Les paramètres de cette fonction sont la valeur de la propriété Color et un handle de palette facultatif. La valeur de retour est une valeur **COLORREF** qui peut être passée aux fonctions GDI, telles que `SetTextColor` et `CreateSolidBrush` .

Les valeurs de couleur pour le stock `ForeColor` et les `BackColor` propriétés sont accessibles en appelant la `GetForeColor` fonction ou `GetBackColor` , respectivement.

L’exemple suivant illustre l’utilisation de ces deux propriétés de couleur lors de la peinture d’un contrôle. Il Initialise une variable **COLORREF** temporaire et un `CBrush` objet avec des appels à `TranslateColor` : un à l’aide de la `ForeColor` propriété et de l’autre à l’aide de la `BackColor` propriété. Un `CBrush` objet temporaire est ensuite utilisé pour peindre le rectangle du contrôle, et la couleur du texte est définie à l’aide de la `ForeColor` propriété.

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md)<br/>
[Classe COleControl](reference/colecontrol-class.md)
