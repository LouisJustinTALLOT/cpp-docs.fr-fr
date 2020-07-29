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
ms.openlocfilehash: 0c95d234fee412c1dacb014dd135ca56fc73bf5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193963"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation, classe

Cette classe décrit une exception levée lorsque la `Context::Oversubscribe` méthode est appelée avec le `_BeginOversubscription` paramètre défini sur **`false`** sans appel préalable à la `Context::Oversubscribe` méthode avec le `_BeginOversubscription` paramètre défini sur **`true`** .

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Surchargé. Construit un objet `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_oversubscribe_operation"></a><a name="ctor"></a>invalid_oversubscribe_operation

Construit un objet `invalid_oversubscribe_operation`.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
