---
title: uninitialized_object (classe)
ms.date: 11/04/2016
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 1c431364aee0f1d1e75059abdb023ae52cf92155
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279327"
---
# <a name="uninitializedobject-class"></a>uninitialized_object (classe)

Exception levée lorsqu’un objet non initialisé est utilisé.

## <a name="syntax"></a>Syntaxe

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[uninitialized_object, constructeur](#ctor)|Initialise une nouvelle instance de la classe `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt.h

**Espace de noms :** Concurrence
## <a name="uninitialized_object__ctor"></a> unsupported_feature

Construit une nouvelle instance de l’exception unsupported_feature.

### <a name="syntax"></a>Syntaxe

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l'erreur.

### <a name="return-value"></a>Valeur de retour

Objet `unsupported_feature`.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
