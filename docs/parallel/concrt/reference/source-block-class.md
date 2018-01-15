---
title: source_block, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs: C++
helpviewer_keywords: source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1709ebf0a831fa7c1bba79b338a2978d6c6dae86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sourceblock-class"></a>source_block, classe
La classe `source_block` est une classe de base abstraite pour les blocs sources uniquement. La classe fournit une fonctionnalité de gestion des liens de base ainsi que des vérifications d'erreurs courantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `_TargetLinkRegistry`  
 Registre de lien à utiliser pour contenir les liens cibles.  
  
 `_MessageProcessorType`  
 Type de processeur pour le traitement des messages.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`target_iterator`|L’itérateur pour parcourir les cibles connectées.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[source_block](#ctor)|Construit un objet `source_block`.|  
|[~ source_block, destructeur](#dtor)|Détruit le `source_block` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[accepter](#accept)|Accepte un message qui a été offert par ce `source_block` objet, en transférant la propriété à l’appelant.|  
|[acquire_ref](#acquire_ref)|Acquiert un décompte de références sur ce `source_block` objet, pour empêcher la suppression.|  
|[consommer](#consume)|Consomme un message précédemment offert par ce `source_block` de l’objet et réservé avec succès par la cible, en transférant la propriété à l’appelant.|  
|[link_target](#link_target)|Lie un bloc cible à ce `source_block` objet.|  
|[release](#release)|Libère une réservation de message réussie précédente.|  
|[release_ref](#release_ref)|Libère un décompte de références sur ce `source_block` objet.|  
|[reserve](#reserve)|Réserve un message précédemment offert par ce `source_block` objet.|  
|[unlink_target](#unlink_target)|Dissocie un bloc cible à partir de ce `source_block` objet.|  
|[unlink_targets](#unlink_targets)|Dissocie tous les blocs cibles à partir de ce `source_block` objet. (Substitue [ISource::unlink_targets](isource-class.md#unlink_targets).)|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[accept_message](#accept_message)|En cas de substitution dans une classe dérivée, accepte un message envoyé par la source. Blocs de messages doivent substituer cette méthode pour valider le `_MsgId` et retourner un message.|  
|[async_send](#async_send)|Les files d’attente des messages de façon asynchrone et démarre une tâche de propagation, si cela n’a pas déjà été fait|  
|[consume_message](#consume_message)|En cas de substitution dans une classe dérivée, consomme un message qui a été réservé précédemment.|  
|[enable_batched_processing](#enable_batched_processing)|Permet de traités par lot de traitement pour ce bloc.|  
|[initialize_source](#initialize_source)|Initialise le `message_propagator` dans cette `source_block`.|  
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `source_block` objet.|  
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile pour les blocs propagateurs, qui dérivent de source_block uniquement|  
|[propagate_output_messages](#propagate_output_messages)|Propager des messages aux cibles.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|En cas de substitution dans une classe dérivée, propage le message donné dans une ou toutes les cibles liées. Il s’agit de la routine de propagation principale pour les blocs de messages.|  
|[release_message](#release_message)|En cas de substitution dans une classe dérivée, libère une réservation de message précédente.|  
|[remove_targets](#remove_targets)|Supprime tous les liens de cible de ce bloc de code source. Cette opération doit être appelée à partir du destructeur.|  
|[reserve_message](#reserve_message)|En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce `source_block` objet.|  
|[resume_propagation](#resume_propagation)|En cas de substitution dans une classe dérivée, continue la propagation après qu’une réservation a été libérée.|  
|[sync_send](#sync_send)|Mode synchrone des files d’attente des messages et démarre une tâche de propagation, si cela n’a pas déjà été fait.|  
|[unlink_target_notification](#unlink_target_notification)|Un rappel qui notifie qu’une cible a été supprimée à partir de ce `source_block` objet.|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Attend que toutes les propagations asynchrones soient terminées. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les propagations asynchrones disposent de temps à se terminer avant de détruire le bloc.|  
  
## <a name="remarks"></a>Notes  
 Blocs de messages doivent dériver de ce bloc pour tirer parti de la gestion de la liaison et de synchronisation fournies par cette classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ISource](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept"></a>accepter 

 Accepte un message qui a été offert par ce `source_block` objet, en transférant la propriété à l’appelant.  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
 `_PTarget`  
 Un pointeur vers le bloc cible qui appelle la `accept` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
 Le `accept` méthode est appelée par une cible pendant qu’un message est offert par ce `ISource` bloc. Le pointeur de message retourné peut être différent de celui passé dans le `propagate` méthode de la `ITarget` bloquer, si cette source décide de faire une copie du message.  
  
##  <a name="accept_message"></a>accept_message 

 En cas de substitution dans une classe dérivée, accepte un message envoyé par la source. Blocs de messages doivent substituer cette méthode pour valider le `_MsgId` et retourner un message.  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 L’identité d’objet runtime de le `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le message que l’appelant a maintenant la propriété de.  
  
### <a name="remarks"></a>Notes  
 Pour transférer la propriété, le pointeur de message d’origine doit être retourné. Pour mettre à jour la propriété, une copie de la charge utile du message doit être effectuée et renvoyée.  
  
##  <a name="acquire_ref"></a>acquire_ref 

 Acquiert un décompte de références sur ce `source_block` objet, pour empêcher la suppression.  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par une `ITarget` objet lié à cette source pendant le `link_target` (méthode).  
  
##  <a name="async_send"></a>async_send 

 Les files d’attente des messages de façon asynchrone et démarre une tâche de propagation, si cela n’a pas déjà été fait  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Msg`  
 Un pointeur vers un `message` objet à envoyer de façon asynchrone.  
  
##  <a name="consume"></a>consommer 

 Consomme un message précédemment offert par ce `source_block` de l’objet et réservé avec succès par la cible, en transférant la propriété à l’appelant.  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de réservée `message` objet.  
  
 `_PTarget`  
 Un pointeur vers le bloc cible qui appelle la `consume` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
 La méthode lève un [bad_target](bad-target-class.md) exception si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.  
  
 Le `consume` méthode est similaire à `accept`, mais doit toujours être précédé d’un appel à `reserve` qui retourné `true`.  
  
##  <a name="consume_message"></a>consume_message 

 En cas de substitution dans une classe dérivée, consomme un message qui a été réservé précédemment.  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet ayant été consommé.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le message que l’appelant a maintenant la propriété de.  
  
### <a name="remarks"></a>Notes  
 Semblable à `accept`, mais est toujours précédé par un appel à `reserve`.  
  
##  <a name="enable_batched_processing"></a>enable_batched_processing 

 Permet de traités par lot de traitement pour ce bloc.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a>initialize_source 

 Initialise le `message_propagator` dans cette `source_block`.  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PScheduler`  
 Planificateur à utiliser pour la planification des tâches.  
  
 `_PScheduleGroup`  
 Le groupe de planification à utiliser pour la planification des tâches.  
  
##  <a name="link_target"></a>link_target 

 Lie un bloc cible à ce `source_block` objet.  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Un pointeur vers un `ITarget` à lier à ce bloc `source_block` objet.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
##  <a name="link_target_notification"></a>link_target_notification 

 Rappel qui notifie qu’une nouvelle cible a été liée à ce `source_block` objet.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Traiter les messages d’entrée. Cela est utile pour les blocs propagateurs, qui dérivent de source_block uniquement  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
  
##  <a name="propagate_output_messages"></a>propagate_output_messages 

 Propager des messages aux cibles.  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 En cas de substitution dans une classe dérivée, propage le message donné dans une ou toutes les cibles liées. Il s’agit de la routine de propagation principale pour les blocs de messages.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
 Pointeur vers le message qui doit être propagée.  
  
##  <a name="release"></a>mise en production 

 Libère une réservation de message réussie précédente.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de réservée `message` objet.  
  
 `_PTarget`  
 Un pointeur vers le bloc cible qui appelle la `release` (méthode).  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
 La méthode lève un [bad_target](bad-target-class.md) exception si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.  
  
##  <a name="release_message"></a>release_message 

 En cas de substitution dans une classe dérivée, libère une réservation de message précédente.  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet est libéré.  
  
##  <a name="release_ref"></a>release_ref 

 Libère un décompte de références sur ce `source_block` objet.  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Pointeur vers le bloc cible qui appelle cette méthode.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par un `ITarget` objet dissocié de cette source. Le bloc source est autorisé à libérer les ressources réservées pour le bloc cible.  
  
##  <a name="remove_targets"></a>remove_targets 

 Supprime tous les liens de cible de ce bloc de code source. Cette opération doit être appelée à partir du destructeur.  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a>réserve 

 Réserve un message précédemment offert par ce `source_block` objet.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
 `_PTarget`  
 Un pointeur vers le bloc cible qui appelle la `reserve` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le message a été réservé avec succès, `false` dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a été déjà réservé ou accepté par une autre cible, la source pourrait refuser des réservations et ainsi de suite.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
 Après avoir appelé `reserve`, si elle réussit, vous devez appeler `consume` ou `release` afin d’accepter ou renoncer possession du message, respectivement.  
  
##  <a name="reserve_message"></a>reserve_message 

 En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce `source_block` objet.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le message a été réservé avec succès, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Après avoir `reserve` est appelée, si elle retourne `true`, `consume` ou `release` doit être appelé pour accepter ou libérer la possession du message.  
  
##  <a name="resume_propagation"></a>resume_propagation 

 En cas de substitution dans une classe dérivée, continue la propagation après qu’une réservation a été libérée.  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a>source_block 

 Construit un objet `source_block`.  
  
```
source_block();
```  
  
##  <a name="dtor"></a>~ source_block 

 Détruit le `source_block` objet.  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a>sync_send 

 Mode synchrone des files d’attente des messages et démarre une tâche de propagation, si cela n’a pas déjà été fait.  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Msg`  
 Un pointeur vers un `message` objet à envoyer de façon synchrone.  
  
##  <a name="unlink_target"></a>unlink_target 

 Dissocie un bloc cible à partir de ce `source_block` objet.  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Un pointeur vers un `ITarget` à dissocier de ce bloc `source_block` objet.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.  
  
##  <a name="unlink_target_notification"></a>unlink_target_notification 

 Un rappel qui notifie qu’une cible a été supprimée à partir de ce `source_block` objet.  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Le `ITarget` bloc qui a été supprimée.  
  
##  <a name="unlink_targets"></a>unlink_targets 

 Dissocie tous les blocs cibles à partir de ce `source_block` objet.  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends 

 Attend que toutes les propagations asynchrones soient terminées. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les propagations asynchrones disposent de temps à se terminer avant de détruire le bloc.  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [ISource, classe](isource-class.md)
