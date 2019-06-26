---
title: Contrôles de boîte de dialogue (C++) | Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 568754bc514ae017293805fab1b25849d5ffe5f8
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400885"
---
# <a name="dialog-box-controls-c"></a>Contrôles de boîte de dialogue (C++)

Vous pouvez ajouter des contrôles à une boîte de dialogue à l’aide de la **boîte de dialogue Éditeur** onglet dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) qui vous permet de choisir le contrôle souhaité et faites-le glisser vers la boîte de dialogue. Par défaut, le **boîte à outils** fenêtre est définie sur Masquer automatiquement. Il s’affiche sous forme d’onglet dans la marge gauche de votre solution lorsque le **boîte de dialogue Éditeur** est ouvert. Toutefois, vous pouvez épingler la **boîte à outils** fenêtre embases en sélectionnant le **Masquer automatiquement** bouton dans le coin supérieur droit de la fenêtre. Pour plus d’informations sur la façon de contrôler le comportement de cette fenêtre, consultez [gestion des fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le moyen le plus rapide pour ajouter des contrôles à une boîte de dialogue, repositionner des contrôles existants ou déplacer des contrôles à partir d’une boîte de dialogue à l’autre consiste à utiliser la méthode glisser-déplacer. La position du contrôle est décrite dans une ligne en pointillés jusqu'à ce qu’il sera déposé dans la boîte de dialogue. Lorsque vous ajoutez un contrôle à une boîte de dialogue avec la méthode glisser-déplacer, le contrôle est donné à une hauteur standard appropriée pour ce type de contrôle.

Lorsque vous ajoutez un contrôle à une boîte de dialogue ou repositionnez, son emplacement final peut être déterminé par les guides ou les marges, ou si vous disposez de la grille de disposition sous tension.

Une fois que vous avez ajouté un contrôle à la boîte de dialogue, vous pouvez modifier les propriétés telles que sa légende dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez également sélectionner plusieurs contrôles et modifier leurs propriétés à la fois.

Pour plus d’informations sur la **boîte de dialogue Éditeur**, consultez Comment [ajouter, modifier ou supprimer des contrôles](adding-editing-or-deleting-controls.md), [contrôles de disposition](../windows/arrangement-of-controls-on-dialog-boxes.md), et [définir contrôler l’accès et des valeurs](../windows/defining-mnemonics-access-keys.md).

Pour plus d’informations sur les contrôles et boîtes de dialogue, consultez [Classes de contrôle](../mfc/control-classes.md), [Classes de boîte de dialogue](../mfc/dialog-box-classes.md), et [Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Les contrôles standards disponibles dans le **boîte à outils** valeur par défaut, les événements sont :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle de bouton](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Contrôle de case à cocher](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Combo Box](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Contrôle d’édition](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Contrôle Group box|(non applicable)|
|[Contrôle List Box](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Static Text](../mfc/reference/cstatic-class.md)|(non applicable)|
|[Contrôle d’image](../mfc/reference/cpictureholder-class.md)|(non applicable)|
|[Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Pour plus d’informations sur l’utilisation de la **RichEdit 1.0** contrôler avec MFC, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) et [enrichi modifier des exemples de contrôle](../mfc/rich-edit-control-examples.md).

Le [contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans le **boîte à outils** pour fournir des fonctionnalités améliorées sont :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle Slider](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Contrôle Spin](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Contrôle de progression](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Contrôle Hot Key](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Contrôle de liste](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Contrôle d’arborescence](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Contrôle onglet](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Contrôle Animation](../mfc/using-an-animation-control.md)|ACN_START|
|[Contrôle Date Time Picker](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Contrôle Month Calendar](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Contrôle de l’adresse IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Contrôle Extended Combo Box](../mfc/creating-an-extended-combo-box-control.md)||
|Contrôle personnalisé|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Contrôles personnalisés

Le **boîte de dialogue Éditeur** vous permet d’utiliser l’existant personnalisé ou contrôles utilisateur dans un modèle de boîte de dialogue.

> [!NOTE]
> Contrôles personnalisés dans ce sens doivent ne pas être confondus avec les contrôles ActiveX. Contrôles ActiveX étaient parfois appelés contrôles personnalisés OLE. En outre, ne confondez pas ces contrôles avec les contrôles owner-drawn dans Windows.

Cette fonctionnalité vise à vous permettent d’utiliser des contrôles autres que ceux fournis par Windows. Au moment de l’exécution, le contrôle est associé à une classe de fenêtre (pas identique à une classe C++). Une façon plus courante pour accomplir la même tâche consiste à installer n’importe quel contrôle, tel qu’un contrôle statique, dans votre boîte de dialogue. Puis au moment de l’exécution, dans le [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fonctionner, supprimez ce contrôle et remplacez-le par votre propre contrôle personnalisé.

> [!NOTE]
> Il s’agit d’une vieille méthode. Aujourd'hui, il est conseillé dans la plupart des cas d’écrire un contrôle ActiveX ou une sous-classe un contrôle commun de Windows.

Pour ces contrôles personnalisés, vous êtes limité à :

- Définition de l’emplacement dans la boîte de dialogue.

- Taper une légende.

- Identifiant le nom de la classe du contrôle Windows dans la mesure où votre code d’application doit inscrire le contrôle portant ce nom.

- Taper une valeur hexadécimale 32 bits qui définit le style du contrôle.

- Définir le style étendu.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->