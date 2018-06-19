---
title: SYSTEMTIME Structure1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a0042adaa223fc5898c057f191f7b750fa230f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372390"
---
# <a name="systemtime-structure1"></a>SYSTEMTIME Structure1
Le `SYSTEMTIME` structure représente une date et heure à l’aide des membres individuels pour les mois, jour, année, semaine, heure, minute, seconde et milliseconde.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _SYSTEMTIME {  
    WORD wYear;  
    WORD wMonth;  
    WORD wDayOfWeek;  
    WORD wDay;  
    WORD wHour;  
    WORD wMinute;  
    WORD wSecond;  
    WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *wYear*  
 L’année en cours.  
  
 *Propriété*  
 Le mois en cours ; Janvier est 1.  
  
 *wDayOfWeek*  
 Le jour actuel de la semaine ; Dimanche est 0, lundi est 1 et ainsi de suite.  
  
 *wDay*  
 Le jour du mois actuel.  
  
 *exactes*  
 L’heure actuelle.  
  
 *Absolu*  
 La minute actuelle.  
  
 *wSecond*  
 La seconde actuelle.  
  
 *Heure*  
 La milliseconde en cours.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winbase.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

