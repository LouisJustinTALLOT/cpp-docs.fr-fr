---
description: 'En savoir plus sur : classe invalid_link_target'
title: invalid_link_target, classe
ms.date: 11/04/2016
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
ms.openlocfilehash: d080886c3aab0ecc120d4ce13f5f75f2eecfea8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334585"
---
# <a name="invalid_link_target-class"></a>invalid_link_target, classe

Cette classe décrit une exception levée quand la méthode `link_target` d'un bloc de messagerie est appelée et que le bloc de messagerie ne parvient pas à établir un lien avec la cible. Cette situation peut être due à un dépassement du nombre de liens autorisé pour le bloc de messagerie ou à une tentative à deux reprises de liaison d'une cible spécifique à la même source.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_link_target : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_link_target](#ctor)|Surchargé. Construit un objet `invalid_link_target`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_link_target`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_link_target"></a><a name="ctor"></a> invalid_link_target

Construit un objet `invalid_link_target`.

```cpp
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md)
