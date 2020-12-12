---
description: 'En savoir plus sur : module :: ReleaseNotifier, classe'
title: Module::ReleaseNotifier, classe
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: ebb4d949cbb1e7230894fa24a523e4d6b6cd2657
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186257"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                | Description
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module :: ReleaseNotifier :: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Désinitialise l’instance actuelle de la `Module::ReleaseNotifier` classe.
[Module :: ReleaseNotifier :: ReleaseNotifier](#releasenotifier-releasenotifier)        | Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module :: ReleaseNotifier :: Invoke](#releasenotifier-invoke)   | En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Supprime l’objet actuel `Module::ReleaseNotifier` si l’objet a été construit avec un paramètre de **`true`** .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a> Module :: ReleaseNotifier :: ~ ReleaseNotifier

Désinitialise l’instance actuelle de la `Module::ReleaseNotifier` classe.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a> Module :: ReleaseNotifier :: Invoke

En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a> Module :: ReleaseNotifier :: Release

Supprime l’objet actuel `Module::ReleaseNotifier` si l’objet a été construit avec un paramètre de **`true`** .

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a> Module :: ReleaseNotifier :: ReleaseNotifier

Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Paramètres

*3/05*<br/>
**`true`** pour supprimer cette instance lorsque la `Release` méthode est appelée ; **`false`** pour ne pas supprimer cette instance.
