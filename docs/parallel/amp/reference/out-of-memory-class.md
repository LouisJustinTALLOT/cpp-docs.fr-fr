---
title: out_of_memory (classe)
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336805"
---
# <a name="out_of_memory-class"></a>out_of_memory (classe)

L’exception qui est jetée quand une méthode échoue en raison d’un manque de mémoire du système ou de l’appareil.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[out_of_memory Constructeur](#ctor)|Initialise une nouvelle instance de la classe `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Spécifications

**En-tête:** amprt.h

**Espace de noms :** Concurrency

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

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

### <a name="return-value"></a>Valeur de retour

Nouvelle instance de la classe `out_of_memory`.

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
