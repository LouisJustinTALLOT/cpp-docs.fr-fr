---
title: Classe Timer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8372e32b408b97a6ac652b0ff2ff5cc19de69b54
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693222"
---
# <a name="timer-class"></a>Classe timer
Un bloc de messagerie `timer` est un `source_block` à cible unique, capable d'envoyer un message à sa cible après un délai spécifié ou à intervalles spécifiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type de charge utile des messages de sortie de ce bloc.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[timer](#ctor)|Surchargé. Construit un `timer` bloc de messagerie qui déclenchera un message donné après un intervalle spécifié.|  
|[~ timer, destructeur](#dtor)|Détruit un `timer` bloc de messagerie.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[pause](#pause)|Arrête le `timer` bloc de messagerie. S’il s’agit d’une répétition `timer` bloc de messagerie, il peut être redémarré avec une ultérieure `start()` appeler. Non extensible pour les minuteries, cela a le même effet qu’un `stop` appeler.|  
|[start](#start)|Démarre le `timer` bloc de messagerie. Le nombre spécifié de millisecondes après cet est appelé, la valeur spécifiée sera propagée en aval comme un `message`.|  
|[stop](#stop)|Arrête le `timer` bloc de messagerie.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[accept_message](#accept_message)|Accepte un message qui a été offert par ce `timer` bloc de messagerie, transférer la propriété à l’appelant.|  
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `timer` et réservé par la cible, en transférant la propriété à l’appelant.|  
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `timer` bloc de messagerie.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Essaie d’offrir le message produit par le `timer` bloc pour toutes les cibles liées.|  
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block::release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `timer` bloc de messagerie. (Substitue [source_block::reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reprend la propagation après qu’une réservation a été libérée. (Substitue [source_block::resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ISource](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="accept_message"></a> accept_message 

 Accepte un message qui a été offert par ce `timer` bloc de messagerie, transférer la propriété à l’appelant.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MsgId`  
 Le `runtime_object_identity` de le proposé `message` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `message` que l’appelant possède désormais la propriété de l’objet.  
  
##  <a name="consume_message"></a> consume_message 

 Consomme un message précédemment offert par le `timer` et réservé par la cible, en transférant la propriété à l’appelant.  
  
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
  
##  <a name="link_target_notification"></a> link_target_notification 

 Rappel qui notifie qu’une nouvelle cible a été liée à ce `timer` bloc de messagerie.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Pointeur vers la cible qui vient d’être lié.  
  
##  <a name="pause"></a> Pause 

 Arrête le `timer` bloc de messagerie. S’il s’agit d’une répétition `timer` bloc de messagerie, il peut être redémarré avec une ultérieure `start()` appeler. Non extensible pour les minuteries, cela a le même effet qu’un `stop` appeler.  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Essaie d’offrir le message produit par le `timer` bloc pour toutes les cibles liées.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

 Réserve un message précédemment offert par ce `timer` bloc de messagerie.  
  
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
  
##  <a name="start"></a> Démarrer 

 Démarre le `timer` bloc de messagerie. Le nombre spécifié de millisecondes après cet est appelé, la valeur spécifiée sera propagée en aval comme un `message`.  
  
```
void start();
```  
  
##  <a name="stop"></a> Arrêter 

 Arrête le `timer` bloc de messagerie.  
  
```
void stop();
```  
  
##  <a name="ctor"></a> Minuterie 

 Construit un `timer` bloc de messagerie qui déclenchera un message donné après un intervalle spécifié.  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Ms`  
 Le nombre de millisecondes qui doivent s’écouler après l’appel de démarrage pour le message spécifié à la propagation en aval.  
  
 `value`  
 La valeur qui sera propagée en aval lorsque la minuterie est écoulé.  
  
 `_PTarget`  
 La cible à laquelle la minuterie propagera son message.  
  
 `_Repeating`  
 Si la valeur est true, indique que la minuterie déclenche périodiquement chaque `_Ms` millisecondes.  
  
 `_Scheduler`  
 Le `Scheduler` objet dans lequel la tâche de propagation du `timer` bloc de messagerie est planifiée est planifié.  
  
 `_ScheduleGroup`  
 Le `ScheduleGroup` objet dans lequel la tâche de propagation du `timer` bloc de messagerie est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.  
  
### <a name="remarks"></a>Notes  
 Le runtime utilise le planificateur par défaut si vous ne spécifiez pas le `_Scheduler` ou `_ScheduleGroup` paramètres.  
  
##  <a name="dtor"></a> ~ timer 

 Détruit un `timer` bloc de messagerie.  
  
```
~timer();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
