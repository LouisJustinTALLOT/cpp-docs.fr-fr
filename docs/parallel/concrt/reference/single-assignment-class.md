---
title: Classe single_assignment | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
dev_langs:
- C++
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bacbdaa4af141101863b4d6d81d114d43aced9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="singleassignment-class"></a>Classe single_assignment
Un bloc de messagerie `single_assignment` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un `message` unique écrit une seule fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de charge utile du message stocké et propagé par la mémoire tampon.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[single_assignment](#ctor)|Surchargé. Construit un `single_assignment` bloc de messagerie.|  
|[~ single_assignment, destructeur](#dtor)|Détruit le `single_assignment` bloc de messagerie.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[has_value](#has_value)|Vérifie si cela `single_assignment` bloc de messagerie a encore été initialisé avec une valeur.|  
|[value](#value)|Obtient une référence à la charge utile actuelle du message qui est stocké dans le `single_assignment` bloc de messagerie.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[accept_message](#accept_message)|Accepte un message qui a été offert par ce `single_assignment` bloc de messagerie, retournant une copie du message à l’appelant.|  
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `single_assignment` et réservé par la cible, en retournant une copie du message à l’appelant.|  
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `single_assignment` bloc de messagerie.|  
|[propagate_message](#propagate_message)|Passe un message à partir de façon asynchrone un `ISource` à ce bloc `single_assignment` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Place le `message _PMessage` dans ce `single_assignment` bloc de messagerie et offre à toutes les cibles liées.|  
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `single_assignment` bloc de messagerie. (Substitue [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reprend la propagation après qu’une réservation a été libérée. (Substitue [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `single_assignment` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|  
  
## <a name="remarks"></a>Notes  
 A `single_assignment` bloc de messagerie propage des copies de son message à chaque cible.  
  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `single_assignment`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 Accepte un message qui a été offert par ce `single_assignment` bloc de messagerie, retournant une copie du message à l’appelant.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 Le `single_assignment` messagerie bloc retourne des copies du message à ses cibles, au lieu de transférer la propriété du message actuellement détenu.  
  
##  <a name="consume_message"></a> consume_message 

 Consomme un message précédemment offert par le `single_assignment` et réservé par la cible, en retournant une copie du message à l’appelant.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet ayant été consommé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 Semblable à `accept`, mais est toujours précédé par un appel à `reserve`.  
  
##  <a name="has_value"></a> has_value 

 Vérifie si cela `single_assignment` bloc de messagerie a encore été initialisé avec une valeur.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bloc a reçu une valeur, `false` dans le cas contraire.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Rappel qui notifie qu’une nouvelle cible a été liée à ce `single_assignment` bloc de messagerie.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Pointeur vers la cible qui vient d’être lié.  
  
##  <a name="propagate_message"></a> propagate_message 

 Passe un message à partir de façon asynchrone un `ISource` à ce bloc `single_assignment` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.  
  
```
virtual message_status propagate_message(
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

 Place le `message` `_PMessage` dans ce `single_assignment` bloc de messagerie et offre à toutes les cibles liées.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
 Un pointeur vers un `message` par ce `single_assignment` bloc de messagerie a pris la propriété.  
  
##  <a name="release_message"></a> release_message 

 Libère une réservation de message précédente.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet est libéré.  
  
##  <a name="reserve_message"></a> reserve_message 

 Réserve un message précédemment offert par ce `single_assignment` bloc de messagerie.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le message a été réservé avec succès, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Après avoir `reserve` est appelée, si elle retourne `true`, `consume` ou `release` doit être appelé pour accepter ou libérer la possession du message.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Reprend la propagation après qu’une réservation a été libérée.  
  
```
virtual void resume_propagation();
```  
  
##  <a name="send_message"></a> send_message 

 Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `single_assignment` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.  
  
```
virtual message_status send_message(
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
  
##  <a name="ctor"></a> single_assignment 

 Construit un `single_assignment` bloc de messagerie.  
  
```
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Filter`  
 Une fonction de filtre qui détermine si les messages transmis doivent être acceptés.  
  
 `_PScheduler`  
 Le `Scheduler` objet dans lequel la tâche de propagation du `single_assignment` bloc de messagerie est planifiée.  
  
 `_PScheduleGroup`  
 Le `ScheduleGroup` objet dans lequel la tâche de propagation du `single_assignment` bloc de messagerie est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.  
  
### <a name="remarks"></a>Notes  
 Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .  
  
 Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `single_assignment` bloc de messagerie pour déterminer si elle doit accepter un message proposé.  
  
##  <a name="dtor"></a> ~ single_assignment 

 Détruit le `single_assignment` bloc de messagerie.  
  
```
~single_assignment();
```  
  
##  <a name="value"></a> Valeur 

 Obtient une référence à la charge utile actuelle du message qui est stocké dans le `single_assignment` bloc de messagerie.  
  
```
T const& value();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La charge utile du message stocké.  
  
### <a name="remarks"></a>Notes  
 Cette méthode attend jusqu'à ce qu’un message arrive si aucun message n’est actuellement stocké dans le `single_assignment` bloc de messagerie.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Classe overwrite_buffer](overwrite-buffer-class.md)   
 [Classe unbounded_buffer](unbounded-buffer-class.md)

