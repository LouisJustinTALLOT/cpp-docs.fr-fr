---
title: context_unblock_unbalanced, classe
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143093"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced, classe

Cette classe décrit une exception levée quand des appels aux méthodes `Block` et `Unblock` d'un objet `Context` ne sont pas correctement associés.

## <a name="syntax"></a>Syntaxe

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Surchargé. Construit un objet `context_unblock_unbalanced`.|

## <a name="remarks"></a>Notes

Les appels aux méthodes `Block` et `Unblock` d’un objet `Context` doivent toujours être couplés correctement. Le runtime d’accès concurrentiel permet aux opérations de se produire dans l’un ou l’autre ordre. Par exemple, un appel à `Block` peut être suivi d’un appel à `Unblock`, ou vice versa. Cette exception est levée si, par exemple, deux appels à la méthode `Unblock` ont été effectués dans une ligne, sur un objet `Context` qui n’a pas été bloqué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>context_unblock_unbalanced

Construit un objet `context_unblock_unbalanced`.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
