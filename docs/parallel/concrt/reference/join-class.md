---
title: Join, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee69daa9ec5570d89d407c980e4ff20deca6360
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="join-class"></a>join, classe
Un bloc de messagerie `join` est un `propagator_block` à cible unique, à sources multiples et ordonné qui combine des messages de type `T` en provenance de chacune de ses sources.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de charge utile des messages joints et propagés par le bloc.  
  
 `_Jtype`  
 Le genre de `join` bloc est `greedy` ou `non_greedy`  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[join](#ctor)|Surchargé. Construit un `join` bloc de messagerie.|  
|[~join Destructor](#dtor)|Détruit le `join` bloc.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[accept_message](#accept_message)|Accepte un message qui a été offert par ce `join` bloc de messagerie, transférer la propriété à l’appelant.|  
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `join` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.|  
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `join` bloc de messagerie.|  
|[propagate_message](#propagate_message)|Passe un message à partir de façon asynchrone un `ISource` à ce bloc `join` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Construit un message de sortie contenant un message d’entrée de chaque source lorsqu’ils ont tous propagé un message. Envoie ce message de sortie à chacune de ses cibles.|  
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `join` bloc de messagerie. (Substitue [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reprend la propagation après qu’une réservation a été libérée. (Substitue [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 Accepte un message qui a été offert par ce `join` bloc de messagerie, transférer la propriété à l’appelant.  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
##  <a name="consume_message"></a> consume_message 

 Consomme un message précédemment offert par le `join` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet ayant été consommé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 Semblable à `accept`, mais est toujours précédé par un appel à `reserve`.  
  
##  <a name="ctor"></a> Joindre 

 Construit un `join` bloc de messagerie.  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Paramètres  
 `_NumInputs`  
 Nombre d’entrées cela `join` bloc sera autorisé.  
  
 `_Filter`  
 Une fonction de filtre qui détermine si les messages transmis doivent être acceptés.  
  
 `_PScheduler`  
 Le `Scheduler` objet dans lequel la tâche de propagation du `join` bloc de messagerie est planifiée.  
  
 `_PScheduleGroup`  
 Le `ScheduleGroup` objet dans lequel la tâche de propagation du `join` bloc de messagerie est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.  
  
### <a name="remarks"></a>Notes  
 Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .  
  
 Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `join` bloc de messagerie pour déterminer si elle doit accepter un message proposé.  
  
##  <a name="dtor"></a> ~join 

 Détruit le `join` bloc.  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Rappel qui notifie qu’une nouvelle cible a été liée à ce `join` bloc de messagerie.  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 Passe un message à partir de façon asynchrone un `ISource` à ce bloc `join` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.  
  
```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
 Pointeur vers l'objet `message`.  
  
 `_PSource`  
 Pointeur vers le bloc source qui transmet le message.  
  
### <a name="return-value"></a>Valeur de retour  
 A [message_status](concurrency-namespace-enums.md) indication de ce que la cible décidé de faire avec le message.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Construit un message de sortie contenant un message d’entrée de chaque source lorsqu’ils ont tous propagé un message. Envoie ce message de sortie à chacune de ses cibles.  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a> release_message 

 Libère une réservation de message précédente.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet est libéré.  
  
##  <a name="reserve_message"></a> reserve_message 

 Réserve un message précédemment offert par ce `join` bloc de messagerie.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le message a été réservé avec succès, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Après avoir `reserve` est appelée, si elle retourne `true`, `consume` ou `release` doit être appelé pour accepter ou libérer la possession du message.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Reprend la propagation après qu’une réservation a été libérée.  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Classe Choice](choice-class.md)   
 [multitype_join, classe](multitype-join-class.md)
