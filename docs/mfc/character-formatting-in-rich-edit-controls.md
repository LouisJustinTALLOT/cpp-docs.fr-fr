---
title: Formatage de caractères dans les contrôles RichEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02165635e8715c1fcac28b9fbee72612b72c1f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349478"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Mise en forme des caractères dans les contrôles RichEdit
Vous pouvez utiliser les fonctions membres du contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour le formatage de caractères et pour récupérer les informations de mise en forme. Pour les caractères, vous pouvez spécifier des caractères, la taille, couleur et effets tels que gras, italique et protégés.  
  
 Vous pouvez appliquer la mise en forme de caractères à l’aide de la [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) et [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) fonctions membres. Pour déterminer le caractère actuel de mise en forme pour le texte sélectionné, utilisez le [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) fonction membre. Le [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) structure est utilisée avec ces fonctions membres pour spécifier des attributs de caractère. Un des membres importants de **CHARFORMAT** est **dwMask**. Dans `SetSelectionCharFormat` et `SetWordCharFormat`, **dwMask** spécifie quels attributs de caractères seront définis par cet appel de fonction. `GetSelectionCharFormat` Indique les attributs du premier caractère de la sélection ; **dwMask** spécifie les attributs qui sont cohérentes dans la sélection.  
  
 Vous pouvez également obtenir et définir la « valeur par défaut mise en forme, » qui est appliqué à tous les caractères insérés par la suite de la mise en forme. Par exemple, si une application définit le caractère par défaut de mise en forme gras et que l’utilisateur entre un caractère, ce caractère est en gras. Pour obtenir et définir la mise en forme de caractères par défaut, utilisez le [fonctions membres GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) et [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) fonctions membres.  
  
 L’attribut de caractère « protégé » ne modifie pas l’apparence du texte. Si l’utilisateur tente de modifier du texte protégé, un contrôle RichEdit envoie sa fenêtre parente un **EN_PROTECTED** message de notification, ce qui permet de la fenêtre parente autoriser ou empêcher la modification. Pour recevoir ce message de notification, vous devez l’activer à l’aide de la [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) fonction membre. Pour plus d’informations sur le masque d’événement, consultez [des Notifications à partir d’un contrôle RichEdit](../mfc/notifications-from-a-rich-edit-control.md), plus loin dans cette rubrique.  
  
 Couleur de premier plan est un attribut de caractère, mais la couleur d’arrière-plan est une propriété du contrôle RichEdit. Pour définir la couleur d’arrière-plan, utilisez la [fonction membre SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

