---
description: 'En savoir plus sur : classe context_unblock_unbalanced'
title: context_unblock_unbalanced, classe
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: d262ff52a675935f95664d2f7ddd69aa159aa0bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188961"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced, classe

Cette classe décrit une exception levée quand des appels aux méthodes `Block` et `Unblock` d'un objet `Context` ne sont pas correctement associés.

## <a name="syntax"></a>Syntaxe

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Surchargé. Construit un objet `context_unblock_unbalanced`.|

## <a name="remarks"></a>Notes

Les appels aux `Block` `Unblock` méthodes et d’un `Context` objet doivent toujours être couplés correctement. Le runtime d’accès concurrentiel permet aux opérations de se produire dans l’un ou l’autre ordre. Par exemple, un appel à `Block` peut être suivi d’un appel à `Unblock` , ou vice versa. Cette exception est levée si, par exemple, deux appels à la `Unblock` méthode ont été effectués dans une ligne, sur un `Context` objet qui n’a pas été bloqué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="context_unblock_unbalanced"></a><a name="ctor"></a> context_unblock_unbalanced

Construit un objet `context_unblock_unbalanced`.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
