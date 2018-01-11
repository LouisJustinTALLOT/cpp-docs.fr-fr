---
title: Call, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs: C++
helpviewer_keywords: call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d575aaa01a3668925c6a81eda7d8d99cc591180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="call-class"></a>call, classe
Un bloc de messagerie `call` est un `target_block` ordonné à plusieurs sources qui appelle une fonction spécifiée lors de la réception d'un message.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de charge utile des messages propagés à ce bloc.  
  
 `_FunctorType`  
 La signature des fonctions que ce bloc peut accepter.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[appel](#ctor)|Surchargé. Construit un `call` bloc de messagerie.|  
|[~ call, destructeur](#dtor)|Détruit le `call` bloc de messagerie.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|Exécute la fonction d’appel sur les messages d’entrée.|  
|[process_message](#process_message)|Traite un message qui a été accepté par ce `call` bloc de messagerie.|  
|[propagate_message](#propagate_message)|Passe un message à partir de façon asynchrone un `ISource` à ce bloc `call` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[send_message](#send_message)|Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `call` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|  
|[supports_anonymous_source](#supports_anonymous_source)|Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée. (Substitue [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a>appel 

 Construit un `call` bloc de messagerie.  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Func`  
 Une fonction qui sera appelée pour chaque message accepté.  
  
 `_Filter`  
 Une fonction de filtre qui détermine si les messages transmis doivent être acceptés.  
  
 `_PScheduler`  
 Le `Scheduler` objet dans lequel la tâche de propagation du `call` bloc de messagerie est planifiée.  
  
 `_PScheduleGroup`  
 Le `ScheduleGroup` objet dans lequel la tâche de propagation du `call` bloc de messagerie est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.  
  
### <a name="remarks"></a>Notes  
 Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .  
  
 Le type `_Call_method` est un functor avec la signature `void (T const &)` qui est appelé par ce `call` bloc de messagerie pour traiter un message.  
  
 Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `call` bloc de messagerie pour déterminer si elle doit accepter un message proposé.  
  
##  <a name="dtor"></a>~ appeler 

 Détruit le `call` bloc de messagerie.  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Exécute la fonction d’appel sur les messages d’entrée.  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 Traite un message qui a été accepté par ce `call` bloc de messagerie.  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PMessage`  
 Pointeur vers le message qui doit être gérée.  
  
##  <a name="propagate_message"></a>propagate_message 

 Passe un message à partir de façon asynchrone un `ISource` à ce bloc `call` bloc de messagerie. Il est appelé par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.  
  
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
  
##  <a name="send_message"></a>send_message 

 Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `call` bloc de messagerie. Il est appelé par le `send` (méthode), lorsqu’elle est appelée par un bloc source.  
  
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
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Étant donné que le bloc de ne pas reporter des messages transmis.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [transformer, classe](transformer-class.md)
