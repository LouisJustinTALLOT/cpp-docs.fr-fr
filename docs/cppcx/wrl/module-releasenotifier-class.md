---
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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418285"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Name                                                                                | Description
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module :: ReleaseNotifier :: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Déinitialise l’instance actuelle de la classe `Module::ReleaseNotifier`.
[Module :: ReleaseNotifier :: ReleaseNotifier](#releasenotifier-releasenotifier)        | Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Name                                                         | Description
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module :: ReleaseNotifier :: Invoke](#releasenotifier-invoke)   | En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Supprime l’objet `Module::ReleaseNotifier` actuel si l’objet a été construit avec un paramètre ayant la **valeur true**.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`ReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module :: ReleaseNotifier :: ~ ReleaseNotifier

Déinitialise l’instance actuelle de la classe `Module::ReleaseNotifier`.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module :: ReleaseNotifier :: Invoke

En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module :: ReleaseNotifier :: Release

Supprime l’objet `Module::ReleaseNotifier` actuel si l’objet a été construit avec un paramètre ayant la **valeur true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module :: ReleaseNotifier :: ReleaseNotifier

Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Paramètres

*release*<br/>
`true` de supprimer cette instance lorsque la méthode `Release` est appelée ; `false` de ne pas supprimer cette instance.
