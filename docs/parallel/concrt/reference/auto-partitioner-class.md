---
title: auto_partitioner, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05232aa954a9ded7d2ab3a26ae4e1524610c3d04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705443"
---
# <a name="autopartitioner-class"></a>auto_partitioner, classe
La classe `auto_partitioner` représente la méthode par défaut que `parallel_for`, `parallel_for_each` et `parallel_transform` utilisent pour partitionner la plage au sein de laquelle ils itèrent. Cette méthode de partitionnement utilise un vol de plage pour équilibrer la charge et annuler par itération.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class auto_partitioner;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[auto_partitioner](#ctor)|Construit un objet `auto_partitioner`.|  
|[~ auto_partitioner, destructeur](#dtor)|Détruit un objet `auto_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `auto_partitioner`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ppl.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dtor"></a> ~auto_partitioner 

 Détruit un objet `auto_partitioner`.  
  
```
~auto_partitioner();
```  
  
##  <a name="ctor"></a> auto_partitioner 

 Construit un objet `auto_partitioner`.  
  
```
auto_partitioner();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
