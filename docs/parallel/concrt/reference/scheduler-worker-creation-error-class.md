---
title: scheduler_worker_creation_error, classe
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: 66e7485787606c22aba2970dbe481a7d29e66621
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268380"
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error, classe

Cette classe décrit une exception levée en raison d'un échec de création d'un contexte d'exécution de travail dans le runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Surchargé. Construit un objet `scheduler_worker_creation_error`.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée en cas d’échec d’un appel au système d’exploitation pour créer des contextes d’exécution à partir de dans le Runtime d’accès concurrentiel. Contextes d’exécution sont des threads qui exécutent des tâches dans le Runtime d’accès concurrentiel. Le code d’erreur qui serait normalement retourné à partir d’un appel à la méthode Win32 `GetLastError` est convertie en une valeur de type `HRESULT` et peuvent être récupérées à l’aide de la méthode de classe de base `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> scheduler_worker_creation_error

Construit un objet `scheduler_worker_creation_error`.

```
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
Le `HRESULT` la valeur de l’erreur qui a provoqué l’exception.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
