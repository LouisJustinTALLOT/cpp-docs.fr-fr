---
title: Définition de l’état du jour d’un mois contrôle Calendar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4254448e3f8f5a23acd9a303788fd13afb2f84
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950793"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Définition de l'état du jour d'un contrôle month calendar
Un des attributs d'un contrôle calendrier mensuel est la possibilité de stocker des informations, connues sous le nom d'état du jour du contrôle, pour chaque jour du mois. Ces informations sont utilisées pour mettre en évidence des dates du mois actuellement affiché.  
  
> [!NOTE]
>  Le `CMonthCalCtrl` l’objet doit avoir le style MCS_DAYSTATE pour afficher les informations d’état jour.  
  
 Informations d’état jour sont exprimées comme un type de données 32 bits, **MONTHDAYSTATE**. Chaque bit d’un **MONTHDAYSTATE** un champ de bits (1 à 31) représente l’état d’un jour du mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.  
  
 Il existe deux méthodes pour définir l’état du jour du contrôle month calendar : explicitement par un appel à [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) ou en gérant le message de notification MCN_GETDAYSTATE.  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>Gestion du message de notification MCN_GETDAYSTATE  
 Le message MCN_GETDAYSTATE est envoyé par le contrôle pour déterminer comment les jours des mois visibles doivent être affichées.  
  
> [!NOTE]
>  Parce que le contrôle met en cache les mois précédents et suivants, en fonction du mois visible, vous recevez cette notification chaque fois qu'un nouveau mois est choisi.  
  
 Pour gérer correctement ce message, vous devez déterminer le nombre de mois sont en cours d’informations d’état jour demandé, initialiser un tableau de **MONTHDAYSTATE** structures avec les valeurs appropriées et d’initialiser le membre de structure associé aux avec les nouvelles informations. La procédure suivante, détaillant les étapes nécessaires, suppose que vous avez un `CMonthCalCtrl` objet appelé *m_monthcal* et un tableau de **MONTHDAYSTATE** objets *mdState*.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Pour gérer le message de notification MCN_GETDAYSTATE  
  
1.  À l’aide de la fenêtre Propriétés, ajoutez un gestionnaire de notification pour le message MCN_GETDAYSTATE le *m_monthcal* objet (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).  
  
2.  Dans le corps du gestionnaire, ajoutez le code suivant :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     L’exemple suivant convertit le *pNMHDR* pointeur vers le type approprié, puis détermine le nombre de mois d’informations est demandé (`pDayState->cDayState`). Pour chaque mois, le champ de bits actuel (`pDayState->prgDayState[i]`) est initialisé à zéro et les dates nécessaires sont assignées (dans ce cas, le 15 de chaque mois).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

