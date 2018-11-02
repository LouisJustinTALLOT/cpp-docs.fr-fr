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
ms.openlocfilehash: 8c5fe88cf952337a7d070eae7a5da149a8e905bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676484"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode

Cet article décrit comment retourner des codes d’erreur à partir d’une méthode de contrôle ActiveX.

Pour indiquer qu’une erreur s’est produite dans une méthode, vous devez utiliser le [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) fonction membre, qui prend SCODE (code d’état) en tant que paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir votre propre.

> [!NOTE]
>  `ThrowError` est destiné à être utilisé uniquement comme un moyen de retourner une erreur à partir d’au sein Get d’une propriété ou Set fonction ou une méthode automation. Il s’agit de la seule fois où le Gestionnaire d’exceptions approprié sera présent sur la pile.

Fonctions d’assistance existent pour la plus courante prédéfinies SCODEs, tel que [courants ;](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Pour obtenir la liste de paramètres prédéfinis SCODEs et obtenir des instructions sur la définition SCODEs personnalisés, consultez la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.

Pour plus d’informations sur le rapport des exceptions dans d’autres zones de votre code, consultez [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

