---
description: 'En savoir plus sur : classe context_self_unblock'
title: context_self_unblock, classe
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 51fae67530e2836b92a6ab7a13e2b136f1d438c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188974"
---
# <a name="context_self_unblock-class"></a>context_self_unblock, classe

Cette classe décrit une exception levée quand la méthode `Unblock` d'un objet `Context` est appelée à partir du même contexte. Elle indique une tentative par un contexte donné de se débloquer.

## <a name="syntax"></a>Syntaxe

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[context_self_unblock](#ctor)|Surchargé. Construit un objet `context_self_unblock`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`context_self_unblock`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="context_self_unblock"></a><a name="ctor"></a> context_self_unblock

Construit un objet `context_self_unblock`.

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
