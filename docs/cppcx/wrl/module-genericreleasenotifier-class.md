---
title: Module::GenericReleaseNotifier, classe
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371308"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier, classe

Invoque un gestionnaire d’événements lorsque le dernier objet du module actuel est libéré. Le gestionnaire d’événements est spécifié par sur un lambda, functor, ou pointeur-à-fonction.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de membre de données qui contient l’emplacement du gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                     | Description
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                     | Description
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::Invoke](#genericreleasenotifier-invoke) | Appelle le gestionnaire d’événements associé à l’objet actuel. `Module::GenericReleaseNotifier`

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                                                          | Description
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Tient le lambda, le functor ou le gestionnaire d’événements pointeur-à-fonction associé à l’objet actuel. `Module::GenericReleaseNotifier`

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Module::GenericReleaseNotifier::callback_

Tient le lambda, le functor ou le gestionnaire d’événements pointeur-à-fonction associé à l’objet actuel. `Module::GenericReleaseNotifier`

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier

Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Paramètres

*rappel*<br/>
Un gestionnaire d’événements lambda, functor ou pointeur à fonction qui peut être`()`invoqué avec l’opérateur de fonction parenthèses ( ).

*Libération*<br/>
Spécifier pour activer l’appel du [module sous-jacent:ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) `true` méthode; autrement, `false`spécifier .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier::Invoke

Appelle le gestionnaire d’événements associé à l’objet actuel. `Module::GenericReleaseNotifier`

```cpp
void Invoke();
```
