---
title: invalid_multiple_scheduling, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs:
- C++
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cc4e3b2a23dd5c617b70a7a4b992323a0e963f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067338"
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling, classe
Cette classe décrit une exception levée quand un objet `task_handle` est planifié à plusieurs reprises à l'aide de la méthode `run` d'un objet `task_group` ou `structured_task_group` sans appel intermédiaire aux méthodes `wait` ou `run_and_wait`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[invalid_multiple_scheduling](#ctor)|Surchargé. Construit un objet `invalid_multiple_scheduling`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> invalid_multiple_scheduling 

 Construit un objet `invalid_multiple_scheduling`.  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>Paramètres  
*_Message*<br/>
Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [task_handle, classe](task-handle-class.md)   
 [task_group, classe](task-group-class.md)   
 [exécuter](task-group-class.md)   
 [attente](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group, classe](structured-task-group-class.md)
