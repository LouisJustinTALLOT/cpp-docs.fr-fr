---
title: Création d’un objet CToolBarCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5e2ee8c0e2239de86252b3d0fb8ec0ab7cc182
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341692"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Création d'un objet CToolBarCtrl
[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objets contiennent plusieurs structures de données interne, une liste d’images bitmap, une liste de chaînes d’étiquette de bouton et une liste de `TBBUTTON` structures — qui associer une image et/ou de chaîne avec la position, le style, l’état, et ID de commande du bouton. Chacun des éléments de ces structures de données constitue un index de base zéro. Avant de pouvoir utiliser un `CToolBarCtrl` de l’objet, vous devez configurer ces structures de données. Pour obtenir la liste des structures de données, consultez [des contrôles de barre d’outils](controls-mfc.md) dans le Kit de développement logiciel Windows. La liste des chaînes utilisable uniquement pour les étiquettes de bouton ; Impossible de récupérer des chaînes à partir de la barre d’outils.  
  
 Pour utiliser un `CToolBarCtrl` de l’objet, en général, suivez ces étapes :  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>Pour utiliser un objet CToolBarCtrl  
  
1.  Construire la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objet.  
  
2.  Appelez [créer](../mfc/reference/ctoolbarctrl-class.md#create) pour créer le contrôle commun de barre d’outils Windows et l’attacher à la `CToolBarCtrl` objet. Si vous souhaitez que les images bitmap pour les boutons, ajoutez les bitmaps des boutons à la barre d’outils en appelant [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Si vous souhaitez que les étiquettes de chaînes pour les boutons, ajoutez les chaînes de la barre d’outils en appelant [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) et/ou [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Après avoir appelé `AddString` et/ou `AddStrings`, vous devez appeler [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) afin d’obtenir l’ou les chaînes à afficher.  
  
3.  Ajouter des structures de boutons à la barre d’outils en appelant [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).  
  
4.  Si vous souhaitez que les info-bulles, gérer **TTN_NEEDTEXT** comme décrit dans les messages dans la fenêtre propriétaire de la barre d’outils [la gestion des Notifications des info](../mfc/handling-tool-tip-notifications.md).  
  
5.  Si vous souhaitez que votre utilisateur puisse être en mesure de personnaliser la barre d’outils, gérer les messages de notification de personnalisation dans la fenêtre propriétaire comme décrit dans [Notifications de personnalisation de la gestion des](../mfc/handling-customization-notifications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

