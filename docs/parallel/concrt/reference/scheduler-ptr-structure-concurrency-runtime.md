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
ms.openlocfilehash: 0da45fa18d12b3f1c93df6b8c8736ed1bfb58ade
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524994"
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

Retourne le pointeur brut au planificateur.

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valeur de retour

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Teste si le pointeur du planificateur n’est pas null.

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Se comporte comme un pointeur.

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr, constructeur

Crée un pointeur de planificateur de shared_ptr au planificateur.

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Paramètres

*Planificateur*<br/>
Le planificateur à convertir.

*pScheduler*<br/>
Le pointeur du planificateur à convertir.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
