---
title: Module::genericreleasenotifier, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18aeac7767fbd4c1688b202670a812e5738ef62f
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494424"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par dans une expression lambda, functor ou pointeur de fonction.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type du membre de données qui contient l’emplacement du Gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                     | Description
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                     | Description
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier :: Invoke](#genericreleasenotifier-invoke) | Appelle le Gestionnaire d’événements associé actuel `Module::GenericReleaseNotifier` objet.

### <a name="protected-data-members"></a>Membres de données protégés

Name                                                                          | Description
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Contient l’expression lambda, functor ou gestionnaire d’événements de pointeur de fonction associé actuel `Module::GenericReleaseNotifier` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Module::GenericReleaseNotifier::callback_

Contient l’expression lambda, functor ou gestionnaire d’événements de pointeur de fonction associé actuel `Module::GenericReleaseNotifier` objet.

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier

Initialise une nouvelle instance de la classe `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Paramètres

*rappel*  
Une expression lambda, functor ou gestionnaire d’événements de pointeur de fonction qui peut être appelé avec l’opérateur de fonction entre parenthèses (`()`).

*release*  
Spécifiez `true` pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) méthode ; sinon, spécifiez `false`.

## <a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier :: Invoke

Appelle le Gestionnaire d’événements associé actuel `Module::GenericReleaseNotifier` objet.

```cpp
void Invoke();
```
