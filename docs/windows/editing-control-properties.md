---
title: Modification des propriétés du contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7976f74e9454b023c4da51168fa780ccaea2342
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873483"
---
# <a name="editing-control-properties"></a>Modification des propriétés d'un contrôle
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Pour modifier les propriétés d’un contrôle ou de contrôles  
  
1.  Dans la boîte de dialogue, sélectionnez le contrôle que vous souhaitez modifier.  
  
    > [!NOTE]
    >  Si vous sélectionnez plusieurs contrôles, uniquement des propriétés communes aux contrôles sélectionnés peuvent être modifiées.  
  
2.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifier les propriétés de votre contrôle.  
  
    > [!NOTE]
    >  Lorsque vous définissez la **Bitmap** propriété pour un bouton, une case d’option ou un contrôle de case à cocher égal à **True**, le style BS_BITMAP est implémenté pour votre contrôle. Pour plus d’informations, consultez [les Styles de bouton](../mfc/reference/styles-used-by-mfc.md#button-styles). Pour obtenir un exemple d’association d’une image bitmap à un contrôle, consultez [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Lorsque vous vous trouvez dans l’éditeur de ressources de boîte de dialogue, les bitmaps n’apparaissent pas sur votre contrôle.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Pour annuler les modifications apportées aux propriétés d’un contrôle  
  
1.  Assurez-vous que le contrôle a le focus dans l’éditeur de boîte de dialogue.  
  
2.  Choisissez **Annuler** à partir de la **modifier** menu (si le focus ne se trouve pas sur le contrôle, le **Annuler** n’est pas disponible).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, et ceci manuellement, consultez [Procédure pas à pas : localisation des applications Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)

