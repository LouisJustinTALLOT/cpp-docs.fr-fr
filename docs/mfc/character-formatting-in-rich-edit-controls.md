---
description: 'En savoir plus sur : la mise en forme des caractères dans les contrôles RichEdit'
title: Mise en forme des caractères dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 47d44a7d586d52ba6a83314711af1350d1c2def6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339694"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Mise en forme des caractères dans les contrôles RichEdit

Vous pouvez utiliser des fonctions membres du contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) pour mettre en forme des caractères et récupérer des informations de mise en forme. Pour les caractères, vous pouvez spécifier la police, la taille, la couleur et les effets tels que gras, italique et protégé.

Vous pouvez appliquer la mise en forme des caractères à l’aide des fonctions membres [SetSelectionCharFormat](reference/cricheditctrl-class.md#setselectioncharformat) et [SetWordCharFormat](reference/cricheditctrl-class.md#setwordcharformat) . Pour déterminer la mise en forme de caractères actuelle pour le texte sélectionné, utilisez la fonction membre [GetSelectionCharFormat](reference/cricheditctrl-class.md#getselectioncharformat) . La structure [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) est utilisée avec ces fonctions membres pour spécifier des attributs de caractères. L’un des membres importants de **Charformat** est **dwMask**. Dans `SetSelectionCharFormat` et `SetWordCharFormat` , **dwMask** spécifie les attributs de caractères qui seront définis par cet appel de fonction. `GetSelectionCharFormat` signale les attributs du premier caractère de la sélection. **dwMask** spécifie les attributs qui sont cohérents tout au long de la sélection.

Vous pouvez également récupérer et définir la « mise en forme de caractères par défaut », qui est la mise en forme appliquée à tous les caractères insérés par la suite. Par exemple, si une application définit la mise en forme de caractère par défaut sur gras et que l’utilisateur tape ensuite un caractère, ce caractère est gras. Pour récupérer et définir la mise en forme des caractères par défaut, utilisez les fonctions membres [GetDefaultCharFormat](reference/cricheditctrl-class.md#getdefaultcharformat) et [SetDefaultCharFormat](reference/cricheditctrl-class.md#setdefaultcharformat) .

L’attribut de caractère « protégé » ne modifie pas l’apparence du texte. Si l’utilisateur tente de modifier du texte protégé, un contrôle RichEdit envoie une **EN_PROTECTED** message de notification à la fenêtre parente, ce qui permet à la fenêtre parente d’autoriser ou d’empêcher la modification. Pour recevoir ce message de notification, vous devez l’activer à l’aide de la fonction membre [SetEventMask](reference/cricheditctrl-class.md#seteventmask) . Pour plus d’informations sur le masque d’événement, consultez [notifications à partir d’un contrôle](notifications-from-a-rich-edit-control.md)RichEdit, plus loin dans cette rubrique.

La couleur de premier plan est un attribut de caractère, mais la couleur d’arrière-plan est une propriété du contrôle RichEdit. Pour définir la couleur d’arrière-plan, utilisez la fonction membre [SetBackgroundColor](reference/cricheditctrl-class.md#setbackgroundcolor) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
