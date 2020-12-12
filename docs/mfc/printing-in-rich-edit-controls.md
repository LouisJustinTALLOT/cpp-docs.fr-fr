---
description: 'En savoir plus sur : impression dans les contrôles RichEdit'
title: Impression dans des contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 9b5c272df36c6a4472c82cc4b0655b1d9626c2ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205731"
---
# <a name="printing-in-rich-edit-controls"></a>Impression dans des contrôles RichEdit

Vous pouvez demander à un contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) d’afficher sa sortie pour un périphérique spécifié, tel qu’une imprimante. Vous pouvez également spécifier le périphérique de sortie pour lequel un contrôle RichEdit met en forme son texte.

Pour mettre en forme une partie du contenu d’un contrôle Rich Edit pour un appareil spécifique, vous pouvez utiliser la fonction membre [FormatRange](reference/cricheditctrl-class.md#formatrange) . La structure [FormatRange](/windows/win32/api/richedit/ns-richedit-formatrange) utilisée avec cette fonction spécifie la plage de texte à mettre en forme, ainsi que le contexte de périphérique (DC) du périphérique cible.

Après la mise en forme du texte pour un périphérique de sortie, vous pouvez envoyer la sortie à l’appareil à l’aide de la fonction membre [DisplayBand](reference/cricheditctrl-class.md#displayband) . En utilisant de façon répétée `FormatRange` et `DisplayBand` , une application qui imprime le contenu d’un contrôle RichEdit peut implémenter des bandes. (Le regroupement est la Division de la sortie en plus petites parties à des fins d’impression.)

Vous pouvez utiliser la fonction membre [SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice) pour spécifier le périphérique cible pour lequel un contrôle RichEdit met en forme son texte. Cette fonction est utile pour la mise en forme WYSIWYG (ce que vous obtenez), dans laquelle une application positionne le texte en utilisant les mesures de police de l’imprimante par défaut à la place de l’écran.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
