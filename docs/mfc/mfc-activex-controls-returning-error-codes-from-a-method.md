---
description: 'En savoir plus sur : contrôles ActiveX MFC : retour de codes d’erreur à partir d’une méthode'
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
ms.openlocfilehash: f6a1f372442ee67787a7a5421dabb4460acfcc7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206069"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode

Cet article explique comment retourner des codes d’erreur à partir d’une méthode de contrôle ActiveX.

Pour indiquer qu’une erreur s’est produite dans une méthode, vous devez utiliser la fonction membre [COleControl :: ThrowError](reference/colecontrol-class.md#throwerror) , qui prend un SCODE (code d’État) comme paramètre. Vous pouvez utiliser un SCODE prédéfini ou définir l’un de vos propres.

> [!NOTE]
> `ThrowError` est destiné à être utilisé uniquement comme moyen de retourner une erreur à partir d’une fonction d’extraction ou de définition d’une propriété ou d’une méthode Automation. Il s’agit de la seule fois où le gestionnaire d’exceptions approprié sera présent sur la pile.

Les fonctions d’assistance existent pour les SCODEs prédéfinis les plus courants, tels que [COleControl :: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl :: GetNotSupported](reference/colecontrol-class.md#getnotsupported)et [COleControl :: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

Pour obtenir la liste des SCODEs prédéfinis et des instructions sur la définition des SCODEs personnalisés, consultez la section [gestion des erreurs dans votre contrôle ActiveX](mfc-activex-controls-advanced-topics.md) dans contrôles ActiveX : Rubriques avancées.

Pour plus d’informations sur la création de rapports d’exceptions dans d’autres zones de votre code, consultez [COleControl :: FireError (](reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](mfc-activex-controls-advanced-topics.md) dans contrôles ActiveX : Rubriques avancées.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
