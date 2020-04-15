---
title: "Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode"
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364557"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode

Cet article décrit comment retourner les codes d’erreur d’une méthode de contrôle ActiveX.

Pour indiquer qu’une erreur s’est produite dans le cadre d’une méthode, vous devez utiliser le [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) fonction membre, qui prend un SCODE (code d’état) comme un paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir l’un des vôtres.

> [!NOTE]
> `ThrowError`est destiné à être utilisé uniquement comme un moyen de retourner une erreur à l’intérieur d’une propriété Get or Set fonction ou une méthode d’automatisation. Ce sont les seules fois où le gestionnaire d’exception approprié sera présent sur la pile.

Les fonctions d’aide existent pour les SCODE prédéfinis les plus communs, telles que [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Pour une liste de SCODE prédéfinis et des instructions sur la définition des SCODE personnalisés, consultez la section [Fautes de manipulation dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans activeX Controls: Advanced Topics.

Pour plus d’informations sur les exceptions de rapport dans d’autres domaines de votre code, voir [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [Fautes de manipulation dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans activeX Controls: Advanced Topics.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
