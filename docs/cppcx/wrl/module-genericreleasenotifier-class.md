---
description: 'En savoir plus sur : module :: GenericReleaseNotifier, classe'
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
ms.openlocfilehash: dd82da7c1b6b9a77c68b6d451bfa6dac31f51180
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186374"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par sur un lambda, un functor ou un pointeur vers une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type du membre de données qui contient l’emplacement du gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                     | Description
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module :: GenericReleaseNotifier :: GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                     | Description
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module :: GenericReleaseNotifier :: Invoke](#genericreleasenotifier-invoke) | Appelle le gestionnaire d’événements associé à l' `Module::GenericReleaseNotifier` objet en cours.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                                                          | Description
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module :: GenericReleaseNotifier :: callback_](#genericreleasenotifier-callback) | Contient le gestionnaire d’événements lambda, functor ou pointeur vers une fonction associé à l’objet actuel `Module::GenericReleaseNotifier` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a> Module :: GenericReleaseNotifier :: callback_

Contient le gestionnaire d’événements lambda, functor ou pointeur vers une fonction associé à l’objet actuel `Module::GenericReleaseNotifier` .

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a> Module :: GenericReleaseNotifier :: GenericReleaseNotifier

Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Paramètres

*rappel*<br/>
Un gestionnaire d’événements lambda, functor ou pointeur vers fonction qui peut être appelé avec l’opérateur de fonction de parenthèses ( `()` ).

*3/05*<br/>
Spécifiez **`true`** pour activer l’appel de la méthode [module :: ReleaseNotifier :: Release ()](module-releasenotifier-class.md#releasenotifier-release) sous-jacent ; sinon, spécifiez **`false`** .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a> Module :: GenericReleaseNotifier :: Invoke

Appelle le gestionnaire d’événements associé à l' `Module::GenericReleaseNotifier` objet en cours.

```cpp
void Invoke();
```
