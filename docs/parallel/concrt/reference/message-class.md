---
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
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139540"
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

|Name|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[message](#ctor)|Surchargé. Construit un objet `message`.|
|[~ message, destructeur](#dtor)|Détruit l’objet `message`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[add_ref](#add_ref)|Ajoute au décompte de références pour l’objet `message`. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.|
|[msg_id](#msg_id)|Retourne l’ID de l’objet `message`.|
|[remove_ref](#remove_ref)|Soustrait du décompte de références pour l’objet `message`. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[payload](#payload)|Charge utile de l’objet `message`.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`message`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="add_ref"></a>add_ref

Ajoute au décompte de références pour l’objet `message`. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.

```cpp
long add_ref();
```

### <a name="return-value"></a>Valeur de retour

Nouvelle valeur du décompte de références.

## <a name="ctor"></a>Message

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
Référence ou pointeur vers un objet `message`.

### <a name="remarks"></a>Notes

Le constructeur qui prend un pointeur vers un objet `message` en tant qu’argument lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_Msg` est `NULL`.

## <a name="dtor"></a>~ message

Détruit l’objet `message`.

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

Retourne l’ID de l’objet `message`.

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `runtime_object_identity` de l'objet `message`.

## <a name="payload"></a>transport

Charge utile de l’objet `message`.

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

Soustrait du décompte de références pour l’objet `message`. Utilisé pour les blocs de message qui nécessitent un décompte de références pour déterminer la durée de vie des messages.

```cpp
long remove_ref();
```

### <a name="return-value"></a>Valeur de retour

Nouvelle valeur du décompte de références.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
