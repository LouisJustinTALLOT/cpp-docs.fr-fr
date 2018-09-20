---
title: Utilisation d’un contrôle Header | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], working with
- header controls
ms.assetid: af3afb5c-bf97-451b-8fee-3adcb8257210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6da3ffd669ebd3d9cc02fc56a13acfa1fe804e7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381736"
---
# <a name="working-with-a-header-control"></a>Utilisation d'un contrôle Header

Le moyen facile d’utiliser un contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) en association avec un contrôle de liste ; consultez [utilisation de CListCtrl](../mfc/using-clistctrl.md) plus loin dans cette série de rubriques. Vous pouvez également utiliser un contrôle header par lui-même. MFC appelle `InitCommonControls` pour vous. Les tâches principales sont les suivantes :

- [Création du contrôle header](../mfc/creating-the-header-control.md)

- [Ajout d’éléments au contrôle header](../mfc/adding-items-to-the-header-control.md)

- [Organisation des éléments dans le contrôle header](../mfc/ordering-items-in-the-header-control.md)

- [Traitement des notifications de contrôle header](../mfc/processing-header-control-notifications.md)

Si l’objet de contrôle d’en-tête est incorporé dans une classe de vue ou de la boîte de dialogue parente, le contrôle est détruit lorsque le parent est détruit.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

