---
title: Sélection actuelle dans un contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: e493f46e2a2b5bec695177e8c8da9c09de13376d
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916454"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Sélection actuelle dans un contrôle RichEdit

L’utilisateur peut sélectionner du texte dans un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) à l’aide de la souris ou du clavier. La sélection actuelle correspond à la plage de caractères sélectionnés ou à la position du point d’insertion si aucun caractère n’est sélectionné. Une application peut obtenir des informations sur la sélection actuelle, définir la sélection actuelle, déterminer quand la sélection actuelle change et afficher ou masquer la sélection de la sélection.

Pour déterminer la sélection actuelle dans un contrôle RichEdit, utilisez la fonction membre [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) . Pour définir la sélection actuelle, utilisez la fonction membre [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) . La structure [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-charrange) est utilisée avec ces fonctions pour spécifier une plage de caractères. Pour récupérer des informations sur le contenu de la sélection actuelle, vous pouvez utiliser la fonction membre [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) .

Par défaut, un contrôle RichEdit affiche et masque la mise en surbrillance de la sélection quand elle gagne et perd le focus. Vous pouvez afficher ou masquer la sélection en surbrillance à tout moment à l’aide de la fonction membre [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) . Par exemple, une application peut fournir une boîte de dialogue de recherche pour rechercher du texte dans un contrôle RichEdit. L’application peut sélectionner du texte correspondant sans fermer la boîte de dialogue, auquel cas elle doit `HideSelection` utiliser pour mettre en surbrillance la sélection.

Pour obtenir le texte sélectionné dans un contrôle Rich Edit, utilisez la fonction membre [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) . Le texte est copié dans le tableau de caractères spécifié. Vous devez vous assurer que le tableau est suffisamment grand pour contenir le texte sélectionné, plus un caractère null de fin.

Vous pouvez rechercher une chaîne dans un contrôle Rich Edit à l’aide de la fonction membre [FindText](../mfc/reference/cricheditctrl-class.md#findtext) . la structure [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-findtextexa) utilisée avec cette fonction spécifie la plage de texte à rechercher et la chaîne à rechercher. Vous pouvez également spécifier des options comme si la recherche respecte la casse.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
