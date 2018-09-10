---
title: Éditeur de boîte de dialogue, onglet de boîte à outils (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fa16a2cf15d5004ff80dda3188d79ffcba72ec1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316209"
---
# <a name="dialog-editor-tab-toolbox-c"></a>Éditeur de boîte de dialogue, onglet de boîte à outils (C++)

Le **boîte de dialogue Éditeur** onglet s’affiche dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans le **boîte de dialogue** éditeur. Pour ajouter des contrôles à votre nouvelle boîte de dialogue, faites glisser des contrôles à partir de la **boîte à outils** à la boîte de dialogue que vous créez (pour plus d’informations, consultez [Ajout d’un contrôle à une boîte de dialogue](adding-a-control-to-a-dialog-box.md)). Vous pouvez ensuite déplacer les contrôles ou modifier leur taille et leur forme.

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

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)  
[Classes de contrôle](../mfc/control-classes.md)  
[Classes de boîte de dialogue](../mfc/dialog-box-classes.md)  
[Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)  
[Exemples de contrôle RichEdit](../mfc/rich-edit-control-examples.md)  
[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)