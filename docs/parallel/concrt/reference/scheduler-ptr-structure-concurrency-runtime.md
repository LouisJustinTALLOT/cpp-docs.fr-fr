---
title: scheduler_ptr, Structure
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 7fd81a1ccf6702c74a013c5772d59f01121b61a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479220"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr, Structure

Représente un pointeur vers un planificateur. Cette classe existe pour permettre la spécification d’une durée de vie partagée à l’aide de shared_ptr ou simplement une référence simple à l’aide du pointeur brut.

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

## <a name="requirements"></a>Configuration requise

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

'''operator bool() const ;
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

*scheduler*<br/>
The scheduler to convert.

*pScheduler*<br/>
The scheduler pointer to convert.

## See Also

[concurrency Namespace](concurrency-namespace.md)
