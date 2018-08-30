---
title: Modification de la police du texte d’une Image (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a8f06ae0021a95e9b4ae40506cfc91d6a8ae99b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200812"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Modification de la police du texte d'une image (Éditeur d'images pour les icônes)

La procédure suivante est un exemple montrant comment :

- Ajouter du texte à une icône dans une Application Windows

- Manipuler la police du texte

### <a name="to-change-the-font-of-text-on-an-image"></a>Pour modifier la police du texte d’une image

1. Créez une Application de formulaires Windows de C++. Pour plus d’informations, consultez [création d’un projet d’Application Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\)). Le [modèle d’Application Windows Forms](https://msdn.microsoft.com/1babdebf-ab3f-4a64-a608-98499a5b9cea) ajoute un fichier nommé `app.ico` à votre projet par défaut.

2. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier app.ico. Le [Éditeur d’images](../windows/image-editor-for-icons.md) s’ouvre.

3. À partir de la **Image** menu, sélectionnez **outils** , puis sélectionnez **outil texte**. Le [boîte de dialogue Outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md) s’affiche.

4. Dans le **outil texte** boîte de dialogue, tapez `C++` dans la zone de texte vide. Ce texte s’affiche dans une zone redimensionnable située dans le coin supérieur gauche de `app.ico`, dans le **Éditeur d’images**.

5. Dans le **Éditeur d’images**, faites glisser la zone redimensionnable au centre du fichier app.ico pour améliorer la lisibilité de votre texte.

6. Dans le **outil texte** boîte de dialogue, cliquez sur le **police** bouton. Le [boîte de dialogue Police de l’outil texte](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) s’affiche.

7. Dans le **police de l’outil texte** boîte de dialogue, sélectionnez **Times New Roman** dans la liste des polices disponibles qui sont répertoriées dans le **police** zone de liste.

8. Sélectionnez **gras** dans la liste des styles de police disponibles répertoriées dans le **style de police** zone de liste.

9. Sélectionnez **10** à partir de la liste des disponibles point tailles répertoriées dans le **taille** zone de liste.

10. Cliquez sur le **OK** bouton. Le **police de l’outil texte** boîte de dialogue se ferme et les nouveaux paramètres de police s’appliquent à votre texte.

11. Cliquez sur le **fermer** bouton sur le **outil texte** boîte de dialogue. La zone redimensionnable autour du texte disparaît de la **Éditeur d’images**.

## <a name="see-also"></a>Voir aussi

[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Barre d’outils](../windows/toolbar-image-editor-for-icons.md)