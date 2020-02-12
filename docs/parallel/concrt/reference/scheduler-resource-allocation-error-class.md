---
title: scheduler_resource_allocation_error, classe
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 2955320b443fb61f26d9f07ca336a45c620e2aa9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143335"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error, classe

Cette classe décrit une exception levée en raison d'un échec d'acquisition d'une ressource critique dans le runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Surchargé. Construit un objet `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_error_code](#get_error_code)|Retourne le code d’erreur qui a provoqué l’exception.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée lorsqu’un appel au système d’exploitation à partir de l’runtime d’accès concurrentiel échoue. Code d’erreur qui serait normalement retourné à partir d’un appel à la méthode Win32 `GetLastError` est converti en une valeur de type `HRESULT` et peut être récupéré à l’aide de la méthode `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="get_error_code"></a>get_error_code

Retourne le code d’erreur qui a provoqué l’exception.

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valeur de retour

`HRESULT` valeur de l’erreur qui a provoqué l’exception.

## <a name="ctor"></a>scheduler_resource_allocation_error

Construit un objet `scheduler_resource_allocation_error`.

```cpp
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

*_Hresult*<br/>
`HRESULT` valeur de l’erreur qui a provoqué l’exception.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
