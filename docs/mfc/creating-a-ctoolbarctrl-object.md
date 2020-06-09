---
title: Création d'un objet CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2627f9aaceeab7760e15b23435233e124c5ea6f0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619004"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Création d'un objet CToolBarCtrl

Les objets [CToolBarCtrl](reference/ctoolbarctrl-class.md) contiennent plusieurs structures de données internes (une liste d’images bitmap d’image de bouton, une liste de chaînes de noms de bouton et une liste de `TBBUTTON` structures) qui associent une image et/ou une chaîne à la position, le style, l’État et l’ID de commande du bouton. Chacun des éléments de ces structures de données est référencé par un index de base zéro. Avant de pouvoir utiliser un `CToolBarCtrl` objet, vous devez configurer ces structures de données. Pour obtenir la liste des structures de données, consultez [Toolbar Controls](controls-mfc.md) in the SDK Windows. La liste de chaînes peut uniquement être utilisée pour les étiquettes de bouton ; vous ne pouvez pas récupérer des chaînes à partir de la barre d’outils.

Pour utiliser un `CToolBarCtrl` objet, vous devez généralement suivre les étapes suivantes :

### <a name="to-use-a-ctoolbarctrl-object"></a>Pour utiliser un objet CToolBarCtrl

1. Construisez l’objet [CToolBarCtrl](reference/ctoolbarctrl-class.md) .

1. Appelez [Create](reference/ctoolbarctrl-class.md#create) pour créer le contrôle commun de barre d’outils Windows et l’attacher à l' `CToolBarCtrl` objet. Si vous souhaitez des images bitmap pour les boutons, ajoutez les bitmaps de bouton à la barre d’outils en appelant [AddBitmap](reference/ctoolbarctrl-class.md#addbitmap). Si vous souhaitez des étiquettes de chaîne pour les boutons, ajoutez les chaînes à la barre d’outils en appelant [AddString](reference/ctoolbarctrl-class.md#addstring) et/ou [AddStrings](reference/ctoolbarctrl-class.md#addstrings). Après avoir appelé `AddString` et/ou `AddStrings` , vous devez appeler [AutoSize](reference/ctoolbarctrl-class.md#autosize) pour que la chaîne ou les chaînes apparaissent.

1. Ajoutez des structures de bouton à la barre d’outils en appelant [AddButtons](reference/ctoolbarctrl-class.md#addbuttons).

1. Si vous souhaitez obtenir des info-bulles, gérez les messages **TTN_NEEDTEXT** dans la fenêtre propriétaire de la barre d’outils, comme décrit dans [gestion des notifications d’info-bulle](handling-tool-tip-notifications.md).

1. Si vous souhaitez que votre utilisateur puisse personnaliser la barre d’outils, gérez les messages de notification de personnalisation dans la fenêtre propriétaire comme décrit dans [gestion des notifications de personnalisation](handling-customization-notifications.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Commandes](controls-mfc.md)
