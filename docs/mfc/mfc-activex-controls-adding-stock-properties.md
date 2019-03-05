---
title: 'Contrôles ActiveX MFC : Ajout de propriétés Stock'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289687"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Contrôles ActiveX MFC : Ajout de propriétés Stock

Propriétés stock diffèrent des propriétés personnalisées, ils sont déjà implémentées par la classe `COleControl`. `COleControl` contient des fonctions membres prédéfinies qui prennent en charge des propriétés communes pour le contrôle. Certaines propriétés courantes incluent la légende du contrôle et les couleurs de premier plan et d’arrière-plan. Pour plus d’informations sur les propriétés stock, consultez [Propriétés Stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard) plus loin dans cet article. Les entrées de mappage de répartition pour les propriétés sont toujours préfixées par DISP_STOCKPROP de stock.

Cet article décrit comment ajouter une propriété stock (dans ce cas, la légende) à un contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résulte. Les rubriques traitées ici sont les suivantes :

- [À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété stock](#_core_using_classwizard_to_add_a_stock_property)

- [Ajoutez les modifications de propriété Assistant de propriétés stock](#_core_classwizard_changes_for_stock_properties)

- [Propriétés stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard)

- [Propriétés stock et notification](#_core_stock_properties_and_notification)

- [Propriétés de couleur](#_core_color_properties)

    > [!NOTE]
    >  Contrôles personnalisés de Visual Basic ont généralement des propriétés telles que le haut, gauche, la largeur, hauteur, alignement, balise, nom, TabIndex, TabStop et Parent. Toutefois, les conteneurs de contrôles ActiveX, sont responsables de l’implémentation de ces propriétés de contrôle et par conséquent, les contrôles ActiveX doivent prend pas en charge ces propriétés.

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété Stock

Ajout de propriétés stock nécessite moins de code que l’ajout de propriétés personnalisées, car prise en charge de la propriété est gérée automatiquement par `COleControl`. La procédure suivante montre comment ajouter la propriété stock Caption à une infrastructure de contrôle ActiveX et peut également être utilisée pour ajouter d’autres propriétés stock. Remplacez le nom de propriété stock sélectionnée pour la légende.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété stock Caption à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

   Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).

1. Dans le **nom de la propriété** , cliquez sur **légende**.

1. Cliquez sur **Terminer**.

##  <a name="_core_classwizard_changes_for_stock_properties"></a> Ajouter la propriété Assistant modifie des propriétés Stock

Étant donné que `COleControl` propriétés stock prend en charge, l’Assistant Ajout de propriété ne change pas la déclaration de classe en aucune façon ; il ajoute la propriété à la table de dispatch. L’Assistant Ajout de propriété ajoute la ligne suivante à la table de dispatch du contrôle, qui se trouve dans l’implémentation (. Fichier CPP) :

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La ligne suivante est ajoutée à la description de l’interface de votre contrôle (. Fichier IDL) :

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Cette ligne assigne à la propriété Caption un ID spécifique. Notez que la propriété peut être liée et demandera une autorisation à partir de la base de données avant de modifier la valeur.

La propriété Caption sont ainsi disponibles aux utilisateurs de votre contrôle. Pour utiliser la valeur d’une propriété stockée, accéder à une variable membre ou une fonction membre de la `COleControl` classe de base. Pour plus d’informations sur ces variables membres et les fonctions membres, consultez la section suivante, propriétés Stock prises en charge par l’Assistant Ajout de propriété.

##  <a name="_core_stock_properties_supported_by_classwizard"></a> Stock des propriétés prises en charge par l’Assistant Ajout de propriété

Le `COleControl` classe fournit neuf propriétés stock. Vous pouvez ajouter les propriétés souhaitées à l’aide de l’Assistant Ajout de propriété.

|Propriété|Entrée de mappage de dispatch|Comment accéder à la valeur|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Valeur accessible en tant que `m_sAppearance`.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Valeur accessible par un appel `GetBackColor`.|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Valeur accessible en tant que `m_sBorderStyle`.|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Valeur accessible par un appel `InternalGetText`.|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Valeur accessible en tant que `m_bEnabled`.|
|`Font`|DISP_STOCKPROP_FONT( )|Consultez l’article [contrôles ActiveX MFC : Utilisation des polices](../mfc/mfc-activex-controls-using-fonts.md) pour utilisation.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Valeur accessible par un appel `GetForeColor`.|
|`hWnd`|DISP_STOCKPROP_HWND( )|Valeur accessible en tant que `m_hWnd`.|
|`Text`|DISP_STOCKPROP_TEXT( )|Valeur accessible par un appel `InternalGetText`. Cette propriété est identique à `Caption`, à l’exception du nom de propriété.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Valeur accessible en tant que `m_lReadyState` ou `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> Propriétés stock et notification

La plupart des propriétés stock comportent des fonctions de notification qui peuvent être substituées. Par exemple, chaque fois que le `BackColor` propriété est modifiée, le `OnBackColorChanged` (fonction) (une fonction membre de la classe de contrôle) est appelée. L’implémentation par défaut (dans `COleControl`) appels `InvalidateControl`. Remplacez cette fonction si vous souhaitez exécuter des actions supplémentaires en réponse à cette situation.

##  <a name="_core_color_properties"></a> Propriétés de couleur

Vous pouvez utiliser le stock `ForeColor` et `BackColor` propriétés ou vos propres propriétés de couleur personnalisée pour le contrôle. Pour utiliser une propriété de couleur, appelez le [fonction membre COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) fonction membre. Les paramètres de cette fonction sont la valeur de la propriété de couleur et un descripteur de palette facultatif. La valeur de retour est un **COLORREF** fonctions de valeur qui peut être passée à GDI, telles que `SetTextColor` et `CreateSolidBrush`.

Les valeurs de couleur pour la cotation `ForeColor` et `BackColor` propriétés sont accessibles en appelant le `GetForeColor` ou le `GetBackColor` de fonction, respectivement.

L’exemple suivant illustre l’utilisation de ces deux propriétés de couleurs lorsque vous dessinez un contrôle. Il initialise une table temporaire **COLORREF** variable et un `CBrush` objet avec les appels à `TranslateColor`: un à l’aide la `ForeColor` propriété et l’autre à l’aide du `BackColor` propriété. Une table temporaire `CBrush` objet est ensuite utilisé pour peindre le rectangle du contrôle, et la couleur de texte est définie à l’aide de la `ForeColor` propriété.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : Propriétés](../mfc/mfc-activex-controls-properties.md)<br/>
[Contrôles ActiveX MFC : Méthodes](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl, classe](../mfc/reference/colecontrol-class.md)
