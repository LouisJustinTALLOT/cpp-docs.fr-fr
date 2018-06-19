---
title: Cycle de vie d’une boîte de dialogue | Documents Microsoft
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
ms.openlocfilehash: faf204f05c03e742e0f491fb3991b56d3405ebc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346179"
---
# <a name="life-cycle-of-a-dialog-box"></a>Cycle de vie d'une boîte de dialogue
Au cours du cycle de vie d’une boîte de dialogue, l’utilisateur appelle la boîte de dialogue, généralement à l’intérieur d’un gestionnaire de commandes qui crée et initialise l’objet de la boîte de dialogue, l’utilisateur interagit avec la boîte de dialogue et la boîte de dialogue se ferme.  
  
 Pour les boîtes de dialogue modales, votre gestionnaire rassemble toutes les données de l’utilisateur a entré une fois que la boîte de dialogue se ferme. Étant donné que l’objet de la boîte de dialogue existe après la fermeture de la fenêtre de la boîte de dialogue, vous pouvez simplement utiliser les variables de membre de votre classe de boîte de dialogue pour extraire les données.  
  
 Pour les boîtes de dialogue non modale, vous pouvez souvent extraire des données à partir de l’objet de la boîte de dialogue lors de la boîte de dialogue est toujours visible. Dans certains cas, l’objet de la boîte de dialogue est détruite ; Quand cela se produit dépend de votre code.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Création et affichage de boîtes de dialogue](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Création de boîtes de dialogue modales](../mfc/creating-modal-dialog-boxes.md)  
  
-   [Création de boîtes de dialogue non modales](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [À l’aide d’un modèle de boîte de dialogue en mémoire](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [Définir la couleur d’arrière-plan de la boîte de dialogue](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [Initialisation de la boîte de dialogue](../mfc/initializing-the-dialog-box.md)  
  
-   [La gestion des messages Windows dans votre boîte de dialogue](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [La récupération des données à partir de l’objet de la boîte de dialogue](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [Fermeture de la boîte de dialogue](../mfc/closing-the-dialog-box.md)  
  
-   [Destruction de la boîte de dialogue](../mfc/destroying-the-dialog-box.md)  
  
-   [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Boîtes de dialogue de feuille de propriétés](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)

