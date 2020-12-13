---
description: 'En savoir plus sur : classe improper_scheduler_attach'
title: improper_scheduler_attach, classe
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 755cd72d20eb88dbd1ff7c58586f0aaf3b964a6a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334632"
---
# <a name="improper_scheduler_attach-class"></a>improper_scheduler_attach, classe

Cette classe décrit une exception levée quand la méthode `Attach` est appelée sur un objet `Scheduler` qui est déjà attaché au contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|Surchargé. Construit un objet `improper_scheduler_attach`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="improper_scheduler_attach"></a><a name="ctor"></a> improper_scheduler_attach

Construit un objet `improper_scheduler_attach`.

```cpp
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
