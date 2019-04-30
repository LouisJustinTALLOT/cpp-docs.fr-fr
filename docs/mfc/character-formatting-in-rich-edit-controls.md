---
title: Mise en forme des caractères dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: a7467f9cd6a14dc6dfc2c03b6eb35f71802454fb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344299"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Mise en forme des caractères dans les contrôles RichEdit

Vous pouvez utiliser les fonctions membres de contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour mettre en forme des caractères et récupérer des informations de mise en forme. Pour les caractères, vous pouvez spécifier de police, la taille, la couleur et des effets tels que le gras, italique et protégées.

Vous pouvez appliquer la mise en forme de caractères à l’aide de la [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) et [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) fonctions membres. Pour déterminer le caractère actuel de mise en forme pour le texte sélectionné, utilisez le [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) fonction membre. Le [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) structure est utilisée avec ces fonctions membres pour spécifier les attributs de caractère. Un des membres importants de **CHARFORMAT** est **dwMask**. Dans `SetSelectionCharFormat` et `SetWordCharFormat`, **dwMask** spécifie quels attributs de caractères seront définis par cet appel de fonction. `GetSelectionCharFormat` Indique les attributs du premier caractère dans la sélection ; **dwMask** spécifie les attributs qui sont cohérentes dans la sélection.

Vous pouvez également obtenir et définir la « valeur par défaut caractère mise en forme, » qui est appliqué à tous les caractères insérés par la suite de la mise en forme. Par exemple, si une application définit le caractère par défaut en gras la mise en forme et l’utilisateur entre un caractère, ce caractère est en gras. Pour obtenir et définir la mise en forme de caractères par défaut, utilisez le [fonctions membres GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) et [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) fonctions membres.

L’attribut de caractère « protégé » ne modifie pas l’apparence du texte. Si l’utilisateur tente de modifier du texte protégé, un contrôle rich edit envoie sa fenêtre parente un **EN_PROTECTED** message de notification, ce qui permet de la fenêtre parente autoriser ou empêcher la modification. Pour recevoir ce message de notification, vous devez l’activer à l’aide de la [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) fonction membre. Pour plus d’informations sur le masque d’événement, consultez [Notifications à partir d’un contrôle Rich Edit](../mfc/notifications-from-a-rich-edit-control.md), plus loin dans cette rubrique.

Couleur de premier plan est un attribut de caractère, mais la couleur d’arrière-plan est une propriété du contrôle RichEdit. Pour définir la couleur d’arrière-plan, utilisez la [fonction membre SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
