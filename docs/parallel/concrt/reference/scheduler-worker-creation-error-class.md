---
description: 'En savoir plus sur : classe scheduler_worker_creation_error'
title: scheduler_worker_creation_error, classe
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: f0fbb0aed19738bb88e4cbfe3a72580627c4fca9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188714"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error, classe

Cette classe décrit une exception levée en raison d'un échec de création d'un contexte d'exécution de travail dans le runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Surchargé. Construit un objet `scheduler_worker_creation_error`.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée lorsqu’un appel au système d’exploitation pour créer des contextes d’exécution à partir de la runtime d’accès concurrentiel échoue. Les contextes d’exécution sont des threads qui exécutent des tâches dans l’runtime d’accès concurrentiel. Le code d’erreur qui serait normalement retourné à partir d’un appel à la méthode Win32 `GetLastError` est converti en une valeur de type `HRESULT` et peut être récupéré à l’aide de la méthode de la classe de base `get_error_code` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="scheduler_worker_creation_error"></a><a name="ctor"></a> scheduler_worker_creation_error

Construit un objet `scheduler_worker_creation_error`.

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

*_Hresult*<br/>
`HRESULT`Valeur de l’erreur qui a provoqué l’exception.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
