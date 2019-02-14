---
title: Contrôles dans les boîtes de dialogue (C++) | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f231a376b335d7fb711ef2039c13f49624e6bfb
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264840"
---
# <a name="controls-in-dialog-boxes-c"></a>Contrôles dans les boîtes de dialogue (C++)

Vous pouvez ajouter des contrôles à une boîte de dialogue à l’aide de la [onglet de boîte de dialogue Éditeur](../windows/dialog-editor-tab-toolbox.md) dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), ce qui vous permet de choisir le contrôle souhaité et faites-le glisser vers la boîte de dialogue. Par défaut, la fenêtre de boîte à outils est définie sur Masquer automatiquement. Il s’affiche sous forme d’onglet dans la marge gauche de votre solution lorsque l’éditeur de boîtes de dialogue est ouverte. Toutefois, vous pouvez épingler la **boîte à outils** fenêtre dans sa position en cliquant sur le **Masquer automatiquement** bouton dans le coin supérieur droit de la fenêtre. Pour plus d’informations sur la façon de contrôler le comportement de cette fenêtre, consultez [gestion des fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le moyen le plus rapide pour ajouter des contrôles à une boîte de dialogue, repositionner des contrôles existants ou déplacer des contrôles à partir d’une boîte de dialogue à l’autre consiste à utiliser la méthode glisser-déplacer. La position du contrôle est décrite dans une ligne en pointillés jusqu'à ce qu’il sera déposé dans la boîte de dialogue. Lorsque vous ajoutez un contrôle à une boîte de dialogue avec la méthode glisser-déplacer, le contrôle est donné à une hauteur standard appropriée pour ce type de contrôle.

Lorsque vous ajoutez un contrôle à une boîte de dialogue ou repositionnez, son emplacement final peut être déterminé par les guides ou les marges, ou si vous disposez de la grille de disposition sous tension.

Une fois que vous avez ajouté un contrôle à la boîte de dialogue, vous pouvez modifier les propriétés telles que sa légende dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez sélectionner plusieurs contrôles et modifier leurs propriétés à la fois.

- [Ajout, modification ou suppression de contrôles](adding-editing-or-deleting-controls.md)

- [Sélection de contrôles](../windows/selecting-controls.md)

- [Dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md)

- [Définition de la même largeur, hauteur ou taille pour des contrôles](../windows/making-controls-the-same-width-height-or-size.md)

- [Définition de la taille d’une zone de liste déroulante et de sa liste déroulante](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md)

- [Définition de la largeur d’une barre de défilement horizontale](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [L’organisation des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [Définition des mnémoniques (Touches d’accès rapide)](../windows/defining-mnemonics-access-keys.md)

- [Spécification de l’emplacement et de la taille d’une boîte de dialogue](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

Les contrôles standards disponibles dans le **boîte à outils** valeur par défaut, les événements sont :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle de bouton](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Contrôle de case à cocher](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Combo Box](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Contrôle d’édition](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Contrôle Group box|(Non applicable)|
|[Contrôle List Box](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Static Text](../mfc/reference/cstatic-class.md)|(Non applicable)|
|[Contrôle d’image](../mfc/reference/cpictureholder-class.md)|(Non applicable)|
|[Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

Pour plus d’informations sur l’utilisation de la **RichEdit 1.0** contrôler avec MFC, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) et [enrichi modifier des exemples de contrôle](../mfc/rich-edit-control-examples.md).

Le [contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans le **boîte à outils** fournissent des fonctionnalités améliorées dans votre application. Elles comprennent :

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

Pour plus d’informations, consultez [Classes de contrôle](../mfc/control-classes.md), [Classes de boîte de dialogue](../mfc/dialog-box-classes.md), et [Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

## <a name="custom-controls"></a>Contrôles personnalisés

L’éditeur de boîtes de dialogue vous permet d’utiliser l’existant « custom » ou des contrôles dans un modèle de boîte de dialogue « utilisateur ».

> [!NOTE]
> Contrôles personnalisés dans ce sens doivent ne pas être confondus avec les contrôles ActiveX. Contrôles ActiveX étaient parfois appelés contrôles personnalisés OLE. En outre, ne confondez pas ces contrôles avec les contrôles owner-drawn dans Windows.

Cette fonctionnalité vise à vous permettent d’utiliser des contrôles autres que ceux fournis par Windows. Au moment de l’exécution, le contrôle est associé à une classe de fenêtre (pas identique à une classe C++). Une façon plus courante pour accomplir la même tâche consiste à installer n’importe quel contrôle, tel qu’un contrôle statique, dans votre boîte de dialogue. Puis au moment de l’exécution, dans le [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fonctionner, supprimez ce contrôle et remplacez-le par votre propre contrôle personnalisé.

Il s’agit d’une vieille méthode. Aujourd'hui, il est conseillé dans la plupart des cas d’écrire un contrôle ActiveX ou une sous-classe un contrôle commun de Windows.

Pour ces contrôles personnalisés, vous êtes limité à :

- Définition de l’emplacement dans la boîte de dialogue.

- Taper une légende.

- Identifiant le nom de la classe du contrôle Windows (code de votre application doit inscrire le contrôle par son nom).

- Taper une valeur hexadécimale 32 bits qui définit le style du contrôle.

- Définir le style étendu.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)<br/>
[Contrôles](../mfc/controls-mfc.md)<br/>