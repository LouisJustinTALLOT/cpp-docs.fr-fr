---
title: Ajout d’un contrôle à une boîte de dialogue (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293622"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>Ajout d’un contrôle à une boîte de dialogue (C++)

Le **boîte de dialogue Éditeur** onglet s’affiche dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans le **boîte de dialogue** éditeur. Pour ajouter des contrôles à votre nouvelle boîte de dialogue, faites glisser des contrôles à partir de la **boîte à outils** à la boîte de dialogue que vous créez. Vous pouvez ensuite déplacer les contrôles ou modifier leur taille et leur forme.

Les contrôles standards disponibles dans le **boîte à outils** sont :

- [Contrôle de bouton](../mfc/reference/cbutton-class.md)

- [Contrôle de case à cocher](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Contrôle Combo Box](../mfc/reference/ccombobox-class.md)

- [Contrôle d’édition](../mfc/reference/cedit-class.md)

- Contrôle Group box

- [Contrôle List Box](../mfc/reference/clistbox-class.md)

- [Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Contrôle Static Text](../mfc/reference/cstatic-class.md)

- [Contrôle d’image](../mfc/reference/cpictureholder-class.md)

- [Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)

- [Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)

Le [contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans le **boîte à outils** fournissent des fonctionnalités améliorées dans votre application. Elles comprennent :

- [Contrôle Slider](../mfc/slider-control-styles.md)

- [Contrôle Spin](../mfc/using-cspinbuttonctrl.md)

- [Contrôle de progression](../mfc/styles-for-the-progress-control.md)

- [Contrôle Hot Key](../mfc/using-a-hot-key-control.md)

- [Contrôle de liste](../mfc/list-control-and-list-view.md)

- [Contrôle d’arborescence](../mfc/tree-control-styles.md)

- [Contrôle onglet](../mfc/tab-controls-and-property-sheets.md)

- [Contrôle Animation](../mfc/using-an-animation-control.md)

- [Contrôle Date Time Picker](../mfc/creating-the-date-and-time-picker-control.md)

- [Contrôle Month Calendar](../mfc/month-calendar-control-examples.md)

- [Contrôle de l’adresse IP](../mfc/reference/cipaddressctrl-class.md)

- [Contrôle Extended Combo Box](../mfc/creating-an-extended-combo-box-control.md)

- [Contrôle personnalisé](custom-controls-in-the-dialog-editor.md)

Vous pouvez ajouter des contrôles personnalisés à la boîte de dialogue en sélectionnant le **contrôle personnalisé** icône dans le **boîte à outils** et faites-la glisser vers votre boîte de dialogue. Pour ajouter un **Syslink** contrôler, ajoutez un contrôle personnalisé, puis modifier le contrôle **classe** propriété **Syslink**. Ainsi, les propriétés actualiser et afficher le **Syslink** propriétés du contrôle. Pour plus d’informations sur la classe wrapper MFC, consultez [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

Vous pouvez également [ajouter des contrôles ActiveX à votre boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Vous pouvez également personnaliser le **boîte à outils** fenêtre pour faciliter son utilisation. Pour plus d’informations, consultez [Utilisation de la boîte à outils](/visualstudio/ide/using-the-toolbox).

Pour plus d’informations sur l’utilisation de la **RichEdit 1.0** contrôler avec MFC, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control-to-a-dialog-box"></a>Pour ajouter un contrôle à une boîte de dialogue

1. Assurez-vous que la fenêtre avec onglet de la boîte de dialogue représente le document actif dans le cadre de l’éditeur. Si une boîte de dialogue n’est pas le document actif, vous ne voyez pas le **onglet de boîte de dialogue Éditeur** dans le **boîte à outils**.

1. Sur le **boîte de dialogue Éditeur** onglet de la [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez le contrôle souhaité, puis :

   - Sélectionnez la boîte de dialogue à l’emplacement où vous souhaitez placer le contrôle. Le contrôle s’affiche où vous avez sélectionné.

       \- ou -

   - Faites glisser le contrôle à partir de la **boîte à outils** fenêtre à l’emplacement sur votre boîte de dialogue.

       \- ou -

   - Double-cliquez sur le contrôle dans le **boîte à outils** fenêtre (il apparaît dans votre boîte de dialogue), puis repositionnez le contrôle à l’emplacement de votre choix.

## <a name="to-add-multiple-controls"></a>Pour ajouter plusieurs contrôles

1. Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez un contrôle dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox).

1. Mise en production la **Ctrl** la clé, sélectionnez la boîte de dialogue autant de fois que vous souhaitez ajouter ce contrôle.

1. Appuyez sur **ÉCHAP** pour arrêter.

## <a name="to-size-a-control-while-you-add-it"></a>Pour dimensionner un contrôle pendant son ajout

1. Sélectionnez un contrôle dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox).

1. Placez votre curseur (qui apparaît comme forme de croix) à l’emplacement souhaité pour le coin supérieur gauche du nouveau contrôle doivent se trouver sur votre boîte de dialogue.

1. Sélectionnez et maintenez le bouton de la souris pour ancrer le coin supérieur gauche de votre contrôle sur la boîte de dialogue, puis faites glisser le curseur vers la droite et vers le bas jusqu'à ce que le contrôle est la taille voulue.

   > [!NOTE]
   > Vous pouvez ancrer n’importe lequel des quatre coins du contrôle que vous dessinez. Cette procédure utilisé le coin supérieur gauche comme exemple.

1. Relâchez le bouton de la souris. Le contrôle est placé dans la boîte de dialogue dans la taille spécifiée.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle après le déposant sur la boîte de dialogue en déplaçant les poignées de redimensionnement sur la bordure du contrôle. Pour plus d’informations, consultez [dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Contrôles](../mfc/controls-mfc.md)<br/>
[Classes de contrôle](../mfc/control-classes.md)<br/>
[Classes de boîte de dialogue](../mfc/dialog-box-classes.md)<br/>
[Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Exemples de contrôle RichEdit](../mfc/rich-edit-control-examples.md)<br/>
