---
title: Création d'un objet CToolBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CToolBarCtrl
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: d0f41731e3a4db7b15d4f2a7ebaac94135d5350d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265104"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Création d'un objet CToolBarCtrl

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objets contiennent plusieurs structures de données internes, une liste d’images bitmap, une liste de chaînes d’étiquette de bouton et une liste de `TBBUTTON` structures — qui associer une image et/ou de chaîne avec la position, le style, l’état, et ID de commande du bouton. Chacun des éléments de ces structures de données est considéré par un index de base zéro. Avant de pouvoir utiliser un `CToolBarCtrl` de l’objet, vous devez configurer ces structures de données. Pour obtenir la liste des structures de données, consultez [contrôles de barre d’outils](controls-mfc.md) dans le SDK Windows. La liste de chaînes utilisable uniquement pour les étiquettes de bouton ; Impossible d’extraire des chaînes à partir de la barre d’outils.

Pour utiliser un `CToolBarCtrl` de l’objet, vous serez en général, procédez comme suit :

### <a name="to-use-a-ctoolbarctrl-object"></a>Pour utiliser un objet CToolBarCtrl

1. Construire la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objet.

1. Appelez [créer](../mfc/reference/ctoolbarctrl-class.md#create) pour créer le contrôle commun de barre d’outils de Windows et l’attacher à la `CToolBarCtrl` objet. Si vous souhaitez que les images bitmap pour les boutons, ajoutez les bitmaps des boutons à la barre d’outils en appelant [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Si vous souhaitez que les étiquettes de chaîne pour les boutons, ajouter les chaînes à la barre d’outils de configuration en appelant [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) et/ou [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Après avoir appelé `AddString` et/ou `AddStrings`, vous devez appeler [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) afin d’obtenir l’ou les chaînes apparaissent.

1. Ajouter des structures de bouton à la barre d’outils en appelant [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Si vous souhaitez que les info-bulles, gérer **TTN_NEEDTEXT** messages dans la fenêtre de propriétaire de la barre d’outils, comme décrit dans [gestion des Notifications des info](../mfc/handling-tool-tip-notifications.md).

1. Si vous souhaitez que votre utilisateur soit en mesure de personnaliser la barre d’outils, gérer les messages de notification de personnalisation dans la fenêtre propriétaire comme décrit dans [gestion des Notifications de personnalisation](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
