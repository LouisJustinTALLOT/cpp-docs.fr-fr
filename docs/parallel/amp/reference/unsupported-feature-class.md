---
title: unsupported_feature, classe
ms.date: 11/04/2016
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 6a742c3fd1965882c3fa72cb1fab985cd4d981d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272540"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature, classe

Exception levée lorsqu’une fonctionnalité non prise en charge est utilisée.

## <a name="syntax"></a>Syntaxe

```
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[unsupported_feature, constructeur](#ctor)|Construit une nouvelle instance de la `unsupported_feature` exception.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature__ctor"></a> unsupported_feature

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

## <a name="requirements"></a>Spécifications

**En-tête :** amprt.h

**Espace de noms :** Concurrence

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
