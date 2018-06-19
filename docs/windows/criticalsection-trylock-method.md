---
title: CriticalSection::TryLock, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4ee99d82212d0d6cdd610b4565bd9292a0265dc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883950"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock, méthode
Tente d’entrer une section critique sans se bloquer. Si l’appel réussit, le thread appelant prend la propriété de la section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cs`  
 Un objet spécifié par l’utilisateur une section critique.  
  
## <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la section critique est entrée correctement ou le thread actuel possède déjà la section critique. Zéro si un autre thread possède déjà la section critique.  
  
## <a name="remarks"></a>Notes  
 La première **TryLock** fonction affecte l’objet en cours de la section critique. La seconde **TryLock** fonction affecte une section critique spécifié par l’utilisateur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSection, classe](../windows/criticalsection-class.md)