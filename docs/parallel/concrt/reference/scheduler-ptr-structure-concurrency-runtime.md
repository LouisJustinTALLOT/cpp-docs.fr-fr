---
description: 'En savoir plus sur : structure scheduler_ptr'
title: Structure scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 314f587c0fd55772a8b1b7b5b8fdf3ddeb53a7a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188779"
---
# <a name="scheduler_ptr-structure"></a>Structure scheduler_ptr

Représente un pointeur vers un planificateur. Cette classe existe pour permettre la spécification d’une durée de vie partagée à l’aide de shared_ptr ou simplement d’une référence simple à l’aide d’un pointeur brut.

## <a name="syntax"></a>Syntaxe

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_ptr :: scheduler_ptr](#ctor)|Surchargé. Crée un pointeur de planificateur de shared_ptr vers le planificateur|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[scheduler_ptr :: obtient](#get)|Retourne le pointeur brut au planificateur|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_ptr :: operator bool](#operator_bool)|Teste si le pointeur du planificateur a une valeur non null|
|[scheduler_ptr :: Operator-&gt;](#operator_ptr)|Se comporte comme un pointeur|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scheduler_ptr`

## <a name="requirements"></a>Spécifications

**En-tête :** pplinterface. h

**Espace de noms :** concurrence

## <a name="scheduler_ptrget-method"></a><a name="get"></a> scheduler_ptr :: méthode d’extraction

Retourne le pointeur brut vers le planificateur.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a> scheduler_ptr :: operator bool

Teste si le pointeur du planificateur a une valeur non null.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a> scheduler_ptr :: Operator-&gt;

Se comporte comme un pointeur.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a> scheduler_ptr :: scheduler_ptr, constructeur

Crée un pointeur de planificateur à partir de shared_ptr vers le planificateur.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Paramètres

*planificateur*<br/>
Planificateur à convertir.

*pScheduler*<br/>
Pointeur de planificateur à convertir.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
