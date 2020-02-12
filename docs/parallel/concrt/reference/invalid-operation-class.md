---
title: invalid_operation, classe
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: e17d530569d16ba0084a58bf0be00d4a8423b7f6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140880"
---
# <a name="invalid_operation-class"></a>invalid_operation, classe

Cette classe décrit une exception qui est levée quand une opération non valide qui n'est pas décrite de façon plus précise par un autre type d'exception levé par le runtime d'accès concurrentiel est exécutée.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_operation : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[invalid_operation](#ctor)|Surchargé. Construit un objet `invalid_operation`.|

## <a name="remarks"></a>Notes

Les différentes méthodes qui lèvent cette exception indiquent généralement dans quelles circonstances elles agissent ainsi.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_operation`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>invalid_operation

Construit un objet `invalid_operation`.

```cpp
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
