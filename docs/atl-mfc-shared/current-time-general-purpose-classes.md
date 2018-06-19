---
title: 'Heure actuelle : Classes à usage général | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec71cf76f859457aa76e69b57b58db3940e974da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354593"
---
# <a name="current-time-general-purpose-classes"></a>Heure actuelle : Classes à usage général
La procédure suivante montre comment créer un `CTime` de l’objet et l’initialiser avec l’heure actuelle.  
  
#### <a name="to-get-the-current-time"></a>Pour obtenir l’heure actuelle  
  
1.  Allouer un `CTime` de l’objet, comme suit :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  Sans être initialisé `CTime` objets ne sont pas initialisés avec une heure valide.  
  
2.  Appelez le `CTime::GetCurrentTime` fonction permettant d’obtenir l’heure actuelle du système d’exploitation. Cette fonction retourne un `CTime` objet qui peut être utilisé pour définir la valeur de `CTime`, comme suit :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]  
  
     Étant donné que `GetCurrentTime` est une fonction membre statique à partir de la `CTime` (classe), vous devez qualifier son nom avec le nom de la classe et l’opérateur de résolution de portée (`::`), `CTime::GetCurrentTime()`.  
  
 Bien évidemment, les deux étapes décrites précédemment peuvent être combinées en une seule instruction comme suit :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure : classes à usage général](../atl-mfc-shared/date-and-time-general-purpose-classes.md)



