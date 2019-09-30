---
title: Initialisation de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685625"
---
# <a name="initializing-the-dialog-box"></a>Initialisation de la boîte de dialogue

Après la création de la boîte de dialogue et de tous ses contrôles, mais juste avant que la boîte de dialogue (de l’un des deux types) apparaisse sur l’écran, la fonction membre [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) de l’objet Dialog est appelée. Pour une boîte de dialogue modale, cela se produit lors de l’appel de `DoModal`. Pour une boîte de dialogue non modale, `OnInitDialog` est appelé lorsque `Create` est appelé. En général, vous substituez `OnInitDialog` pour initialiser les contrôles de la boîte de dialogue, par exemple en définissant le texte initial d’une zone d’édition. Vous devez appeler la fonction membre `OnInitDialog` de la classe de base, `CDialog`, à partir de votre substitution `OnInitDialog`.

Si vous souhaitez définir la couleur d’arrière-plan de la boîte de dialogue (et celle de toutes les autres boîtes de dialogue de votre application), consultez [définition de la couleur d’arrière-plan de la boîte de dialogue](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
