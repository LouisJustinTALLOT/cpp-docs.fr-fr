---
description: En savoir plus sur les opérations du presse-papiers dans les contrôles RichEdit
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
ms.openlocfilehash: 9a9fda9aebe3a749359776c1bc0d41e75deaef76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251204"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Opérations du Presse-papiers dans les contrôles RichEdit

Votre application peut coller le contenu du presse-papiers dans un contrôle RichEdit ([CRichEditCtrl](reference/cricheditctrl-class.md)) à l’aide du meilleur format de presse-papiers disponible ou d’un format de presse-papiers spécifique. Vous pouvez également déterminer si un contrôle RichEdit peut coller un format de presse-papiers.

Vous pouvez copier ou couper le contenu de la sélection actuelle à l’aide de la fonction membre [Copy](reference/cricheditctrl-class.md#copy) ou [Cut](reference/cricheditctrl-class.md#cut) . De même, vous pouvez coller le contenu du presse-papiers dans un contrôle RichEdit à l’aide de la fonction membre [Paste](reference/cricheditctrl-class.md#paste) . Le contrôle colle le premier format disponible qu’il reconnaît, ce qui est vraisemblablement le format le plus descriptif.

Pour coller un format de presse-papiers spécifique, vous pouvez utiliser la fonction membre [PasteSpecial](reference/cricheditctrl-class.md#pastespecial) . Cette fonction est utile pour les applications avec une commande de collage spéciale qui permet à l’utilisateur de sélectionner le format du presse-papiers. Vous pouvez utiliser la fonction membre [CanPaste](reference/cricheditctrl-class.md#canpaste) pour déterminer si un format donné est reconnu par le contrôle.

Vous pouvez également utiliser `CanPaste` pour déterminer si un format de presse-papiers disponible est reconnu par un contrôle RichEdit. Cette fonction est utile dans le `OnInitMenuPopup` Gestionnaire. Une application peut activer ou griser sa commande de collage, selon que le contrôle peut coller n’importe quel format disponible.

Les contrôles RichEdit inscrivent deux formats de presse-papiers : le format de texte enrichi et un format appelé texte et objets RichEdit. Une application peut inscrire ces formats à l’aide de la fonction [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) , en spécifiant les valeurs **CF_RTF** et **CF_RETEXTOBJ** .

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
