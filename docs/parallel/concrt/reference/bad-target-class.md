---
title: bad_target, classe
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142855"
---
# <a name="bad_target-class"></a>bad_target, classe

Cette classe décrit une exception levée quand un bloc de messagerie reçoit un pointeur vers une cible qui n'est pas valide pour l'opération en cours.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[bad_target](#ctor)|Surchargé. Construit un objet `bad_target`.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée pour des raisons telles qu’une cible qui tente d’utiliser un message réservé pour une autre cible ou libérant une réservation qu’il ne contient pas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`bad_target`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>bad_target

Construit un objet `bad_target`.

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
