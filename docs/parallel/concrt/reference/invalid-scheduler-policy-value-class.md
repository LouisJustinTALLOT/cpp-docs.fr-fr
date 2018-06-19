---
title: invalid_scheduler_policy_value, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec11d7ebc7d2c074344e9651a7c548fe1ad01943
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689725"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value, classe
Cette classe décrit une exception levée quand une clé de stratégie d'un objet `SchedulerPolicy` est défini sur une valeur non valide pour cette clé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Surchargé. Construit un objet `invalid_scheduler_policy_value`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value 

 Construit un objet `invalid_scheduler_policy_value`.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `_Message`  
 Message descriptif de l'erreur.  
  

## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [SchedulerPolicy, classe](schedulerpolicy-class.md)
