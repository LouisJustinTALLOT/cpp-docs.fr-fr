---
title: invalid_operation, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c189649447b318a651957c82b8cfab8cd11fb60a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054829"
---
# <a name="invalidoperation-class"></a>invalid_operation, classe
Cette classe décrit une exception qui est levée quand une opération non valide qui n'est pas décrite de façon plus précise par un autre type d'exception levé par le runtime d'accès concurrentiel est exécutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_operation : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[invalid_operation](#ctor)|Surchargé. Construit un objet `invalid_operation`.|  
  
## <a name="remarks"></a>Notes  
 Les différentes méthodes qui lèvent cette exception indiquent généralement dans quelles circonstances elles agissent ainsi.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `invalid_operation`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> invalid_operation 

 Construit un objet `invalid_operation`.  
  
```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```  
  
### <a name="parameters"></a>Paramètres  
*_Message*<br/>
Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
