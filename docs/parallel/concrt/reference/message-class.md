---
description: 'En savoir plus sur : classe de message'
title: message, classe
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 0e15dafd9606e68f7a6ed1bed3795791c0f6870c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202312"
---
# <a name="message-class"></a>message, classe

Enveloppe de message de base contenant la charge utile de données transmise entre les blocs de messagerie.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données de la charge utile dans le message.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[message](#ctor)|Surchargé. Construit un objet `message`.|
|[~ message, destructeur](#dtor)|Détruit l' `message` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[add_ref](#add_ref)|Ajoute au décompte de références pour l' `message` objet. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.|
|[msg_id](#msg_id)|Retourne l’ID de l' `message` objet.|
|[remove_ref](#remove_ref)|Soustrait du décompte de références pour l' `message` objet. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[payload](#payload)|Charge utile de l' `message` objet.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`message`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="add_ref"></a><a name="add_ref"></a> add_ref

Ajoute au décompte de références pour l' `message` objet. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.

```cpp
long add_ref();
```

### <a name="return-value"></a>Valeur renvoyée

Nouvelle valeur du décompte de références.

## <a name="message"></a><a name="ctor"></a> Message

Construit un objet `message`.

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>Paramètres

*_P*<br/>
Charge utile de ce message.

*_Id*<br/>
ID unique de ce message.

*_Msg*<br/>
Référence ou pointeur vers un `message` objet.

### <a name="remarks"></a>Notes

Le constructeur qui prend un pointeur vers un `message` objet en tant qu’argument lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_Msg` a la valeur `NULL` .

## <a name="message"></a><a name="dtor"></a> ~ message

Détruit l' `message` objet.

```cpp
virtual ~message();
```

## <a name="msg_id"></a><a name="msg_id"></a> msg_id

Retourne l’ID de l' `message` objet.

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet `runtime_object_identity` de l'objet `message`.

## <a name="payload"></a><a name="payload"></a> transport

Charge utile de l' `message` objet.

```cpp
T const payload;
```

## <a name="remove_ref"></a><a name="remove_ref"></a> remove_ref

Soustrait du décompte de références pour l' `message` objet. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.

```cpp
long remove_ref();
```

### <a name="return-value"></a>Valeur renvoyée

Nouvelle valeur du décompte de références.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
