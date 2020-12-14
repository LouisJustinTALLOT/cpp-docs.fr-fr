---
description: 'En savoir plus sur : classe unsupported_os'
title: unsupported_os, classe
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 1f9ee74db42d2b34c1b4e24a1951d84a442224bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188090"
---
# <a name="unsupported_os-class"></a>unsupported_os, classe

Cette classe décrit une exception levée quand un système d'exploitation non pris en charge est utilisé.

## <a name="syntax"></a>Syntaxe

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[unsupported_os](#ctor)|Surchargé. Construit un objet `unsupported_os`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`unsupported_os`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="unsupported_os"></a><a name="ctor"></a> unsupported_os

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

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
