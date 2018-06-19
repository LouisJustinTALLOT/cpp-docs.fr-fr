---
title: Flux des opérations dans les contrôles RichEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66afb05031b302877dfd34f64e6076f882a256d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379923"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Opérations de flux dans les contrôles RichEdit
Vous pouvez utiliser des flux pour transférer des données dans ou hors d’un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Un flux de données est défini par une [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) structure, qui spécifie une mémoire tampon et une fonction de rappel définie par l’application.  
  
 Pour lire les données dans une riche contrôle d’édition (autrement dit, le flux de données dans), utilisez la [fonction membre StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) fonction membre. Le contrôle appelle à plusieurs reprises la fonction de rappel définie par l’application, qui transfère une partie des données dans la mémoire tampon chaque fois.  
  
 Pour enregistrer le contenu d’une riche contrôle d’édition (autrement dit, le flux sortant de données), vous pouvez utiliser la [fonction membre StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) fonction membre. Le contrôle à plusieurs reprises écrit dans la mémoire tampon, puis appelle la fonction de rappel définie par l’application. Pour chaque appel, la fonction de rappel enregistre le contenu de la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

