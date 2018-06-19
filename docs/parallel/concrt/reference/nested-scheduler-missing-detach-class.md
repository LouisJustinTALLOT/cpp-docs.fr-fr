---
title: nested_scheduler_missing_detach, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26027693209bc5b4687686efeae5d190ed374607
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687359"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach, classe
Cette classe décrit une exception levée quand le runtime d'accès concurrentiel détecte que vous avez omis d'appeler la méthode `CurrentScheduler::Detach` sur un contexte joint à un deuxième planificateur à l'aide de la méthode `Attach` de l'objet `Scheduler`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[nested_scheduler_missing_detach](#ctor)|Surchargé. Construit un objet `nested_scheduler_missing_detach`.|  
  
## <a name="remarks"></a>Notes  
 Cette exception est levée uniquement lorsque vous imbriquez un planificateur à l’intérieur d’un autre en appelant le `Attach` méthode d’un `Scheduler` objet dans un contexte qui est déjà détenu par ou attaché à un autre planificateur. Le Runtime d’accès concurrentiel lève cette exception de façon opportuniste lorsqu’il peut détecter le scénario comme une aide pour localiser le problème. Pas de chaque instance de néglige appeler le `CurrentScheduler::Detach` est garanti que méthode lèvent cette exception.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> nested_scheduler_missing_detach 

 Construit un objet `nested_scheduler_missing_detach`.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `_Message`  
 Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Scheduler, classe](scheduler-class.md)
