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
ms.openlocfilehash: da0a44b90346959756c1ef7c685bef234fe6e46a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296681"
---
# <a name="messagenotfound-class"></a>message_not_found, classe

Cette classe décrit une exception levée quand un bloc de messagerie ne parvient pas à trouver un message demandé.

## <a name="syntax"></a>Syntaxe

```
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

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> message_not_found

Construit un objet `message_not_found`.

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
