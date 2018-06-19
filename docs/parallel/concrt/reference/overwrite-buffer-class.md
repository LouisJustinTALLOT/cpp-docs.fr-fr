---
title: Classe overwrite_buffer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dccde651898bf5ff0986dc2e577a1d2ee5765e3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694194"
---
# <a name="overwritebuffer-class"></a>Classe overwrite_buffer
Un bloc de messagerie `overwrite_buffer` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un seul message à la fois. Les nouveaux messages remplacent ceux précédemment conservés.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de charge utile des messages stockés et propagés par la mémoire tampon.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[overwrite_buffer](#ctor)|Surchargé. Construit un `overwrite_buffer` bloc de messagerie.|  
|[~ overwrite_buffer, destructeur](#dtor)|Détruit le `overwrite_buffer` bloc de messagerie.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[has_value](#has_value)|Vérifie si cela `overwrite_buffer` bloc de messagerie a déjà une valeur.|  
|[value](#value)|Obtient une référence à la charge utile actuelle du message qui est stocké dans le `overwrite_buffer` bloc de messagerie.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[accept_message](#accept_message)|Accepte un message qui a été offert par ce `overwrite_buffer` bloc de messagerie, retournant une copie du message à l’appelant.|  
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `overwrite_buffer` bloc de messagerie et réservé par la cible, en retournant une copie du message à l’appelant.|  
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `overwrite_buffer` bloc de messagerie.|  
|[propagate_message](#propagate_message)|Passe un message à partir de façon asynchrone un `ISource` à ce bloc `overwrite_buffer` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Place le `message _PMessage` dans ce `overwrite_buffer` bloc de messagerie et offre à toutes les cibles liées.|  
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `overwrite_buffer` bloc de messagerie. (Substitue [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reprend la propagation après qu’une réservation a été libérée. (Substitue [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `overwrite_buffer` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[supports_anonymous_source](#supports_anonymous_source)|Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée. (Substitue [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Notes  
 Un `overwrite_buffer` bloc de messagerie propage des copies de son message stocké vers chacune de ses cibles.  
  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 Accepte un message qui a été offert par ce `overwrite_buffer` bloc de messagerie, retournant une copie du message à l’appelant.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
### <a name="remarks"></a>Notes  
 Le `overwrite_buffer` messagerie bloc retourne des copies du message à ses cibles, au lieu de transférer la propriété du message actuellement détenu.  
  
##  <a name="consume_message"></a> consume_message 

 Consomme un message précédemment offert par le `overwrite_buffer` bloc de messagerie et réservé par la cible, en retournant une copie du message à l’appelant.  
  
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

 Vérifie si cela `overwrite_buffer` bloc de messagerie a déjà une valeur.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bloc a reçu une valeur, `false` dans le cas contraire.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Rappel qui notifie qu’une nouvelle cible a été liée à ce `overwrite_buffer` bloc de messagerie.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Pointeur vers la cible qui vient d’être lié.  
  
##  <a name="dtor"></a> ~overwrite_buffer 

 Détruit le `overwrite_buffer` bloc de messagerie.  
  
```
~overwrite_buffer();
```  
  
##  <a name="ctor"></a> overwrite_buffer 

 Construit un `overwrite_buffer` bloc de messagerie.  
  
```
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Filter`  
 Une fonction de filtre qui détermine si les messages transmis doivent être acceptés.  
  
 `_PScheduler`  
 Le `Scheduler` objet dans lequel la tâche de propagation du `overwrite_buffer` bloc de messagerie est planifiée.  
  
 `_PScheduleGroup`  
 Le `ScheduleGroup` objet dans lequel la tâche de propagation du `overwrite_buffer` bloc de messagerie est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.  
  
### <a name="remarks"></a>Notes  
 Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .  
  
 Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `overwrite_buffer` bloc de messagerie pour déterminer si elle doit accepter un message proposé.  
  
##  <a name="propagate_message"></a> propagate_message 

 Passe un message à partir de façon asynchrone un `ISource` à ce bloc `overwrite_buffer` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.  
  
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

 Place le `message _PMessage` dans ce `overwrite_buffer` bloc de messagerie et offre à toutes les cibles liées.  
  
```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
 Un pointeur vers un `message` objet que cette `overwrite_buffer` a pris la propriété.  
  
### <a name="remarks"></a>Notes  
 Cette méthode remplace le message actuel dans le `overwrite_buffer` avec le message accepté récemment `_PMessage`.  
  
##  <a name="send_message"></a> send_message 

 Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `overwrite_buffer` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.  
  
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
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Étant donné que le bloc de ne pas reporter des messages transmis.  
  
##  <a name="release_message"></a> release_message 

 Libère une réservation de message précédente.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de la `message` de l’objet est libéré.  
  
##  <a name="reserve_message"></a> reserve_message 

 Réserve un message précédemment offert par ce `overwrite_buffer` bloc de messagerie.  
  
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
  
##  <a name="value"></a> Valeur 

 Obtient une référence à la charge utile actuelle du message qui est stocké dans le `overwrite_buffer` bloc de messagerie.  
  
```
T value();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La charge utile du message actuellement stocké.  
  
### <a name="remarks"></a>Notes  
 La valeur stockée dans le `overwrite_buffer` peut changer immédiatement après que cette méthode est retournée. Cette méthode attend jusqu'à ce qu’un message arrive si aucun message n’est actuellement stocké dans le `overwrite_buffer`.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Classe unbounded_buffer](unbounded-buffer-class.md)   
 [single_assignment, classe](single-assignment-class.md)
