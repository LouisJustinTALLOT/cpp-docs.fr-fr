---
title: message_not_found, classe
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: 63b921e47b01e3be7dfc060cbb41e5fd9016d04f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139572"
---
# <a name="message_not_found-class"></a>message_not_found, classe

Cette classe décrit une exception levée quand un bloc de messagerie ne parvient pas à trouver un message demandé.

## <a name="syntax"></a>Syntaxe

```cpp
class message_not_found : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[message_not_found](#ctor)|Surchargé. Construit un objet `message_not_found`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`message_not_found`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>message_not_found

Construit un objet `message_not_found`.

```cpp
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
