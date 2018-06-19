---
title: scheduler_ptr::structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672e4a0dd5f66ab613dde8877915c799d6c4b2f4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686982"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr, Structure
Représente un pointeur vers un planificateur. Cette classe a pour fonction de permettre la spécification d'une durée de vie partagée à l'aide de shared_ptr ou d'une référence simple à l'aide d'un pointeur brut.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|Surchargé. Crée un pointeur de planificateur de shared_ptr vers le planificateur|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|Retourne le pointeur brut au planificateur|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[scheduler_ptr::operator bool](#operator_bool)|Teste si le pointeur du planificateur a une valeur non null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Se comporte comme un pointeur|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `scheduler_ptr`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** pplinterface.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="get"></a>  scheduler_ptr::Get, méthode  
 Retourne le pointeur brut au planificateur  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_bool"></a>  scheduler_ptr::operator bool   
 Teste si le pointeur du planificateur a une valeur non null  
  
''' bool() opérateur const ;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
opérateur de scheduler_interface* -> () const ;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
scheduler_ptr explicite (std::shared_ptr < scheduler_interface > du Planificateur) ;

scheduler_ptr explicite (_In_opt_ scheduler_interface * pScheduler) ;
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
