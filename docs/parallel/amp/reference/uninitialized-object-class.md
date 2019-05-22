---
title: uninitialized_object (classe)
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: a977957fcb28a7f4c6c849c954026e2bda4e728c
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975154"
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
|[uninitialized_object, constructeur](#uninitialized_object)|Initialise une nouvelle instance de la classe `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt.h

**Espace de noms :** Concurrence

## <a name="uninitialized_object"></a> uninitialized_object

Construit une nouvelle instance de la `uninitialized_object` exception.

### <a name="syntax"></a>Syntaxe

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l'erreur.

### <a name="return-value"></a>Valeur de retour

Le `uninitialized_object` objet exception.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
