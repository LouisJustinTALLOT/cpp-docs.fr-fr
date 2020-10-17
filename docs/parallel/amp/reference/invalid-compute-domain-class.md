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
ms.openlocfilehash: 09418991e805e494c1d79ef31980bbec66a2e172
ms.sourcegitcommit: ced5ff1431ffbd25b20d106901955532723bd188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92135565"
---
# <a name="invalid_compute_domain-class"></a>invalid_compute_domain (classe)

Exception levée lorsque le runtime ne peut pas démarrer un noyau à l’aide du domaine de calcul spécifié sur le site d’appel [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) .

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur invalid_compute_domain](#ctor)|Initialise une nouvelle instance de la classe `invalid_compute_domain`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Conditions requises

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="invalid_compute_domain"></a><a name="ctor"></a> invalid_compute_domain

Initialise une nouvelle instance de la classe.

### <a name="syntax"></a>Syntaxe

```cpp
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l’erreur.

### <a name="return-value"></a>Valeur renvoyée

Une instance de la `invalid_compute_domain` classe

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
