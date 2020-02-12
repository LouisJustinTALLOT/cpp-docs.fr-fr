---
title: invalid_oversubscribe_operation, classe
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140832"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation, classe

Cette classe décrit une exception levée lorsque la méthode `Context::Oversubscribe` est appelée avec le paramètre `_BeginOversubscription` ayant la valeur **false** sans appel antérieur à la méthode `Context::Oversubscribe` avec le paramètre `_BeginOversubscription` ayant la valeur **true**.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Surchargé. Construit un objet `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>invalid_oversubscribe_operation

Construit un objet `invalid_oversubscribe_operation`.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
