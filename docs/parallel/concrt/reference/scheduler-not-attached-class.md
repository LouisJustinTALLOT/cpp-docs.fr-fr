---
description: 'En savoir plus sur : classe scheduler_not_attached'
title: scheduler_not_attached, classe
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: 1d412ffecea288d4ecad1d0c2949e7444adfd913
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188857"
---
# <a name="scheduler_not_attached-class"></a>scheduler_not_attached, classe

Cette classe décrit une exception levée quand une opération qui requiert l'attachement d'un planificateur au contexte actuel est effectuée alors qu'aucun planificateur n'est attaché.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|Surchargé. Construit un objet `scheduler_not_attached`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="scheduler_not_attached"></a><a name="ctor"></a> scheduler_not_attached

Construit un objet `scheduler_not_attached`.

```cpp
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
