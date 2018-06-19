---
title: invalid_scheduler_policy_key, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78bc955b43f3b6650f7a2fe654e5920c9cac971
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705170"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key, classe
Cette classe décrit une exception levée quand une clé non valide ou inconnue est passée à un constructeur d'objet `SchedulerPolicy`, ou quand la méthode `SetPolicyValue` d'un objet `SchedulerPolicy` est passée à une clé qui doit être modifiée à l'aide d'autres moyens que la méthode `SetConcurrencyLimits`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_scheduler_policy_key : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[invalid_scheduler_policy_key](#ctor)|Surchargé. Construit un objet `invalid_scheduler_policy_key`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> invalid_scheduler_policy_key 

 Construit un objet `invalid_scheduler_policy_key`.  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `_Message`  
 Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [SchedulerPolicy, classe](schedulerpolicy-class.md)
