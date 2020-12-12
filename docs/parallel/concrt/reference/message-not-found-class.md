---
description: 'En savoir plus sur : classe message_not_found'
title: message_not_found, classe
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: c0b098a530768617b2fa2cf52dfe374dc44a2c12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169383"
---
# <a name="message_not_found-class"></a>message_not_found, classe

Cette classe décrit une exception levée quand un bloc de messagerie ne parvient pas à trouver un message demandé.

## <a name="syntax"></a>Syntaxe

```cpp
class message_not_found : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[message_not_found](#ctor)|Surchargé. Construit un objet `message_not_found`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`message_not_found`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="message_not_found"></a><a name="ctor"></a> message_not_found

Construit un objet `message_not_found`.

```cpp
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
