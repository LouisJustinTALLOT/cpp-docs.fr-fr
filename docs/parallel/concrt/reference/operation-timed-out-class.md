---
title: operation_timed_out, classe
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 7a2513d30aa68798707f3bb16318db9b594b9e16
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138880"
---
# <a name="operation_timed_out-class"></a>operation_timed_out, classe

Cette classe décrit une exception levée quand une opération a expiré.

## <a name="syntax"></a>Syntaxe

```cpp
class operation_timed_out : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[operation_timed_out](#ctor)|Surchargé. Construit un objet `operation_timed_out`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`operation_timed_out`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>operation_timed_out

Construit un objet `operation_timed_out`.

```cpp
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
