---
description: 'En savoir plus sur : classe message_processor'
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
ms.openlocfilehash: f74314bde6e12ea8b00bfc7bfd2567ca15864f75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202195"
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
Type de données de la charge utile au sein des messages gérés par cet `message_processor` objet.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[async_send](#async_send)|En cas de substitution dans une classe dérivée, place les messages dans le bloc de manière asynchrone.|
|[sync_send](#sync_send)|En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.|
|[wait](#wait)|En cas de substitution dans une classe dérivée, attend la fin de toutes les opérations asynchrones.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|En cas de substitution dans une classe dérivée, effectue le traitement en avant des messages dans le bloc. Appelée une fois chaque fois qu’un nouveau message est ajouté et que la file d’attente est vide.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`message_processor`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="async_send"></a><a name="async_send"></a> async_send

En cas de substitution dans une classe dérivée, place les messages dans le bloc de manière asynchrone.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
`message`Objet à envoyer de façon asynchrone.

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="process_incoming_message"></a><a name="process_incoming_message"></a> process_incoming_message

En cas de substitution dans une classe dérivée, effectue le traitement en avant des messages dans le bloc. Appelée une fois chaque fois qu’un nouveau message est ajouté et que la file d’attente est vide.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Notes

Les implémentations de bloc de message doivent substituer cette méthode.

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

En cas de substitution dans une classe dérivée, place les messages dans le bloc de façon synchrone.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
`message`Objet à envoyer de façon synchrone.

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="wait"></a><a name="wait"></a> qu'

En cas de substitution dans une classe dérivée, attend la fin de toutes les opérations asynchrones.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>Notes

Les implémentations de processeur doivent substituer cette méthode.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe ordered_message_processor](ordered-message-processor-class.md)
