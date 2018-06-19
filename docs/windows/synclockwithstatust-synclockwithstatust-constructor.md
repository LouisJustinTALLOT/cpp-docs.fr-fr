---
title: Synclockwithstatust::synclockwithstatust, constructeur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f665866a43e45d6526aa33f17c05eacebdd84aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891348"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT, constructeur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `other`  
 Une référence rvalue à un autre objet SyncLockWithStatusT.  
  
 `sync`  
 Une référence à un autre objet SyncLockWithStatusT.  
  
 `status`  
 La valeur de la [status_](../windows/synclockwithstatust-status-data-member.md) membre de données de la `other` paramètre ou le `sync` paramètre.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la classe SyncLockWithStatusT.  
  
 Le premier constructeur initialise l’objet SyncLockWithStatusT actuel à partir d’un autre SyncLockWithStatusT spécifié par le paramètre `other`et puis invalide l’autre objet SyncLockWithStatusT. Le deuxième constructeur est `protected`et initialise l’objet SyncLockWithStatusT actuel à un état non valide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockWithStatusT (classe)](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus, méthode](../windows/synclockwithstatust-getstatus-method.md)