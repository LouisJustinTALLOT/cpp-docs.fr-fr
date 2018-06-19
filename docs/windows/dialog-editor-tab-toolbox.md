---
title: Onglet Éditeur de la boîte de dialogue, la boîte à outils | Documents Microsoft
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
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb7da9e08d44435570180859c1614f7817595833
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882574"
---
# <a name="dialog-editor-tab-toolbox"></a>Éditeur de boîtes de dialogue, onglet de la boîte à outils
L’onglet d’éditeur de boîte de dialogue s’affiche dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans l’éditeur de boîte de dialogue. Pour ajouter des contrôles à votre nouvelle boîte de dialogue, faites glisser les contrôles à partir de la boîte à outils vers la boîte de dialogue que vous créez (pour plus d’informations, consultez [Ajout d’un contrôle à une boîte de dialogue](adding-a-control-to-a-dialog-box.md)). Vous pouvez ensuite déplacer les contrôles ou modifier leur taille et leur forme.  
  
 Les contrôles standard disponibles dans la boîte à outils sont les suivants :  
  
-   [Contrôle de bouton](../mfc/reference/cbutton-class.md)  
  
-   [Contrôle de case à cocher](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Contrôle Combo Box](../mfc/reference/ccombobox-class.md)  
  
-   [Contrôle d’édition](../mfc/reference/cedit-class.md)  
  
-   Contrôle Group box  
  
-   [Contrôle de zone de liste](../mfc/reference/clistbox-class.md)  
  
-   [Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Contrôle Static Text](../mfc/reference/cstatic-class.md)  
  
-   [Contrôle d’image](../mfc/reference/cpictureholder-class.md)  
  
-   [Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)  
  
-   [Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)  
  
 Le [les contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans la boîte à outils fournissent des fonctionnalités améliorées dans votre application. Elles comprennent :  
  
-   [Contrôle Slider](../mfc/slider-control-styles.md)  
  
-   [Contrôle toupie](../mfc/using-cspinbuttonctrl.md)  
  
-   [Contrôle de progression](../mfc/styles-for-the-progress-control.md)  
  
-   [Contrôle Hot Key](../mfc/using-a-hot-key-control.md)  
  
-   [Contrôle de liste](../mfc/list-control-and-list-view.md)  
  
-   [Contrôle d’arborescence](../mfc/tree-control-styles.md)  
  
-   [Contrôle onglet](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Contrôle Animation](../mfc/using-an-animation-control.md)  
  
-   [Contrôle Date Time Picker](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Contrôle Month Calendar](../mfc/month-calendar-control-examples.md)  
  
-   [Contrôle d’adresse IP](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Contrôle Extended Combo Box](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Contrôle personnalisé](custom-controls-in-the-dialog-editor.md)  
  
 Vous pouvez ajouter des contrôles personnalisés à la boîte de dialogue en sélectionnant le **contrôle personnalisé** icône dans la boîte à outils et faites-la glisser vers votre boîte de dialogue. Pour ajouter un contrôle Syslink, ajoutez un contrôle personnalisé, puis modifiez le **classe** propriété **Syslink**. Cela entraînera l’actualisation des propriétés et l’affichage des propriétés du contrôle Syslink. Pour plus d’informations sur la classe wrapper MFC, consultez [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 Vous pouvez également [ajouter des contrôles ActiveX à votre boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Vous pouvez également personnaliser la fenêtre Boîte à outils pour faciliter son utilisation. Pour plus d’informations, consultez [Utilisation de la boîte à outils](/visualstudio/ide/using-the-toolbox).  

 Pour plus d’informations sur l’utilisation du contrôle RichEdit 1.0 avec MFC, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles](../mfc/controls-mfc.md)   
 [Classes de contrôle](../mfc/control-classes.md)   
 [Classes de boîte de dialogue](../mfc/dialog-box-classes.md)   
 [Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)   
 [Exemples du contrôle RichEdit](../mfc/rich-edit-control-examples.md)   
 [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)

