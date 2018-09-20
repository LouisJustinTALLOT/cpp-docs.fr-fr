---
title: Création et affichage de boîtes de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 437fb934e95ce527a77038d643e9cee86b6f1f2c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387742"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Création et affichage de boîtes de dialogue

Création d’un objet de la boîte de dialogue est une opération en deux phases. Tout d’abord, construisez l’objet de la boîte de dialogue, puis créer la fenêtre de la boîte de dialogue. Boîtes de dialogue modales et non modales diffèrent légèrement dans le processus utilisé pour créer et de les afficher. Le tableau suivant répertorie comment modales et non modales boîtes de dialogue sont normalement construites et affichées.

### <a name="dialog-creation"></a>Création de la boîte de dialogue

|Type de la boîte de dialogue|Méthode de création|
|-----------------|----------------------|
|[Non modal](../mfc/creating-modeless-dialog-boxes.md)|Construire `CDialog`, puis appelez `Create` fonction membre.|
|[Modale](../mfc/creating-modal-dialog-boxes.md)|Construire `CDialog`, puis appelez `DoModal` fonction membre.|

Vous pouvez, si vous le souhaitez, votre boîte de dialogue Créer à partir d’un [modèle de boîte de dialogue en mémoire](../mfc/using-a-dialog-template-in-memory.md) que vous avez construit plutôt qu’à partir d’une ressource de modèle de boîte de dialogue. Il s’agit toutefois une rubrique avancée.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

