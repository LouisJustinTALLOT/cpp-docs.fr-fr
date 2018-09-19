---
title: ISource, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14593161512e56d39b77bb0cc5af88a3ff849409
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071885"
---
# <a name="isource-class"></a>ISource, classe
La classe `ISource` est l'interface de tous les blocs sources. Les blocs sources propagent les messages aux blocs `ITarget`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>Paramètres  
*T*<br/>
Le type de données de la charge utile dans les messages produits par le bloc source.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`source_type`|Alias de type pour `T`.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[~ ISource, destructeur](#dtor)|Détruit le `ISource` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[accept](#accept)|En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce `ISource` bloc, en transférant la propriété à l’appelant.|  
|[acquire_ref](#acquire_ref)|En cas de substitution dans une classe dérivée, acquiert un décompte de références sur ce `ISource` bloc, pour empêcher la suppression.|  
|[consommer](#consume)|En cas de substitution dans une classe dérivée, consomme un message précédemment proposé par ce `ISource` bloquer et réservé avec succès par la cible, en transférant la propriété à l’appelant.|  
|[link_target](#link_target)|En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.|  
|[release](#release)|En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.|  
|[release_ref](#release_ref)|En cas de substitution dans une classe dérivée, libère un décompte de références sur ce `ISource` bloc.|  
|[reserve](#reserve)|En cas de substitution dans une classe dérivée, réserve un message précédemment proposé par ce `ISource` bloc.|  
|[unlink_target](#unlink_target)|En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce `ISource` bloquer, s’il était précédemment lié.|  
|[unlink_targets](#unlink_targets)|En cas de substitution dans une classe dérivée, dissocie tous les blocs de cibles à partir de ce `ISource` bloc.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ISource`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept"></a> Accepter 

 En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce `ISource` bloc, en transférant la propriété à l’appelant.  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.  
  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `accept` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le message dont l’appelant est désormais propriétaire.  
  
### <a name="remarks"></a>Notes  
 Le `accept` méthode est appelée par une cible pendant qu’un message est offert par ce `ISource` bloc. Le pointeur de message retourné peut être différent de celui passé dans le `propagate` méthode de la `ITarget` bloquer, si cette source décide d’effectuer une copie du message.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 En cas de substitution dans une classe dérivée, acquiert un décompte de références sur ce `ISource` bloc, pour empêcher la suppression.  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par un `ITarget` objet lié à cette source pendant le `link_target` (méthode).  
  
##  <a name="consume"></a> consommer 

 En cas de substitution dans une classe dérivée, consomme un message précédemment proposé par ce `ISource` bloquer et réservé avec succès par la cible, en transférant la propriété à l’appelant.  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_MsgId*<br/>
Le `runtime_object_identity` de réservée `message` objet.  
  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `consume` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 Le `consume` méthode est similaire à `accept`, mais doit toujours être précédé par un appel à `reserve` qui retourné `true`.  
  
##  <a name="dtor"></a> ~ ISource 

 Détruit le `ISource` objet.  
  
```
virtual ~ISource();
```  
  
##  <a name="link_target"></a> link_target 

 En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui est lié à cette `ISource` bloc.  
  
##  <a name="release"></a> Mise en production 

 En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_MsgId*<br/>
Le `runtime_object_identity` de réservée `message` objet.  
  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `release` (méthode).  
  
##  <a name="release_ref"></a> release_ref 

 En cas de substitution dans une classe dérivée, libère un décompte de références sur ce `ISource` bloc.  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par un `ITarget` objet dissocié de cette source. Le bloc source est autorisé à libérer les ressources réservées pour le bloc cible.  
  
##  <a name="reserve"></a> réserver 

 En cas de substitution dans une classe dérivée, réserve un message précédemment proposé par ce `ISource` bloc.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.  
  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `reserve` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le message a été réservé avec succès, `false` dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a été déjà réservé ou accepté par une autre cible, la source peut refuser des réservations et ainsi de suite.  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé `reserve`, si elle réussit, vous devez appeler `consume` ou `release` afin d’accepter ou renoncer à la possession du message, respectivement.  
  
##  <a name="unlink_target"></a> unlink_target 

 En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce `ISource` bloquer, s’il était précédemment lié.  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_PTarget*<br/>
Un pointeur vers le bloc cible qui est dissocié de ce `ISource` bloc.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 En cas de substitution dans une classe dérivée, dissocie tous les blocs de cibles à partir de ce `ISource` bloc.  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [ITarget, classe](itarget-class.md)
