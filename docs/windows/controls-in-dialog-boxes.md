---
description: 'En savoir plus sur : contrôles de boîte de dialogue (C++)'
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
ms.openlocfilehash: e68547ebd550797d4ad195c6bef4c3f2a71e769e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327146"
---
# <a name="dialog-box-controls-c"></a>Contrôles de boîte de dialogue (C++)

Vous pouvez ajouter des contrôles à une boîte de dialogue à l’aide de l’onglet **éditeur de boîtes de dialogue** de la [fenêtre boîte à outils](/visualstudio/ide/reference/toolbox) , qui vous permet de choisir le contrôle souhaité et de le faire glisser dans la boîte de dialogue. Par défaut, la fenêtre **boîte à outils** a la valeur Masquer automatiquement. Il apparaît sous la forme d’un onglet dans la marge gauche de votre solution lorsque l' **éditeur de boîtes de dialogue** est ouvert. Toutefois, vous pouvez épingler la fenêtre **boîte à outils** à la position en sélectionnant le bouton **Masquer automatiquement** dans le coin supérieur droit de la fenêtre. Pour plus d’informations sur la façon de contrôler le comportement de cette fenêtre, consultez [gestion des fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le moyen le plus rapide d’ajouter des contrôles à une boîte de dialogue, de repositionner des contrôles existants ou de déplacer des contrôles d’une boîte de dialogue à une autre, consiste à utiliser la méthode de glisser-déplacer. La position du contrôle est présentée dans une ligne pointillée jusqu’à ce qu’elle soit insérée dans la boîte de dialogue. Lorsque vous ajoutez un contrôle à une boîte de dialogue avec la méthode de glisser-déplacer, le contrôle reçoit une hauteur standard appropriée à ce type de contrôle.

Lorsque vous ajoutez un contrôle à une boîte de dialogue ou le repositionnez, son emplacement final peut être déterminé par des repères ou des marges, ou si vous avez activé la grille de disposition.

Une fois que vous avez ajouté un contrôle à la boîte de dialogue, vous pouvez modifier des propriétés telles que sa légende dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez également sélectionner plusieurs contrôles et modifier leurs propriétés en même temps.

Pour plus d’informations sur **l’éditeur de boîtes de dialogue**, consultez Comment [Ajouter, modifier ou supprimer des contrôles](adding-editing-or-deleting-controls.md), mettre [en page des contrôles](../windows/arrangement-of-controls-on-dialog-boxes.md)et [définir l’accès aux contrôles et les valeurs](../windows/defining-mnemonics-access-keys.md).

Pour plus d’informations sur les contrôles et les boîtes de dialogue, consultez [classes de contrôle](../mfc/control-classes.md), classes de [boîte de dialogue](../mfc/dialog-box-classes.md)et [styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Les contrôles standard disponibles dans la **boîte à outils** avec des événements par défaut sont les suivants :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle Button](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Contrôle Check Box ](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Combo Box](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Contrôle Edit](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Contrôle Group box|(non applicable)|
|[Contrôle zone de liste](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Static Text](../mfc/reference/cstatic-class.md)|(non applicable)|
|[Contrôle Picture](../mfc/reference/cpictureholder-class.md)|(non applicable)|
|[Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Pour plus d’informations sur l’utilisation du contrôle **richedit 1,0** avec MFC, consultez [utilisation du contrôle RichEdit 1,0 avec MFC](./adding-editing-or-deleting-controls.md) et des [exemples de contrôles](../mfc/rich-edit-control-examples.md)RichEdit.

Les [contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans la **boîte à outils** pour offrir des fonctionnalités améliorées sont les suivants :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle de curseur](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Contrôle Spin](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Contrôle Progress](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Contrôle Hot Key](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Contrôle List](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Contrôle Tree](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Contrôle Tab](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Contrôle Animation](../mfc/using-an-animation-control.md)|ACN_START|
|[Contrôle de sélecteur de date et heure](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Contrôle Month Calendar](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Contrôle d’adresse IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Contrôle Extended Combo Box](../mfc/creating-an-extended-combo-box-control.md)||
|Contrôle personnalisé|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Contrôles personnalisés

L' **éditeur de boîtes de dialogue** vous permet d’utiliser des contrôles utilisateur ou personnalisés existants dans un modèle de boîte de dialogue.

> [!NOTE]
> Dans ce sens, les contrôles personnalisés ne doivent pas être confondus avec les contrôles ActiveX. Les contrôles ActiveX étaient parfois appelés contrôles personnalisés OLE. En outre, ne confondez pas ces contrôles avec les contrôles owner-drawn dans Windows.

Cette fonctionnalité est conçue pour vous permettre d’utiliser des contrôles autres que ceux fournis par Windows. Au moment de l’exécution, le contrôle est associé à une classe de fenêtre (et non à une classe C++). Une méthode plus courante pour accomplir la même tâche consiste à installer n’importe quel contrôle, tel qu’un contrôle statique, dans votre boîte de dialogue. Ensuite, au moment de l’exécution, dans la fonction [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) , supprimez ce contrôle et remplacez-le par votre propre contrôle personnalisé.

> [!NOTE]
> Il s’agit d’une ancienne technique. Aujourd’hui, il est recommandé dans la plupart des cas d’écrire un contrôle ActiveX ou une sous-classe un contrôle commun Windows.

Pour ces contrôles personnalisés, vous êtes limité à :

- Définition de l’emplacement dans la boîte de dialogue.

- Saisie d’une légende.

- Identifiant le nom de la classe Windows du contrôle, car votre code d’application doit inscrire le contrôle par ce nom.

- Saisie d’une valeur hexadécimale 32 bits qui définit le style du contrôle.

- Définition du style étendu.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](./adding-editing-or-deleting-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
