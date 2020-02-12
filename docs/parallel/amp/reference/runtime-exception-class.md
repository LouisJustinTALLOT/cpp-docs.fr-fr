---
title: runtime_exception (classe)
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: 6ad784720833d2ae5de7d653d132ba144aec2677
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126374"
---
# <a name="runtime_exception-class"></a>runtime_exception (classe)

Type de base pour les exceptions dans C++ la bibliothèque amp (Accelerated massive parallelism).

### <a name="syntax"></a>Syntaxe

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur runtime_exception](#ctor)|Initialise une nouvelle instance de la classe `runtime_exception`.|
|[Destructeur ~ runtime_exception](#dtor)|Détruit l’objet `runtime_exception`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_error_code](#get_error_code)|Retourne le code d’erreur qui a provoqué l’exception.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Copie le contenu de l’objet `runtime_exception` spécifié dans celui-ci.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="ctor"></a>Constructeur runtime_exception

Initialise une nouvelle instance de la classe.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l’erreur qui a provoqué l’exception.

*_Hresult*<br/>
HRESULT de l’erreur qui a provoqué l’exception.

*_Other*<br/>
Objet `runtime_exception` à copier.

### <a name="return-value"></a>Valeur de retour

Objet `runtime_exception`.

## <a name="dtor"></a>Destructeur ~ runtime_exception

Détruit l'objet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a>get_error_code

Retourne le code d’erreur qui a provoqué l’exception.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT de l’erreur qui a provoqué l’exception.

## <a name="operator_eq"></a>  operator=
  Copie le contenu de l’objet `runtime_exception` spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `runtime_exception` à copier.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `runtime_exception`.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
