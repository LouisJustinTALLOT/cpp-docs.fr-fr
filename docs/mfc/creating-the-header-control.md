---
title: Création du contrôle Header | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 465c880c480f9ccd3a52f6319ee97ed203c3bd74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344511"
---
# <a name="creating-the-header-control"></a>Création du contrôle Header
Le contrôle header n’est pas directement disponible dans l’éditeur de boîte de dialogue (bien que vous pouvez ajouter un contrôle de liste, qui inclut un contrôle header).  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>Pour placer un contrôle header dans une boîte de dialogue  
  
1.  Incorporez manuellement une variable membre de type [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) dans votre classe de boîte de dialogue.  
  
2.  Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), créer et définir les styles pour le `CHeaderCtrl`, placez-le et l’afficher.  
  
3.  Ajouter des éléments au contrôle header.  
  
4.  Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour les messages de notification du contrôle header vous devez gérer (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Pour placer un contrôle header dans une vue (pas une CListView)  
  
1.  Incorporer une [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objet dans votre classe d’affichage.  
  
2.  Appliquer un style, position et afficher la fenêtre de contrôle d’en-tête dans la vue [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction membre.  
  
3.  Ajouter des éléments au contrôle header.  
  
4.  Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe d’affichage pour les messages de notification du contrôle header vous devez gérer (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).  
  
 Dans les deux cas, l’objet de contrôle incorporé est créé lors de la création de l’objet de vue ou de la boîte de dialogue. Vous devez appeler [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) pour créer la fenêtre de contrôle. Pour positionner le contrôle, appelez [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) pour déterminer la taille initiale et la position du contrôle et [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) pour définir la position souhaitée. Ajouter des éléments de comme décrit dans [Ajout d’éléments au contrôle Header](../mfc/adding-items-to-the-header-control.md).  
  
 Pour plus d’informations, consultez [création d’un contrôle d’en-tête](http://msdn.microsoft.com/library/windows/desktop/bb775238) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

