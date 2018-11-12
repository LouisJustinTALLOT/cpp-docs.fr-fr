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
ms.openlocfilehash: d8b94a17c4d842e97901e97dd2197692252eed43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613159"
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error, classe

Cette classe décrit une exception levée en raison d'un échec d'acquisition d'une ressource critique dans le runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```
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

Cette exception est généralement levée en cas d’échec d’un appel vers le système d’exploitation dans le Runtime d’accès concurrentiel. Le code d’erreur qui serait normalement retourné à partir d’un appel à la méthode Win32 `GetLastError` est convertie en une valeur de type `HRESULT` et peuvent être récupérées à l’aide de la `get_error_code` (méthode).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="get_error_code"></a> get_error_code

Retourne le code d’erreur qui a provoqué l’exception.

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le `HRESULT` la valeur de l’erreur qui a provoqué l’exception.

##  <a name="ctor"></a> scheduler_resource_allocation_error

Construit un objet `scheduler_resource_allocation_error`.

```
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
Le `HRESULT` la valeur de l’erreur qui a provoqué l’exception.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
