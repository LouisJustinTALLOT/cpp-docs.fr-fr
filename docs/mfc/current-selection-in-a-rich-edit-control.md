---
title: La sélection actuelle dans un contrôle Rich Edit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5870c7c3352a53d85bdd15020a1e7f535ef6efc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403667"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Sélection actuelle dans un contrôle RichEdit

L’utilisateur peut sélectionner le texte dans un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) à l’aide de la souris ou du clavier. La sélection actuelle est la plage de caractères sélectionnés, ou la position du point d’insertion si aucun caractère sont sélectionnés. Une application peut obtenir des informations sur la sélection actuelle, définir la sélection actuelle, déterminer quand mettre en surbrillance les modifications de sélection en cours et les afficher ou les masquer la sélection.

Pour déterminer la sélection actuelle dans un contrôle RichEdit, utilisez la [fonction membre GetSel](../mfc/reference/cricheditctrl-class.md#getsel) fonction membre. Pour définir la sélection actuelle, utilisez la [fonction membre SetSel](../mfc/reference/cricheditctrl-class.md#setsel) fonction membre. Le [structure CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) structure est utilisée avec ces fonctions pour spécifier une plage de caractères. Pour récupérer des informations sur le contenu de la sélection actuelle, vous pouvez utiliser la [fonction membre GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) fonction membre.

Par défaut, un contrôle rich edit affiche et masque la surbrillance de sélection lorsqu’il obtient et perd le focus. Vous pouvez afficher ou masquer la surbrillance de sélection à tout moment à l’aide de la [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) fonction membre. Par exemple, une application peut fournir une boîte de dialogue de recherche pour rechercher du texte dans un contrôle RichEdit. L’application peut sélectionner un texte correspondant sans fermer la boîte de dialogue, auquel cas vous devez utiliser `HideSelection` pour mettre en surbrillance de la sélection.

Pour obtenir le texte sélectionné dans un contrôle RichEdit, utilisez la [fonction membre GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) fonction membre. Le texte est copié dans le tableau de caractères spécifié. Vous devez vous assurer que le tableau est assez grand pour contenir le texte sélectionné plus un caractère null de fin.

Vous pouvez rechercher une chaîne dans un contrôle rich edit à l’aide de la [FindText](../mfc/reference/cricheditctrl-class.md#findtext) fonction membre la [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa) structure utilisée avec cette fonction spécifie la plage de texte à la recherche et la chaîne à rechercher. Vous pouvez également spécifier des options telles que si la recherche respecte la casse.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

