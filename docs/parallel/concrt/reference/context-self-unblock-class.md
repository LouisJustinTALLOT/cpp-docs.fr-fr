---
title: context_self_unblock, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
dev_langs:
- C++
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36bfc6053ddbfb68598e1465896f94bb0a895f1b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435894"
---
# <a name="contextselfunblock-class"></a>context_self_unblock, classe

Cette classe décrit une exception levée quand la méthode `Unblock` d'un objet `Context` est appelée à partir du même contexte. Elle indique une tentative par un contexte donné de se débloquer.

## <a name="syntax"></a>Syntaxe

```
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

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> context_self_unblock

Construit un objet `context_self_unblock`.

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
