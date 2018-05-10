---
title: message_processor, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95e95cc84ca999402e0d64c0699750bb92203cef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="messageprocessor-class"></a>message_processor, classe
La classe `message_processor` est la classe de base abstraite pour le traitement des objets `message`. Aucune garantie n'existe sur l'ordre des messages.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données de la charge utile dans les messages gérés par cet `message_processor` objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`type`|Alias de type pour `T`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[async_send](#async_send)|En cas de substitution dans une classe dérivée, place de façon asynchrone des messages dans le bloc.|  
|[sync_send](#sync_send)|En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.|  
|[attente](#wait)|En cas de substitution dans une classe dérivée, attend que toutes les opérations asynchrones se termine.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|En cas de substitution dans une classe dérivée, effectue le traitement de transfert des messages dans le bloc. Appelé à chaque fois qu’un nouveau message est ajouté et la file d’attente n’est pas vide.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `message_processor`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="async_send"></a> async_send 

 En cas de substitution dans une classe dérivée, place de façon asynchrone des messages dans le bloc.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Msg`  
 A `message` objet à envoyer de façon asynchrone.  
  
### <a name="remarks"></a>Notes  
 Les implémentations de processeur doivent substituer cette méthode.  
  
##  <a name="process_incoming_message"></a> process_incoming_message 

 En cas de substitution dans une classe dérivée, effectue le traitement de transfert des messages dans le bloc. Appelé à chaque fois qu’un nouveau message est ajouté et la file d’attente n’est pas vide.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Notes  
 Les implémentations de bloc de message doivent substituer cette méthode.  
  
##  <a name="sync_send"></a> sync_send 

 En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Msg`  
 A `message` objet à envoyer de façon synchrone.  
  
### <a name="remarks"></a>Notes  
 Les implémentations de processeur doivent substituer cette méthode.  
  
##  <a name="wait"></a> attente 

 En cas de substitution dans une classe dérivée, attend que toutes les opérations asynchrones se termine.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Notes  
 Les implémentations de processeur doivent substituer cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [ordered_message_processor, classe](ordered-message-processor-class.md)
