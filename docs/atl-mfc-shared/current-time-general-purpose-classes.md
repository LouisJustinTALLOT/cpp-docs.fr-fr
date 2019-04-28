---
title: 'Heure actuelle : Classes à usage général'
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
ms.openlocfilehash: e883a47243feb7ad1555748ffdda9b8ae9594644
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236212"
---
# <a name="current-time-general-purpose-classes"></a>Heure actuelle : Classes à usage général

La procédure suivante montre comment créer un `CTime` de l’objet et l’initialiser avec l’heure actuelle.

### <a name="to-get-the-current-time"></a>Pour obtenir l’heure actuelle

1. Allouer un `CTime` de l’objet, comme suit :

   [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]

   > [!NOTE]
   > Non initialisé `CTime` objets ne sont pas initialisés à une heure valide.

1. Appelez le `CTime::GetCurrentTime` fonction pour obtenir l’heure actuelle du système d’exploitation. Cette fonction retourne un `CTime` objet qui peut être utilisé pour définir la valeur de `CTime`, comme suit :

   [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]

   Dans la mesure où `GetCurrentTime` est une fonction membre statique à partir de la `CTime` (classe), vous devez qualifier son nom avec le nom de la classe et l’opérateur de résolution de portée (`::`), `CTime::GetCurrentTime()`.

Bien sûr, les deux étapes décrites précédemment peuvent être combinés dans une seule instruction comme suit :

[!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]
