---
description: 'En savoir plus sur : initialisation de la boîte de dialogue'
title: Initialisation de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 317098a8c0cc745bbd4c94b9ed02401774cb0df9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197619"
---
# <a name="initializing-the-dialog-box"></a>Initialisation de la boîte de dialogue

Après la création de la boîte de dialogue et de tous ses contrôles, mais juste avant que la boîte de dialogue (de l’un des deux types) apparaisse sur l’écran, la fonction membre [OnInitDialog](reference/cdialog-class.md#oninitdialog) de l’objet Dialog est appelée. Pour une boîte de dialogue modale, cela se produit pendant l' `DoModal` appel. Pour une boîte de dialogue non modale, `OnInitDialog` est appelé quand `Create` est appelé. En général, vous substituez `OnInitDialog` pour initialiser les contrôles de la boîte de dialogue, par exemple en définissant le texte initial d’une zone d’édition. Vous devez appeler la `OnInitDialog` fonction membre de la classe de base, `CDialog` , à partir de votre `OnInitDialog` remplacement.

Si vous souhaitez définir la couleur d’arrière-plan de la boîte de dialogue (et celle de toutes les autres boîtes de dialogue de votre application), consultez [définition de la couleur d’arrière-plan de la boîte de dialogue](setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
