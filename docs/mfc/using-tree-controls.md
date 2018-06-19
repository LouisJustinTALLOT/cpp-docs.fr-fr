---
title: À l’aide de contrôles d’arborescence | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd7210f2f63d55fc4244a6b88456ede1265c8e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384867"
---
# <a name="using-tree-controls"></a>Utilisation de contrôles d’arborescence
L’utilisation typique d’un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) suit le modèle suivant :  
  
-   Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, ou si vous utilisez `CTreeView`, la création est automatique lors de la création de la boîte de dialogue ou la vue. Si vous souhaitez créer le contrôle d’arborescence comme une fenêtre enfant d’une autre fenêtre, utilisez la [créer](../mfc/reference/ctreectrl-class.md#create) fonction membre.  
  
-   Si vous souhaitez que votre contrôle d’arborescence pour utiliser des images, définissez une liste d’images en appelant [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Vous pouvez également modifier la mise en retrait en appelant [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Judicieux de procéder est [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (pour les contrôles dans les boîtes de dialogue) ou [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (pour les vues).  
  
-   Placer les données dans le contrôle en appelant le `CTreeCtrl`de [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) fonction une fois pour chaque élément de données. `InsertItem` Retourne un handle vers l’élément que vous pouvez utiliser pour faire plus tard, par exemple quand Ajout d’éléments enfants. Est judicieux pour initialiser les données `OnInitDialog` (pour les contrôles dans les boîtes de dialogue) ou `OnInitialUpdate` (pour les vues).  
  
-   Lorsque l’utilisateur interagit avec le contrôle, il envoie différents messages de notification. Vous pouvez spécifier une fonction pour gérer chacun des messages que vous souhaitez gérer en ajoutant un **ON_NOTIFY_REFLECT** macro dans la table des messages de la fenêtre du contrôle ou en ajoutant un `ON_NOTIFY` (macro) à la table des messages de la fenêtre parente. Consultez [Messages de Notification de contrôle d’arborescence](../mfc/tree-control-notification-messages.md) plus loin dans cette rubrique pour obtenir la liste des notifications possibles.  
  
-   Appelez les diverses fonctions de jeu de membres pour définir des valeurs pour le contrôle. Les modifications que vous pouvez apporter incluent la définition de la mise en retrait et la modification du texte, image ou associés liées un élément de données.  
  
-   Utilisez les diverses fonctions Get pour examiner le contenu du contrôle. Vous pouvez également parcourir le contenu du contrôle d’arborescence avec des fonctions qui vous permettent d’extraire des handles vers des parents, enfants et frères d’un élément spécifié. Vous pouvez même trier les enfants d’un nœud particulier.  
  
-   Lorsque vous avez terminé avec le contrôle, assurez-vous qu’il est correctement détruit. Si le contrôle d’arborescence se trouve dans une boîte de dialogue ou s’il s’agit d’une vue, il et `CTreeCtrl` objet sera détruit automatiquement. Si pas, vous devez vous assurer que les deux le contrôle et la `CTreeCtrl` objet sont détruits correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

