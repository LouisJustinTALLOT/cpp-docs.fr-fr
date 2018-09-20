---
title: context_unblock_unbalanced, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs:
- C++
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cd35b53db37d51a9feec567fe66c53b1381b4d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431331"
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced, classe

Cette classe décrit une exception levée quand des appels aux méthodes `Block` et `Unblock` d'un objet `Context` ne sont pas correctement associés.

## <a name="syntax"></a>Syntaxe

```
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Surchargé. Construit un objet `context_unblock_unbalanced`.|

## <a name="remarks"></a>Notes

Les appels à la `Block` et `Unblock` méthodes d’un `Context` objet doit toujours être associé correctement. Le Runtime d’accès concurrentiel autorise les opérations se produire dans les deux sens. Par exemple, un appel à `Block` peut être suivie d’un appel à `Unblock`, ou vice versa. Cette exception serait levée si, par exemple, deux appels à la `Unblock` méthode ont été apportées dans une ligne, sur un `Context` objet qui n’a pas été bloqué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> context_unblock_unbalanced

Construit un objet `context_unblock_unbalanced`.

```
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
