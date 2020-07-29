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
ms.openlocfilehash: 5b0e5766fda878acb1fdc54a79ce162444eb06de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225720"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par un objet et son membre pointeur-à-a-Method.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de l’objet dont la fonction membre est le gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                 | Description
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module :: MethodReleaseNotifier :: MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Initialise une nouvelle instance de la classe `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                   | Description
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module :: MethodReleaseNotifier :: Invoke](#methodreleasenotifier-invoke) | Appelle le gestionnaire d’événements associé à l' `Module::MethodReleaseNotifier` objet en cours.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                                                    | Description
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module :: MethodReleaseNotifier :: method_](#methodreleasenotifier-method) | Contient un pointeur vers le gestionnaire d’événements pour l' `Module::MethodReleaseNotifier` objet actuel.
[Module :: MethodReleaseNotifier :: object_](#methodreleasenotifier-object) | Contient un pointeur vers l’objet dont la fonction membre est le gestionnaire d’événements pour l' `Module::MethodReleaseNotifier` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module :: MethodReleaseNotifier :: Invoke

Appelle le gestionnaire d’événements associé à l' `Module::MethodReleaseNotifier` objet en cours.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module :: MethodReleaseNotifier :: method_

Contient un pointeur vers le gestionnaire d’événements pour l' `Module::MethodReleaseNotifier` objet actuel.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module :: MethodReleaseNotifier :: MethodReleaseNotifier

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
Fonction membre de l' *objet* de paramètre qui est le gestionnaire d’événements.

*3/05*<br/>
Spécifiez **`true`** pour activer l’appel de la méthode [module :: ReleaseNotifier :: Release ()](module-releasenotifier-class.md#releasenotifier-release) sous-jacent ; sinon, spécifiez **`false`** .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module :: MethodReleaseNotifier :: object_

Contient un pointeur vers l’objet dont la fonction membre est le gestionnaire d’événements pour l' `Module::MethodReleaseNotifier` objet actuel.

```cpp
T* object_;
```
