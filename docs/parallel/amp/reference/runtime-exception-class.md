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
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336799"
---
# <a name="runtime_exception-class"></a>runtime_exception (classe)

Le type de base pour les exceptions dans la bibliothèque de parallélisme massif accéléré (AMP).

### <a name="syntax"></a>Syntaxe

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[runtime_exception Constructeur](#ctor)|Initialise une nouvelle instance de la classe `runtime_exception`.|
|[Destructeur runtime_exception](#dtor)|Détruit l’objet. `runtime_exception`|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_error_code](#get_error_code)|Retourne le code d’erreur qui a causé l’exception.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur](#operator_eq)|Copie le contenu `runtime_exception` de l’objet spécifié dans celui-ci.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

## <a name="requirements"></a>Spécifications

**En-tête:** amprt.h

**Espace de noms :** Concurrency

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>runtime_exception Constructeur

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
Une description de l’erreur qui a causé l’exception.

*_Hresult*<br/>
Le HRESULT de l’erreur qui a causé l’exception.

*_Other*<br/>
Objet `runtime_exception` à copier.

### <a name="return-value"></a>Valeur de retour

Objet `runtime_exception`.

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>Destructeur runtime_exception

Détruit l'objet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

Retourne le code d’erreur qui a causé l’exception.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le HRESULT de l’erreur qui a causé l’exception.

## <a name="operator"></a><a name="operator_eq"></a>opérateur

Copie le contenu `runtime_exception` de l’objet spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `runtime_exception` à copier.

### <a name="return-value"></a>Valeur de retour

Une référence `runtime_exception` à cet objet.

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
