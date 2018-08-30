---
title: Opérations du Presse-papiers dans les contrôles Edit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb207b31da27041ee777277e7e76502789402ab7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216228"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Opérations du Presse-papiers dans les contrôles RichEdit
Votre application peut coller le contenu du Presse-papiers dans un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) à l’aide du format de Presse-papiers mieux disponible ou un format de Presse-papiers spécifique. Vous pouvez également déterminer si un contrôle RichEdit est capable de coller un format de Presse-papiers.  
  
 Vous pouvez copier ou couper le contenu de la sélection actuelle à l’aide de la [copie](../mfc/reference/cricheditctrl-class.md#copy) ou [couper](../mfc/reference/cricheditctrl-class.md#cut) fonction membre. De même, vous pouvez coller le contenu du Presse-papiers dans un contrôle RichEdit à l’aide de la [collez](../mfc/reference/cricheditctrl-class.md#paste) fonction membre. Le contrôle colle le premier format disponible qu’elle reconnaît, qui est vraisemblablement le format le plus descriptif.  
  
 Pour coller un format de Presse-papiers spécifique, vous pouvez utiliser la [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) fonction membre. Cette fonction est utile pour les applications avec une commande Collage spécial qui permet à l’utilisateur de sélectionner le format de Presse-papiers. Vous pouvez utiliser la [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) fonction membre pour déterminer si un format donné est reconnu par le contrôle.  
  
 Vous pouvez également utiliser `CanPaste` pour déterminer si n’importe quel format de Presse-papiers disponible est reconnu par un contrôle RichEdit. Cette fonction est utile dans les `OnInitMenuPopup` gestionnaire. Une application peut activer ou griser sa commande Collage selon si le contrôle peut coller n’importe quel format disponible.  
  
 Contrôles RichEdit enregistrent deux formats de Presse-papiers : format de texte enrichi et un format appelé RichEdit Text and Objects. Une application peut enregistrer ces formats à l’aide de la [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) fonctionner, en spécifiant le **CF_RTF** et **CF_RETEXTOBJ** valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

