---
title: message_processor, classe
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: 88944b2d935eebd0e031be1431c2a0f4efa3d760
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139469"
---
# <a name="message_processor-class"></a>message_processor, classe

La classe `message_processor` est la classe de base abstraite pour le traitement des objets `message`. Aucune garantie n'existe sur l'ordre des messages.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données de la charge utile au sein des messages gérés par cet objet `message_processor`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[async_send](#async_send)|En cas de substitution dans une classe dérivée, place les messages dans le bloc de manière asynchrone.|
|[sync_send](#sync_send)|En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.|
|[qu'](#wait)|En cas de substitution dans une classe dérivée, attend la fin de toutes les opérations asynchrones.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|En cas de substitution dans une classe dérivée, effectue le traitement en avant des messages dans le bloc. Appelée une fois chaque fois qu’un nouveau message est ajouté et que la file d’attente est vide.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`message_processor`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="async_send"></a>async_send

En cas de substitution dans une classe dérivée, place les messages dans le bloc de manière asynchrone.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Objet `message` à envoyer de façon asynchrone.

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="process_incoming_message"></a>process_incoming_message

En cas de substitution dans une classe dérivée, effectue le traitement en avant des messages dans le bloc. Appelée une fois chaque fois qu’un nouveau message est ajouté et que la file d’attente est vide.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Notes

Les implémentations de bloc de message doivent substituer cette méthode.

## <a name="sync_send"></a>sync_send

En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Objet `message` à envoyer de façon synchrone.

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="wait"></a>qu'

En cas de substitution dans une classe dérivée, attend la fin de toutes les opérations asynchrones.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ordered_message_processor, classe](ordered-message-processor-class.md)
