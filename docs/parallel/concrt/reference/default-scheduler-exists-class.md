---
title: default_scheduler_exists, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
dev_langs:
- C++
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488f1d08c089b159971834729596d74b4e3dab22
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106044"
---
# <a name="defaultschedulerexists-class"></a>default_scheduler_exists, classe
Cette classe décrit une exception levée quand la méthode `Scheduler::SetDefaultSchedulerPolicy` est appelée alors qu'un planificateur par défaut existe déjà au sein du processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class default_scheduler_exists : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[default_scheduler_exists](#ctor)|Surchargé. Construit un objet `default_scheduler_exists`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `default_scheduler_exists`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> default_scheduler_exists 

 Construit un objet `default_scheduler_exists`.  
  
```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```  
  
### <a name="parameters"></a>Paramètres  
*_Message*<br/>
Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
