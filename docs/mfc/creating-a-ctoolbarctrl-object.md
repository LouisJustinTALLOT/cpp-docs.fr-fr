---
title: Création d'un objet CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: cf1d2eeb9efd2f8a1e7b433c0e18dd868a8b9aca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445897"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Création d'un objet CToolBarCtrl

Les objets [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) contiennent plusieurs structures de données internes, à savoir une liste de bitmaps d’image de bouton, une liste de chaînes de noms de bouton et une liste de structures de `TBBUTTON`, qui associent une image et/ou une chaîne à la position, le style, l’État et l’ID de commande du bouton. Chacun des éléments de ces structures de données est référencé par un index de base zéro. Avant de pouvoir utiliser un objet `CToolBarCtrl`, vous devez configurer ces structures de données. Pour obtenir la liste des structures de données, consultez [Toolbar Controls](controls-mfc.md) in the SDK Windows. La liste de chaînes peut uniquement être utilisée pour les étiquettes de bouton ; vous ne pouvez pas récupérer des chaînes à partir de la barre d’outils.

Pour utiliser un objet `CToolBarCtrl`, vous devez généralement suivre les étapes suivantes :

### <a name="to-use-a-ctoolbarctrl-object"></a>Pour utiliser un objet CToolBarCtrl

1. Construisez l’objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .

1. Appelez [Create](../mfc/reference/ctoolbarctrl-class.md#create) pour créer le contrôle commun de barre d’outils Windows et l’attacher à l’objet `CToolBarCtrl`. Si vous souhaitez des images bitmap pour les boutons, ajoutez les bitmaps de bouton à la barre d’outils en appelant [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Si vous souhaitez des étiquettes de chaîne pour les boutons, ajoutez les chaînes à la barre d’outils en appelant [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) et/ou [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Après avoir appelé `AddString` et/ou `AddStrings`, vous devez appeler [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) pour que la chaîne ou les chaînes apparaissent.

1. Ajoutez des structures de bouton à la barre d’outils en appelant [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Si vous souhaitez obtenir des info-bulles, gérez les messages **TTN_NEEDTEXT** dans la fenêtre propriétaire de la barre d’outils, comme décrit dans [gestion des notifications d’info-bulle](../mfc/handling-tool-tip-notifications.md).

1. Si vous souhaitez que votre utilisateur puisse personnaliser la barre d’outils, gérez les messages de notification de personnalisation dans la fenêtre propriétaire comme décrit dans [gestion des notifications de personnalisation](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
