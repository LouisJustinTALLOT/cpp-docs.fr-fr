---
title: Modifier la police du texte d’une Image (Éditeur d’images pour les icônes) | Documents Microsoft
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
ms.openlocfilehash: b3ddef7e52866d5e25c3b9f5e5c580062f73e1b3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860890"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Modification de la police du texte d'une image (Éditeur d'images pour les icônes)
La procédure suivante est un exemple montrant comment :  
  
-   Ajouter du texte à une icône dans une Application Windows  
  
-   Manipuler la police du texte  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>Pour modifier la police du texte d’une image  
  
1.  Créer une Application Windows Forms C++. Pour plus d’informations, consultez [création d’un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa). Le [modèle Application Windows Forms](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea) ajoute un fichier nommé app.ico à votre projet par défaut.  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur le fichier app.ico. Le [Éditeur d’images](../windows/image-editor-for-icons.md) s’ouvre.  
  
3.  À partir de la **Image** menu, sélectionnez **outils** , puis sélectionnez **outil texte**. Le [boîte de dialogue Outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md) s’affiche.  
  
4.  Dans la boîte de dialogue Outil texte, tapez `C++` dans la zone de texte vide. Ce texte apparaît dans une zone redimensionnable située dans le coin supérieur gauche du fichier app.ico, dans l’éditeur d’images.  
  
5.  Dans l’éditeur d’images, faites glisser la zone redimensionnable au centre du fichier app.ico pour améliorer la lisibilité du texte.  
  
6.  Dans la boîte de dialogue Outil texte, cliquez sur le **police** bouton. Le [boîte de dialogue Police de texte outil](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) s’affiche.  
  
7.  Dans la boîte de dialogue Police de l’outil texte, sélectionnez **Times New Roman** dans la liste des polices disponibles sont répertoriées dans le **police** zone de liste.  
  
8.  Sélectionnez **gras** à partir de la liste des styles de police disponibles répertoriées dans le **style de police** zone de liste.  
  
9. Sélectionnez **10** à partir de la liste des disponibles point tailles répertoriées dans le **taille** zone de liste.  
  
10. Cliquez sur le **OK** bouton. La boîte de dialogue Police outil texte se ferme et les nouveaux paramètres de police s’appliquent à votre texte.  
  
11. Cliquez sur le **fermer** bouton dans la boîte de dialogue Outil texte. La zone redimensionnable autour du texte disparaît de l’éditeur d’images.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Barre d’outils](../windows/toolbar-image-editor-for-icons.md)

