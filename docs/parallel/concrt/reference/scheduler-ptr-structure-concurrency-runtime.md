---
title: Structure scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358766"
---
# <a name="scheduler_ptr-structure"></a>Structure scheduler_ptr

Représente un pointeur vers un planificateur. Cette classe existe pour permettre la spécification d’une durée de vie partagée en utilisant shared_ptr ou tout simplement une référence simple en utilisant pointeur brut.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[scheduler_ptr::obtenir](#get)|Retourne le pointeur brut au planificateur|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_ptr::opérateur bool](#operator_bool)|Teste si le pointeur du planificateur a une valeur non null|
|[scheduler_ptr::opérateur-&gt;](#operator_ptr)|Se comporte comme un pointeur|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scheduler_ptr`

## <a name="requirements"></a>Spécifications

**En-tête:** pplinterface.h

**Namespace:** concurrence

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr::obtenir la méthode

Retourne le pointeur brut au planificateur.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valeur de retour

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::opérateur bool

Teste si le pointeur de calendrier n’est pas nul.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr::opérateur-&gt;

Se comporte comme un pointeur.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr::scheduler_ptr Constructeur

Crée un pointeur de planificateur de shared_ptr à l’horaire.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Paramètres

*Planificateur*<br/>
L’planificateur à convertir.

*pScheduler*<br/>
Le pointeur de planificateur à convertir.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
