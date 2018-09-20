---
title: Impression dans les contrôles RichEdit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38389f62ebeeaccf6b7b4c211b056b6f6c3ac188
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421321"
---
# <a name="printing-in-rich-edit-controls"></a>Impression dans des contrôles RichEdit

Vous pouvez indiquer à un contrôle rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour afficher sa sortie pour un périphérique spécifique, tel qu’une imprimante. Vous pouvez également spécifier le périphérique de sortie pour lequel un contrôle rich edit met en forme son texte.

Pour mettre en forme le contenu d’un contrôle RichEdit pour un périphérique spécifique, vous pouvez utiliser la [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) fonction membre. Le [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-_formatrange) structure utilisée avec cette fonction spécifie la plage de texte à mettre en forme, ainsi que le contexte de périphérique (DC) pour l’appareil cible.

Après la mise en forme de texte pour un périphérique de sortie, vous pouvez envoyer la sortie à l’appareil à l’aide de la [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) fonction membre. À l’aide de manière répétée `FormatRange` et `DisplayBand`, une application qui imprime le contenu d’un contrôle RichEdit peut implémenter de tranche. (Bandes concerne la division de la sortie en parties plus petites à des fins d’impression.)

Vous pouvez utiliser la [fonction membre SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) fonction membre pour spécifier le périphérique cible pour lequel un contrôle rich edit met en forme son texte. Cette fonction est utile pour WYSIWYG (ce que vous voyez ce que vous obtenez) mise en forme, dans laquelle une application place le texte à l’aide de la métrique des polices de l’imprimante par défaut au lieu de l’écran.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

