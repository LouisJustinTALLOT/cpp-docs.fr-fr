---
description: 'En savoir plus sur : définition de l’état du jour d’un contrôle Month Calendar'
title: Définition de l'état du jour d'un contrôle month calendar
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: e7fc06516877c54aadaef715c33abd128bbd6994
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217209"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Définition de l'état du jour d'un contrôle month calendar

Un des attributs d'un contrôle calendrier mensuel est la possibilité de stocker des informations, connues sous le nom d'état du jour du contrôle, pour chaque jour du mois. Ces informations sont utilisées pour mettre en évidence des dates du mois actuellement affiché.

> [!NOTE]
> L' `CMonthCalCtrl` objet doit avoir le style MCS_DAYSTATE pour afficher les informations d’État du jour.

Les informations d’État du jour sont exprimées sous la forme d’un type de données 32 bits, **MONTHDAYSTATE**. Chaque bit dans un champ de bits **MONTHDAYSTATE** (1 à 31) représente l’état d’un jour dans un mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.

Il existe deux méthodes pour définir l’état du jour du contrôle Month Calendar : explicitement avec un appel à [CMonthCalCtrl :: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) ou en gérant le message de notification MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Gestion du message de notification MCN_GETDAYSTATE

Le message MCN_GETDAYSTATE est envoyé par le contrôle pour déterminer comment les jours dans les mois visibles doivent être affichés.

> [!NOTE]
> Parce que le contrôle met en cache les mois précédents et suivants, en fonction du mois visible, vous recevez cette notification chaque fois qu'un nouveau mois est choisi.

Pour gérer correctement ce message, vous devez déterminer le nombre de mois pendant lesquels les informations d’État sont demandées, initialiser un tableau de structures **MONTHDAYSTATE** avec les valeurs appropriées et initialiser le membre de structure associé avec les nouvelles informations. La procédure suivante, détaillant les étapes nécessaires, suppose que vous disposez d’un `CMonthCalCtrl` objet appelé *m_monthcal* et d’un tableau d’objets **MONTHDAYSTATE** , *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Pour gérer le message de notification MCN_GETDAYSTATE

1. À l’aide de l' [Assistant classe](reference/mfc-class-wizard.md), ajoutez un gestionnaire de notifications pour le message MCN_GETDAYSTATE à l’objet *M_monthcal* (consultez [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans le corps du gestionnaire, ajoutez le code suivant :

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   L’exemple convertit le pointeur *pNMHDR* en type approprié, puis détermine le nombre de mois d’informations demandé ( `pDayState->cDayState` ). Pour chaque mois, le champ de bits actuel (`pDayState->prgDayState[i]`) est initialisé à zéro et les dates nécessaires sont assignées (dans ce cas, le 15 de chaque mois).

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
