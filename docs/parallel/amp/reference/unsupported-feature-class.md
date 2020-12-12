---
description: 'En savoir plus sur : classe unsupported_feature'
title: unsupported_feature, classe
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 22cbc193de2a42e76ead4097d1e39351693ef706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314501"
---
# <a name="unsupported_feature-class"></a>unsupported_feature, classe

Exception levée lorsqu’une fonctionnalité non prise en charge est utilisée.

## <a name="syntax"></a>Syntaxe

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur unsupported_feature](#unsupported_feature)|Construit une nouvelle instance de l' `unsupported_feature` exception.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a><a name="unsupported_feature"></a> unsupported_feature

  Construit une nouvelle instance de l' `unsupported_feature` exception.

### <a name="syntax"></a>Syntaxe

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Description de l’erreur.

### <a name="return-value"></a>Valeur renvoyée

Objet `unsupported_feature`.

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
