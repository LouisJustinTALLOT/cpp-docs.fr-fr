---
title: cancellation_token_registration, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
dev_langs: C++
helpviewer_keywords: cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70ab8114860a77582a6c9f6276b74122f9505c26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration, classe
La classe `cancellation_token_registration` représente une notification de rappel de `cancellation_token`. Quand la méthode `register` sur une classe `cancellation_token` est utilisée pour recevoir une notification relative à la date d'annulation, un objet `cancellation_token_registration` est retourné comme handle au rappel afin que l'appelant puisse demander qu'un rappel spécifique ne soit plus effectué via l'utilisation de la méthode `deregister`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[cancellation_token_registration](#ctor)||  
|[~ cancellation_token_registration, destructeur](#dtor)||  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** pplcancellation_token.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dtor"></a>~ cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="ctor"></a>cancellation_token_registration 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
##  <a name="operator_neq"></a>opérateur ! = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq"></a>opérateur = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq_eq"></a>opérateur == 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
