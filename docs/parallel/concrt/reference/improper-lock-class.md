---
description: 'En savoir plus sur : classe improper_lock'
title: improper_lock, classe
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 8e29172ad171bbd3f95b3079840fb50b91dfe577
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334633"
---
# <a name="improper_lock-class"></a>improper_lock, classe

Cette classe décrit une exception levée quand un verrou est incorrectement acquis.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[improper_lock](#ctor)|Surchargé. Construit un objet `improper_lock exception`.|

## <a name="remarks"></a>Notes

En général, cette exception est levée lorsqu’une tentative est faite pour acquérir un verrou non réentrant de manière récursive sur le même contexte.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`improper_lock`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="improper_lock"></a><a name="ctor"></a> improper_lock

Construit un objet `improper_lock exception`.

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe critical_section](critical-section-class.md)<br/>
[Classe reader_writer_lock](reader-writer-lock-class.md)
