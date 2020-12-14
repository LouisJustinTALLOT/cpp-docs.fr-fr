---
description: 'En savoir plus sur : classe scheduler_resource_allocation_error'
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
ms.openlocfilehash: 50f84cbf76d30a415e2393797baa7d6cfa1e89f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188727"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error, classe

Cette classe décrit une exception levée en raison d'un échec d'acquisition d'une ressource critique dans le runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Surchargé. Construit un objet `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_error_code](#get_error_code)|Retourne le code d’erreur qui a provoqué l’exception.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée lorsqu’un appel au système d’exploitation à partir de l’runtime d’accès concurrentiel échoue. Le code d’erreur qui serait normalement retourné à partir d’un appel à la méthode Win32 `GetLastError` est converti en une valeur de type `HRESULT` et peut être récupéré à l’aide de la `get_error_code` méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="get_error_code"></a><a name="get_error_code"></a> get_error_code

Retourne le code d’erreur qui a provoqué l’exception.

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

`HRESULT`Valeur de l’erreur qui a provoqué l’exception.

## <a name="scheduler_resource_allocation_error"></a><a name="ctor"></a> scheduler_resource_allocation_error

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
`HRESULT`Valeur de l’erreur qui a provoqué l’exception.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
