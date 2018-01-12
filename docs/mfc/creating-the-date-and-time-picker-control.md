---
title: "Création de la Date Time Picker contrôle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e9c0b99f42bef162ed3c571e19630f9227a8504e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-date-and-time-picker-control"></a>Création du contrôle de sélecteur de date et heure
La création du contrôle de sélecteur de date et d’heure dépend de l’utilisation du contrôle dans une boîte de dialogue ou de la créer dans un autre type de fenêtre.  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Pour utiliser CDateTimeCtrl directement dans une boîte de dialogue  
  
1.  Dans l’éditeur de boîte de dialogue Ajouter une Date et un contrôle de sélecteur de temps à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.  
  
2.  Spécifiez les styles nécessaires, à l’aide de la boîte de dialogue Propriétés de contrôle de sélecteur de date et d’heure.  
  
3.  Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CDateTimeCtrl` fonctions membres.  
  
4.  Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour n’importe quel contrôle date time picker [notification](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) messages, vous devez gérer (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez d’autres styles pour le `CDateTimeCtrl` objet.  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Pour utiliser CDateTimeCtrl dans un autre type de fenêtre  
  
1.  Déclarez le contrôle dans la classe d’affichage ou de la fenêtre.  
  
2.  Appel du contrôle [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction de gestionnaire (si vous êtes le sous-classement du contrôle). Définissez les styles pour le contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

