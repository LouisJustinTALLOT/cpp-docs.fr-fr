---
title: 'Contrôles ActiveX MFC : Retour de Codes d’erreur à partir d’une méthode | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927917"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode
Cet article décrit comment retourner des codes d’erreur à partir d’une méthode de contrôle ActiveX.  
  
 Pour indiquer qu’une erreur s’est produite dans une méthode, vous devez utiliser le [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) fonction membre, qui prend SCODE (code d’état) en tant que paramètre. Vous pouvez utiliser un paramètre SCODE prédéfini ou définir votre propre.  
  
> [!NOTE]
>  `ThrowError` est destiné à être utilisé uniquement comme un moyen de retourner une erreur à partir d’au sein Get d’une propriété ou Set fonction ou une méthode automation. Il s’agit de la seule fois où le Gestionnaire d’exceptions approprié sera présent sur la pile.  
  
 Fonctions d’assistance existent pour la plus courante prédéfinies SCODEs, par exemple [courants ;](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Pour obtenir la liste de paramètres prédéfinis SCODEs et obtenir des instructions sur la définition de SCODEs personnalisés, consultez la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.  
  
 Pour plus d’informations sur les rapports d’exceptions dans d’autres zones de votre code, consultez [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

