---
title: invalid_compute_domain (classe)
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 264b93d11b82eb00ac85e92413ca1a7071e06879
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582245"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain (classe)

L’exception est levée lorsque le runtime ne peut pas démarrer un noyau à l’aide du domaine de calcul spécifié à la [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) site d’appel.

## <a name="syntax"></a>Syntaxe

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_compute_domain, constructeur](#ctor)|Initialise une nouvelle instance de la classe `invalid_compute_domain`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt.h

**Espace de noms :** Concurrency

## <a name="ctor"></a> invalid_compute_domain

Initialise une nouvelle instance de la classe.

## <a name="syntax"></a>Syntaxe

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l'erreur.

### <a name="return-value"></a>Valeur de retour

Une instance de la `invalid_compute_domain` classe

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
