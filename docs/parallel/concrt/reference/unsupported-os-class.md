---
title: unsupported_os, classe
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 253cd76182e1b6f85be3701663bd10c86c10e6ba
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142341"
---
# <a name="unsupported_os-class"></a>unsupported_os, classe

Cette classe décrit une exception levée quand un système d'exploitation non pris en charge est utilisé.

## <a name="syntax"></a>Syntaxe

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[unsupported_os](#ctor)|Surchargé. Construit un objet `unsupported_os`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`unsupported_os`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>unsupported_os

Construit un objet `unsupported_os`.

### <a name="syntax"></a>Syntaxe

```cpp
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
