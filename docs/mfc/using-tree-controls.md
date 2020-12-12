---
description: 'En savoir plus sur : utilisation de contrôles d’arborescence'
title: Utilisation de contrôles d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 7b8a10acc3ee256f4b26c9988c4de7df900e1535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143193"
---
# <a name="using-tree-controls"></a>Utilisation de contrôles d’arborescence

L’utilisation classique d’un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) suit le modèle ci-dessous :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue ou si vous utilisez `CTreeView` , la création est automatique lors de la création de la boîte de dialogue ou de la vue. Si vous souhaitez créer le contrôle d’arborescence en tant que fenêtre enfant d’une autre fenêtre, utilisez la fonction [Create](../mfc/reference/ctreectrl-class.md#create) member.

- Si vous souhaitez que votre contrôle d’arborescence utilise des images, définissez une liste d’images en appelant [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Vous pouvez également modifier la mise en retrait en appelant [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Pour ce faire, il est recommandé d’utiliser [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (pour les contrôles dans les boîtes de dialogue) ou [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (pour les vues).

- Placez les données dans le contrôle en appelant la `CTreeCtrl` fonction [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) de pour chaque élément de données. `InsertItem` retourne un handle vers l’élément que vous pouvez utiliser pour y faire référence ultérieurement, par exemple lors de l’ajout d’éléments enfants. Un bon moment pour initialiser les données se trouve dans `OnInitDialog` (pour les contrôles dans les boîtes de dialogue) ou `OnInitialUpdate` (pour les vues).

- À mesure que l’utilisateur interagit avec le contrôle, il envoie différents messages de notification. Vous pouvez spécifier une fonction pour gérer chacun des messages que vous souhaitez gérer en ajoutant une macro ON_NOTIFY_REFLECT dans la table des messages de votre fenêtre de contrôle ou en ajoutant une macro ON_NOTIFY à la table des messages de votre fenêtre parente. Consultez [les messages de notification de contrôle d’arborescence](../mfc/tree-control-notification-messages.md) plus loin dans cette rubrique pour obtenir la liste des notifications possibles.

- Appelez les différentes fonctions membres Set pour définir les valeurs du contrôle. Les modifications que vous pouvez apporter incluent la définition de la mise en retrait et la modification du texte, de l’image ou des données associées à un élément.

- Utilisez les différentes fonctions d’extraction pour examiner le contenu du contrôle. Vous pouvez également parcourir le contenu du contrôle d’arborescence avec des fonctions qui vous permettent de récupérer des handles vers les parents, les enfants et les frères d’un élément spécifié. Vous pouvez même trier les enfants d’un nœud particulier.

- Lorsque vous avez terminé avec le contrôle, assurez-vous qu’il est correctement détruit. Si le contrôle d’arborescence se trouve dans une boîte de dialogue ou s’il s’agit d’une vue, l' `CTreeCtrl` objet est détruit automatiquement. Si ce n’est pas le cas, vous devez vous assurer que le contrôle et l' `CTreeCtrl` objet sont correctement détruits.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
