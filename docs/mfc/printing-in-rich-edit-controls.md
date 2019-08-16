---
title: Impression dans des contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 671aec27584af975ce1635793ae80879e7208d4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508009"
---
# <a name="printing-in-rich-edit-controls"></a>Impression dans des contrôles RichEdit

Vous pouvez demander à un contrôle Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) d’afficher sa sortie pour un périphérique spécifié, tel qu’une imprimante. Vous pouvez également spécifier le périphérique de sortie pour lequel un contrôle RichEdit met en forme son texte.

Pour mettre en forme une partie du contenu d’un contrôle Rich Edit pour un appareil spécifique, vous pouvez utiliser la fonction membre [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) . La structure [FormatRange](/windows/win32/api/richedit/ns-richedit-formatrange) utilisée avec cette fonction spécifie la plage de texte à mettre en forme, ainsi que le contexte de périphérique (DC) du périphérique cible.

Après la mise en forme du texte pour un périphérique de sortie, vous pouvez envoyer la sortie à l’appareil à l’aide de la fonction membre [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) . En utilisant `FormatRange` de façon répétée et `DisplayBand`, une application qui imprime le contenu d’un contrôle RichEdit peut implémenter des bandes. (Le regroupement est la Division de la sortie en plus petites parties à des fins d’impression.)

Vous pouvez utiliser la fonction membre [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) pour spécifier le périphérique cible pour lequel un contrôle RichEdit met en forme son texte. Cette fonction est utile pour la mise en forme WYSIWYG (ce que vous obtenez), dans laquelle une application positionne le texte en utilisant les mesures de police de l’imprimante par défaut à la place de l’écran.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
