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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371289"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier, classe

Invoque un gestionnaire d’événements lorsque le dernier objet du module actuel est libéré. Le gestionnaire d’événements est spécifié par un objet et son membre pointeur à une méthode.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet dont la fonction de membre est le gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                                 | Description
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Initialise une nouvelle instance de la classe `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                   | Description
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Appelle le gestionnaire d’événements associé à l’objet actuel. `Module::MethodReleaseNotifier`

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                                                    | Description
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Tient un pointeur au gestionnaire `Module::MethodReleaseNotifier` d’événements pour l’objet actuel.
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Tient un pointeur à l’objet dont la `Module::MethodReleaseNotifier` fonction de membre est le gestionnaire d’événement pour l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Spécifications

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier::Invoke

Appelle le gestionnaire d’événements associé à l’objet actuel. `Module::MethodReleaseNotifier`

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

Tient un pointeur au gestionnaire `Module::MethodReleaseNotifier` d’événements pour l’objet actuel.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

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

*Objet*<br/>
Un objet dont la fonction de membre est un gestionnaire d’événements.

*Méthode*<br/>
Fonction membre de *l’objet* de paramètre qui est le gestionnaire d’événement.

*Libération*<br/>
Spécifier pour activer l’appel du [module sous-jacent:ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) `true` méthode; autrement, `false`spécifier .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

Tient un pointeur à l’objet dont la `Module::MethodReleaseNotifier` fonction de membre est le gestionnaire d’événement pour l’objet actuel.

```cpp
T* object_;
```
