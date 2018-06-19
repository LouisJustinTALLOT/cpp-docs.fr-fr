---
title: bad_target, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be10e5e4105dd16a68ad2854538d6181e90bfbe9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705339"
---
# <a name="badtarget-class"></a>bad_target, classe
Cette classe décrit une exception levée quand un bloc de messagerie reçoit un pointeur vers une cible qui n'est pas valide pour l'opération en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[bad_target](#ctor)|Surchargé. Construit un objet `bad_target`.|  
  
## <a name="remarks"></a>Notes  
 Cette exception est généralement levée pour des raisons comme une cible essayant de consommer un message qui est réservé pour une cible différente ou annulant une réservation qu’il ne contient pas.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> bad_target 

 Construit un objet `bad_target`.  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `_Message`  
 Message descriptif de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)



