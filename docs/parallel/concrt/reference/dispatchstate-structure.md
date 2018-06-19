---
title: DispatchState, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs:
- C++
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89d3b62248d305e6acebdc8a03b7ef48c2910b28
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691064"
---
# <a name="dispatchstate-structure"></a>DispatchState, structure
La structure `DispatchState` est utilisée pour transférer l'état à la méthode `IExecutionContext::Dispatch`. Elle décrit les circonstances dans lesquelles la méthode `Dispatch` est appelée sur une interface `IExecutionContext`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[DispatchState::DispatchState](#ctor)|Construit un nouveau `DispatchState` objet.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Taille de cette structure, qui est utilisée pour le contrôle de version.|  
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indique si ce contexte a entré le `Dispatch` méthode étant donné que le contexte précédent bloqué de façon asynchrone. Cela est utilisé uniquement sur le contexte de planification UMS et est défini sur la valeur `0` pour tous les autres contextes d’exécution.|  
|[DispatchState::m_reserved](#m_reserved)|Bits réservés pour le passage de futures informations.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `DispatchState`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a>  DispatchState::DispatchState, constructeur  
 Construit un nouveau `DispatchState` objet.  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>  Données membres DispatchState::m_dispatchStateSize  
 Taille de cette structure, qui est utilisée pour le contrôle de version.  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  Données membres DispatchState::m_fIsPreviousContextAsynchronouslyBlocked  
 Indique si ce contexte a entré le `Dispatch` méthode étant donné que le contexte précédent bloqué de façon asynchrone. Cela est utilisé uniquement sur le contexte de planification UMS et est défini sur la valeur `0` pour tous les autres contextes d’exécution.  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>  Données membres DispatchState::m_reserved  
 Bits réservés pour le passage de futures informations.  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
