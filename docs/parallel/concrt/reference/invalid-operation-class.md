---
description: 'En savoir plus sur : classe invalid_operation'
title: invalid_operation, classe
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: f3050d487f2c374f66f264b6e568fce5244d25ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334542"
---
# <a name="invalid_operation-class"></a>invalid_operation, classe

Cette classe décrit une exception qui est levée quand une opération non valide qui n'est pas décrite de façon plus précise par un autre type d'exception levé par le runtime d'accès concurrentiel est exécutée.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_operation : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_operation](#ctor)|Surchargé. Construit un objet `invalid_operation`.|

## <a name="remarks"></a>Notes

Les différentes méthodes qui lèvent cette exception indiquent généralement dans quelles circonstances elles agissent ainsi.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_operation`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_operation"></a><a name="ctor"></a> invalid_operation

Construit un objet `invalid_operation`.

```cpp
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
