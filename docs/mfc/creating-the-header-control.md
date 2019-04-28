---
title: Création du contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 669b13cf566f24bfcd5a29ae41af1cdb90513f73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242313"
---
# <a name="creating-the-header-control"></a>Création du contrôle Header

Le contrôle header n’est pas directement disponible dans l’éditeur de boîtes de dialogue (bien que vous pouvez ajouter un contrôle de liste, qui inclut un contrôle header).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Pour placer un contrôle header dans une boîte de dialogue

1. Incorporez manuellement une variable membre de type [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) dans votre classe de boîte de dialogue.

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), créer et définir les styles pour le `CHeaderCtrl`, placez-le et l’afficher.

1. Ajouter des éléments au contrôle header.

1. Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour toute notification de contrôle header messages vous devez gérer (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Pour placer un contrôle header dans une vue (pas une CListView)

1. Incorporer un [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objet dans votre classe d’affichage.

1. Appliquer un style, position et afficher la fenêtre de contrôle d’en-tête dans la vue [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction membre.

1. Ajouter des éléments au contrôle header.

1. Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe d’affichage pour les messages de notification de n’importe quel contrôle header vous devez gérer (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

Dans les deux cas, l’objet de contrôle incorporé est créé lorsque l’objet de vue ou de la boîte de dialogue est créé. Vous devez l’appeler [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) pour créer la fenêtre de contrôle. Pour positionner le contrôle, appelez [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) pour déterminer la taille initiale et la position du contrôle et [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) pour définir la position souhaitée. Ajoutez ensuite les éléments comme décrit dans [Ajout d’éléments au contrôle Header](../mfc/adding-items-to-the-header-control.md).

Pour plus d’informations, consultez [création d’un contrôle d’en-tête](/windows/desktop/Controls/header-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
