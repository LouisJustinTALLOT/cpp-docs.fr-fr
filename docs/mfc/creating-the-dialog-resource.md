---
title: Création de la ressource de boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c68f8f48ec08446a9fca20524a8309b041607a92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401587"
---
# <a name="creating-the-dialog-resource"></a>Création des ressources de boîte de dialogue

À la conception de la [boîte de dialogue](../mfc/dialog-boxes.md) et créer la ressource de boîte de dialogue, vous utilisez le [éditeur de boîte de dialogue](../windows/dialog-editor.md). Dans l’éditeur de boîtes de dialogue, vous pouvez :

- Ajuster la taille et l’emplacement de que votre boîte de dialogue aura lorsqu’il apparaît.

- Différents types de contrôles à partir d’une palette de contrôles glisser -déplacer les où vous le souhaitez dans la boîte de dialogue.

- Positionner les contrôles avec des boutons d’alignement sur la barre d’outils.

- Tester votre boîte de dialogue en simulant l’apparence et le comportement dans votre programme. En mode Test, vous pouvez manipuler les contrôles de la boîte de dialogue en tapant du texte dans les zones de texte, en cliquant sur les boutons de commande et ainsi de suite.

Lorsque vous avez terminé, votre ressource de modèle est stocké dans le fichier de script de ressources de votre application. Vous pouvez la modifier ultérieurement si nécessaire. Pour obtenir une description complète de la création et de modifier des ressources de la boîte de dialogue, consultez la [éditeur de boîte de dialogue](../windows/dialog-editor.md) rubriques. Cette technique est également utilisée pour créer les ressources de modèle de boîte de dialogue de [CFormView](../mfc/reference/cformview-class.md) et [CRecordView](../mfc/reference/crecordview-class.md) classes.

Lors de l’apparence de la boîte de dialogue vous convient le mieux, créez une classe de boîte de dialogue et mappez ses messages, comme indiqué dans [création d’une classe de boîte de dialogue avec les Assistants Code](../mfc/creating-a-dialog-class-with-code-wizards.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

