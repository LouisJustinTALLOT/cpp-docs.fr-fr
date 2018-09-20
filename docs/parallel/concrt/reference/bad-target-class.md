---
title: bad_target, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b13aecabbf7f9935671b6bd44b654e78c5cd58dd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395074"
---
# <a name="badtarget-class"></a>bad_target, classe

Cette classe décrit une exception levée quand un bloc de messagerie reçoit un pointeur vers une cible qui n'est pas valide pour l'opération en cours.

## <a name="syntax"></a>Syntaxe

```
class bad_target : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[bad_target](#ctor)|Surchargé. Construit un objet `bad_target`.|

## <a name="remarks"></a>Notes

Cette exception est généralement levée pour des raisons telles que d’une cible essayant de consommer un message qui est réservé à une autre cible ou la libération d’une réservation qu’il ne contient pas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`bad_target`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> bad_target

Construit un objet `bad_target`.

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)

