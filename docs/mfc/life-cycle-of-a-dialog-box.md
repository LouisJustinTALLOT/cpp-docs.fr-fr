---
title: Cycle de vie d’une boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05138040b6283b7af01f6e010bc371490aea495e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440496"
---
# <a name="life-cycle-of-a-dialog-box"></a>Cycle de vie d'une boîte de dialogue

Pendant le cycle de vie d’une boîte de dialogue, l’utilisateur appelle la boîte de dialogue, généralement à l’intérieur d’un gestionnaire de commandes qui crée et initialise l’objet de la boîte de dialogue, l’utilisateur interagit avec la boîte de dialogue, et la boîte de dialogue se ferme.

Pour les boîtes de dialogue modales, votre gestionnaire rassemble les données de l’utilisateur a entré une fois que la boîte de dialogue se ferme. Étant donné que l’objet de la boîte de dialogue existe après la fermeture de sa fenêtre de boîte de dialogue, vous pouvez simplement utiliser les variables de membre de votre classe de boîte de dialogue pour extraire les données.

Pour les boîtes de dialogue non modale, vous pouvez souvent extraire des données à partir de l’objet de la boîte de dialogue tandis que la boîte de dialogue est toujours visible. À un moment donné, la boîte de dialogue détruit ; Lorsque cela se produit dépend de votre code.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création et affichage de boîtes de dialogue](../mfc/creating-and-displaying-dialog-boxes.md)

- [Création de boîtes de dialogue modales](../mfc/creating-modal-dialog-boxes.md)

- [Création de boîtes de dialogue non modale](../mfc/creating-modeless-dialog-boxes.md)

- [À l’aide d’un modèle de boîte de dialogue en mémoire](../mfc/using-a-dialog-template-in-memory.md)

- [Définir la couleur d’arrière-plan de la boîte de dialogue](../mfc/setting-the-dialog-boxs-background-color.md)

- [Initialisation de la boîte de dialogue](../mfc/initializing-the-dialog-box.md)

- [Traitement des messages de Windows dans votre boîte de dialogue](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Récupération des données à partir de l’objet de la boîte de dialogue](../mfc/retrieving-data-from-the-dialog-object.md)

- [Fermeture de la boîte de dialogue](../mfc/closing-the-dialog-box.md)

- [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md)

- [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Boîtes de dialogue de feuille de propriétés](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)

