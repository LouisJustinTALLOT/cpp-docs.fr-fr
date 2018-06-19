---
title: Itopologynode, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4168fbfbd2bf17ad8b8b752d2843c8f57b0f3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692689"
---
# <a name="itopologynode-structure"></a>ITopologyNode, structure
Interface avec un nœud de topologie, comme défini par le gestionnaire des ressources. Un nœud contient une ou plusieurs ressources d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Retourne le nombre de ressources d’exécution regroupés sous ce nœud.|  
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Retourne la première ressource de l’exécution, regroupée sous ce nœud dans l’ordre d’énumération.|  
|[ITopologyNode::GetId](#getid)|Retourne l’identificateur unique du Gestionnaire de ressources pour ce nœud.|  
|[ITopologyNode::GetNext](#getnext)|Retourne une interface pour le nœud de topologie suivant dans l’ordre d’énumération.|  
|[ITopologyNode::GetNumaNode](#getnumanode)|Retourne les fenêtres attribué un numéro de nœud NUMA auquel appartenance ce nœud du Gestionnaire de ressources.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est généralement utilisée pour parcourir la topologie du système comme observée par le Gestionnaire de ressources.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ITopologyNode`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="getexecutionresourcecount"></a>  Itopologynode::getexecutionresourcecount, méthode  
 Retourne le nombre de ressources d’exécution regroupés sous ce nœud.  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de ressources d’exécution sont regroupés sous ce nœud.  
  
##  <a name="getfirstexecutionresource"></a>  Itopologynode::getfirstexecutionresource, méthode  
 Retourne la première ressource de l’exécution, regroupée sous ce nœud dans l’ordre d’énumération.  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La première ressource de l’exécution sont regroupés sous ce nœud dans l’ordre d’énumération.  
  
##  <a name="getid"></a>  Itopologynode::GetId, méthode  
 Retourne l’identificateur unique du Gestionnaire de ressources pour ce nœud.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur unique du Gestionnaire de ressources pour ce nœud.  
  
### <a name="remarks"></a>Notes  
 Le Runtime d’accès concurrentiel représente des threads matériels sur le système dans des groupes de nœuds processeur. Nœuds sont dérivés habituellement de la topologie matérielle du système. Par exemple, tous les processeurs sur un socket spécifique ou un nœud NUMA spécifique peuvent appartenir au même nœud de processeur. Le Gestionnaire des ressources assigne des identificateurs uniques à ces nœuds en commençant par `0` de `nodeCount - 1`, où `nodeCount` représente le nombre total de nœuds processeur sur le système.  
  
 Le nombre de nœuds peut être obtenu à partir de la fonction [GetProcessorNodeCount](concurrency-namespace-functions.md).  
  
##  <a name="getnext"></a>  Itopologynode::GetNext, méthode  
 Retourne une interface pour le nœud de topologie suivant dans l’ordre d’énumération.  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une interface vers le nœud suivant dans l’ordre d’énumération. S’il n’y a pas d’autres nœuds dans l’ordre d’énumération de la topologie du système, cette méthode retourne la valeur `NULL`.  
  
##  <a name="getnumanode"></a>  Itopologynode::getnumanode, méthode  
 Retourne les fenêtres attribué un numéro de nœud NUMA auquel appartenance ce nœud du Gestionnaire de ressources.  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Les fenêtres affecté le numéro de nœud NUMA auquel appartenance ce nœud du Gestionnaire de ressources.  
  
### <a name="remarks"></a>Notes  
 Un proxy de thread en cours d’exécution sur une racine de processeur virtuel appartenant à ce nœud aura affinité au moins au niveau du nœud NUMA pour le nœud NUMA retourné par cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
