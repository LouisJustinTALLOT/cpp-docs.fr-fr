---
description: 'En savoir plus sur : classe bad_target'
title: bad_target, classe
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 0bade57ef06ee1ecf675d69531da918fc2a3510f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172243"
---
# <a name="bad_target-class"></a>bad_target, classe

Cette classe décrit une exception levée quand un bloc de messagerie reçoit un pointeur vers une cible qui n'est pas valide pour l'opération en cours.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[bad_target](#ctor)|Surchargé. Construit un objet `bad_target`.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée pour des raisons telles qu’une cible qui tente d’utiliser un message réservé pour une autre cible ou libérant une réservation qu’il ne contient pas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`bad_target`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="bad_target"></a><a name="ctor"></a> bad_target

Construit un objet `bad_target`.

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
