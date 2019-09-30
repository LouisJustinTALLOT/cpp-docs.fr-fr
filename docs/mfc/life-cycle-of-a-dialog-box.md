---
title: Utilisation des boîtes de dialogue dans MFC
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685729"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Utilisation des boîtes de dialogue dans MFC

Pendant le cycle de vie d’une boîte de dialogue, l’utilisateur appelle la boîte de dialogue, généralement à l’intérieur d’un gestionnaire de commandes qui crée et initialise l’objet de boîte de dialogue, l’utilisateur interagit avec la boîte de dialogue, puis la boîte de dialogue se ferme.

Pour les boîtes de dialogue modales, votre gestionnaire recueille toutes les données entrées par l’utilisateur une fois la boîte de dialogue fermée. Étant donné que l’objet de boîte de dialogue existe après la fermeture de sa fenêtre de dialogue, vous pouvez simplement utiliser les variables membres de votre classe de boîte de dialogue pour extraire les données.

Pour les boîtes de dialogue non modales, vous pouvez souvent extraire des données de l’objet de boîte de dialogue lorsque la boîte de dialogue est toujours visible. À un moment donné, l’objet Dialog est détruit. Lorsque cela se produit dépend de votre code.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création et affichage de boîtes de dialogue](../mfc/creating-and-displaying-dialog-boxes.md)

- [Création de boîtes de dialogue modales](../mfc/creating-modal-dialog-boxes.md)

- [Création de boîtes de dialogue non modales](../mfc/creating-modeless-dialog-boxes.md)

- [Utilisation d’un modèle de boîte de dialogue en mémoire](../mfc/using-a-dialog-template-in-memory.md)

- [Définition de la couleur d’arrière-plan de la boîte de dialogue](../mfc/setting-the-dialog-boxs-background-color.md)

- [Initialisation de la boîte de dialogue](../mfc/initializing-the-dialog-box.md)

- [Gestion des messages Windows dans votre boîte de dialogue](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Récupération de données de l’objet Dialog](../mfc/retrieving-data-from-the-dialog-object.md)

- [Fermeture de la boîte de dialogue](../mfc/closing-the-dialog-box.md)

- [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md)

- [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Boîtes de dialogue de la feuille de propriétés](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)
