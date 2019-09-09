---
title: Opérations du Presse-papiers dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508967"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Opérations du Presse-papiers dans les contrôles RichEdit

Votre application peut coller le contenu du presse-papiers dans un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) à l’aide du meilleur format de presse-papiers disponible ou d’un format de presse-papiers spécifique. Vous pouvez également déterminer si un contrôle RichEdit peut coller un format de presse-papiers.

Vous pouvez copier ou couper le contenu de la sélection actuelle à l’aide de la fonction membre [Copy](../mfc/reference/cricheditctrl-class.md#copy) ou [Cut](../mfc/reference/cricheditctrl-class.md#cut) . De même, vous pouvez coller le contenu du presse-papiers dans un contrôle RichEdit à l’aide de la fonction membre [Paste](../mfc/reference/cricheditctrl-class.md#paste) . Le contrôle colle le premier format disponible qu’il reconnaît, ce qui est vraisemblablement le format le plus descriptif.

Pour coller un format de presse-papiers spécifique, vous pouvez utiliser la fonction membre [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) . Cette fonction est utile pour les applications avec une commande de collage spéciale qui permet à l’utilisateur de sélectionner le format du presse-papiers. Vous pouvez utiliser la fonction membre [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) pour déterminer si un format donné est reconnu par le contrôle.

Vous pouvez également utiliser `CanPaste` pour déterminer si un format de presse-papiers disponible est reconnu par un contrôle RichEdit. Cette fonction est utile dans le `OnInitMenuPopup` gestionnaire. Une application peut activer ou griser sa commande de collage, selon que le contrôle peut coller n’importe quel format disponible.

Les contrôles RichEdit inscrivent deux formats de presse-papiers : le format de texte enrichi et un format appelé texte et objets RichEdit. Une application peut inscrire ces formats à l’aide de la fonction [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) , en spécifiant les valeurs **CF_RTF** et **CF_RETEXTOBJ** .

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
