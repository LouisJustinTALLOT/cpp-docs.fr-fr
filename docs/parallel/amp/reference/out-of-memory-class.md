---
description: 'En savoir plus sur : classe out_of_memory'
title: out_of_memory (classe)
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: bb7ba1db5be5921111b1fba2e12ea5cf6a5bea1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329921"
---
# <a name="out_of_memory-class"></a>out_of_memory (classe)

Exception levée en cas d’échec d’une méthode en raison d’un manque de mémoire système ou de périphérique.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur out_of_memory](#ctor)|Initialise une nouvelle instance de la classe `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="out_of_memory"></a><a name="ctor"></a> out_of_memory

Initialise une nouvelle instance de la classe.

### <a name="syntax"></a>Syntaxe

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l’erreur.

### <a name="return-value"></a>Valeur renvoyée

Nouvelle instance de la classe `out_of_memory`.

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
