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
ms.openlocfilehash: 882c589d0d25b54650affa7fd41f916ecf6097d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276869"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Opérations du Presse-papiers dans les contrôles RichEdit

Votre application peut coller le contenu du Presse-papiers dans un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) à l’aide du format de Presse-papiers mieux disponible ou un format de Presse-papiers spécifique. Vous pouvez également déterminer si un contrôle RichEdit est capable de coller un format de Presse-papiers.

Vous pouvez copier ou couper le contenu de la sélection actuelle à l’aide de la [copie](../mfc/reference/cricheditctrl-class.md#copy) ou [couper](../mfc/reference/cricheditctrl-class.md#cut) fonction membre. De même, vous pouvez coller le contenu du Presse-papiers dans un contrôle RichEdit à l’aide de la [collez](../mfc/reference/cricheditctrl-class.md#paste) fonction membre. Le contrôle colle le premier format disponible qu’elle reconnaît, qui est vraisemblablement le format le plus descriptif.

Pour coller un format de Presse-papiers spécifique, vous pouvez utiliser la [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) fonction membre. Cette fonction est utile pour les applications avec une commande Collage spécial qui permet à l’utilisateur de sélectionner le format de Presse-papiers. Vous pouvez utiliser la [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) fonction membre pour déterminer si un format donné est reconnu par le contrôle.

Vous pouvez également utiliser `CanPaste` pour déterminer si n’importe quel format de Presse-papiers disponible est reconnu par un contrôle RichEdit. Cette fonction est utile dans les `OnInitMenuPopup` gestionnaire. Une application peut activer ou griser sa commande Collage selon si le contrôle peut coller n’importe quel format disponible.

Contrôles RichEdit enregistrent deux formats de Presse-papiers : format de texte enrichi et un format appelé RichEdit Text and Objects. Une application peut enregistrer ces formats à l’aide de la [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) fonctionner, en spécifiant le **CF_RTF** et **CF_RETEXTOBJ** valeurs.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
