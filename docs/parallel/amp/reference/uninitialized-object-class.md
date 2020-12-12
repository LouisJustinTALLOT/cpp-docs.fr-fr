---
description: 'En savoir plus sur : classe uninitialized_object'
title: uninitialized_object (classe)
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 4929de9e865492c9fb468f5fac336f67fb307efb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326388"
---
# <a name="uninitialized_object-class"></a>uninitialized_object (classe)

Exception levée lorsqu’un objet non initialisé est utilisé.

## <a name="syntax"></a>Syntaxe

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur uninitialized_object](#uninitialized_object)|Initialise une nouvelle instance de la classe `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="uninitialized_object"></a><a name="uninitialized_object"></a> uninitialized_object

Construit une nouvelle instance de l' `uninitialized_object` exception.

### <a name="syntax"></a>Syntaxe

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l’erreur.

### <a name="return-value"></a>Valeur renvoyée

`uninitialized_object`Objet exception.

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
