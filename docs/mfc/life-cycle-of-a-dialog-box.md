---
description: 'En savoir plus sur : utilisation des boîtes de dialogue dans MFC'
title: Utilisation des boîtes de dialogue dans MFC
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: 5e88d34ab26f8abd24923aacafa02c3c62ec7f06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327791"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Utilisation des boîtes de dialogue dans MFC

Pendant le cycle de vie d’une boîte de dialogue, l’utilisateur appelle la boîte de dialogue, généralement à l’intérieur d’un gestionnaire de commandes qui crée et initialise l’objet de boîte de dialogue, l’utilisateur interagit avec la boîte de dialogue, puis la boîte de dialogue se ferme.

Pour les boîtes de dialogue modales, votre gestionnaire recueille toutes les données entrées par l’utilisateur une fois la boîte de dialogue fermée. Étant donné que l’objet de boîte de dialogue existe après la fermeture de sa fenêtre de dialogue, vous pouvez simplement utiliser les variables membres de votre classe de boîte de dialogue pour extraire les données.

Pour les boîtes de dialogue non modales, vous pouvez souvent extraire des données de l’objet de boîte de dialogue lorsque la boîte de dialogue est toujours visible. À un moment donné, l’objet Dialog est détruit. Lorsque cela se produit dépend de votre code.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création et affichage de boîtes de dialogue](creating-and-displaying-dialog-boxes.md)

- [Création de boîtes de dialogue modales](creating-modal-dialog-boxes.md)

- [Création de boîtes de dialogue non modales](creating-modeless-dialog-boxes.md)

- [Utilisation d'un modèle de boîte de dialogue en mémoire](using-a-dialog-template-in-memory.md)

- [Définition de la couleur d’arrière-plan de la boîte de dialogue](setting-the-dialog-boxs-background-color.md)

- [Initialisation de la boîte de dialogue](initializing-the-dialog-box.md)

- [Gestion des messages Windows dans votre boîte de dialogue](handling-windows-messages-in-your-dialog-box.md)

- [Récupération des données d'un objet de la boîte de dialogue](retrieving-data-from-the-dialog-object.md)

- [Fermeture de la boîte de dialogue](closing-the-dialog-box.md)

- [Destruction de la boîte de dialogue](destroying-the-dialog-box.md)

- [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](dialog-data-exchange-and-validation.md)

- [Boîtes de dialogue de la feuille de propriétés](property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)
