---
title: Opérations de flux dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 04bf49371b3ab5eaaad2775b532d8d35bf990ce3
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915285"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Opérations de flux dans les contrôles RichEdit

Vous pouvez utiliser des flux pour transférer des données vers ou à partir d’un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Un flux est défini par une structure [EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-editstream) , qui spécifie une mémoire tampon et une fonction de rappel définie par l’application.

Pour lire des données dans un contrôle Rich Edit (autrement dit, transmettre les données en continu), utilisez la fonction membre [Stream](../mfc/reference/cricheditctrl-class.md#streamin) . Le contrôle appelle à plusieurs reprises la fonction de rappel définie par l’application, qui transfère à chaque fois une partie des données dans la mémoire tampon.

Pour enregistrer le contenu d’un contrôle RichEdit (autrement dit, transmettre en continu les données), vous pouvez utiliser la fonction membre [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) . Le contrôle écrit à plusieurs reprises dans la mémoire tampon, puis appelle la fonction de rappel définie par l’application. Pour chaque appel, la fonction de rappel enregistre le contenu de la mémoire tampon.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
