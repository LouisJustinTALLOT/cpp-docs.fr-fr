---
title: Module::MethodReleaseNotifier, classe
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 41b7cfb2601cd2023e895dbcf1a56e85fe65b35d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336161"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par un objet et son membre pointeur-à la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de l’objet dont la fonction membre est le Gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                 | Description
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Initialise une nouvelle instance de la classe `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                   | Description
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier :: Invoke](#methodreleasenotifier-invoke) | Appelle le Gestionnaire d’événements associé actuel `Module::MethodReleaseNotifier` objet.

### <a name="protected-data-members"></a>Membres de données protégés

Name                                                                    | Description
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Contient un pointeur vers le Gestionnaire d’événements actuel `Module::MethodReleaseNotifier` objet.
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Contient un pointeur vers l’objet dont la fonction membre est le Gestionnaire d’événements actuel `Module::MethodReleaseNotifier` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier :: Invoke

Appelle le Gestionnaire d’événements associé actuel `Module::MethodReleaseNotifier` objet.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

Contient un pointeur vers le Gestionnaire d’événements actuel `Module::MethodReleaseNotifier` objet.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

Initialise une nouvelle instance de la classe `Module::MethodReleaseNotifier`.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Paramètres

*object*<br/>
Objet dont la fonction membre est un gestionnaire d’événements.

*method*<br/>
La fonction membre de paramètre *objet* qui est le Gestionnaire d’événements.

*release*<br/>
Spécifiez `true` pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) méthode ; sinon, spécifiez `false`.

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

Contient un pointeur vers l’objet dont la fonction membre est le Gestionnaire d’événements actuel `Module::MethodReleaseNotifier` objet.

```cpp
T* object_;
```
