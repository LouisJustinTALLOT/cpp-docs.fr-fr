---
title: cancellation_token, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs: C++
helpviewer_keywords: cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a27bb4221e1a8db19f0dd7be37bb6ca3966635de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cancellationtoken-class"></a>cancellation_token, classe
La classe `cancellation_token` représente la capacité à déterminer si l'annulation d'une opération a été demandée. Un jeton donné peut être associé à un objet `task_group`, `structured_task_group` ou `task` pour entraîner une annulation implicite. Il peut également être sondé à la recherche d'une annulation ou comporter un rappel enregistré en cas d'annulation de la classe `cancellation_token_source` associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[cancellation_token](#ctor)||  
|[~ cancellation_token, destructeur](#dtor)||  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[deregister_callback](#deregister_callback)|Supprime un rappel précédemment enregistré à l'aide de la méthode `register` basée sur l'objet `cancellation_token_registration` retourné au moment de l'enregistrement.|  
|[is_cancelable](#is_cancelable)|Indique si ce jeton peut être annulé ou non.|  
|[is_canceled](#is_canceled)|Retourne `true` si le jeton a été annulé.|  
|[none](#none)|Retourne un jeton d'annulation qui ne pourra jamais faire l'objet d'une annulation.|  
|[register_callback](#register_callback)|Enregistre une fonction de rappel avec le jeton. Le rappel est effectué si et lorsque le jeton est annulé. Notez que si le jeton est déjà annulé lorsque cette méthode est appelée, le rappel est effectué immédiatement et de manière synchrone.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `cancellation_token`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** pplcancellation_token.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dtor"></a>~ cancellation_token 

```
~cancellation_token();
```  
  
##  <a name="ctor"></a>cancellation_token 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
##  <a name="deregister_callback"></a>deregister_callback 

 Supprime un rappel précédemment enregistré à l'aide de la méthode `register` basée sur l'objet `cancellation_token_registration` retourné au moment de l'enregistrement.  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Registration`  
 Objet `cancellation_token_registration` correspondant au rappel dont l'enregistrement doit être annulé. Ce jeton doit avoir été précédemment retourné par un appel à la méthode `register`.  
  
##  <a name="is_cancelable"></a>is_cancelable 

 Indique si ce jeton peut être annulé ou non.  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Indique si ce jeton peut être annulé ou non.  
  
##  <a name="is_canceled"></a>is_canceled 

 Retourne `true` si le jeton a été annulé.  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le jeton a été annulé ; sinon `false`.  
  
##  <a name="none"></a>Aucun 

 Retourne un jeton d'annulation qui ne pourra jamais faire l'objet d'une annulation.  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Jeton d'annulation qui ne peut pas être annulé.  
  
##  <a name="operator_neq"></a>opérateur ! = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq"></a>opérateur = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq_eq"></a>opérateur == 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="register_callback"></a>register_callback 

 Enregistre une fonction de rappel avec le jeton. Le rappel est effectué si et lorsque le jeton est annulé. Notez que si le jeton est déjà annulé lorsque cette méthode est appelée, le rappel est effectué immédiatement et de manière synchrone.  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Function`  
 Type de l'objet de fonction qui est rappelé lorsque `cancellation_token` est annulé.  
  
 `_Func`  
 Objet de fonction qui est rappelé lorsque `cancellation_token` est annulé.  
  
### <a name="return-value"></a>Valeur de retour  
 Objet `cancellation_token_registration` qui peut être utilisé dans la méthode `deregister` pour annuler l'enregistrement d'un rappel précédemment enregistré et l'empêcher d'être effectué. La méthode lève un [invalid_operation](invalid-operation-class.md) exception si elle est appelée sur une `cancellation_token` objet qui a été créé à l’aide de la [cancellation_token::none](#none) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
