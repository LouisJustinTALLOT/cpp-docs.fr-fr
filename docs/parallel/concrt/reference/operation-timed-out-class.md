---
description: 'En savoir plus sur : classe operation_timed_out'
title: operation_timed_out, classe
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 476dfc2d7f29b2769c076ff525f3d0eb1e20a8f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236553"
---
# <a name="operation_timed_out-class"></a>operation_timed_out, classe

Cette classe décrit une exception levée quand une opération a expiré.

## <a name="syntax"></a>Syntaxe

```cpp
class operation_timed_out : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[operation_timed_out](#ctor)|Surchargé. Construit un objet `operation_timed_out`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`operation_timed_out`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="operation_timed_out"></a><a name="ctor"></a> operation_timed_out

Construit un objet `operation_timed_out`.

```cpp
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
