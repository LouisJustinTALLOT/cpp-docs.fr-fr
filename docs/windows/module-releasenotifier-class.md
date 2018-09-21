---
title: Module::releasenotifier, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c9af03549eec7b62cc34aec2840764c54d2a21e
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494359"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                                | Description
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module::ReleaseNotifier :: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Annule l’initialisation de l’instance actuelle de la `Module::ReleaseNotifier` classe.
[Module::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module::ReleaseNotifier :: Invoke](#releasenotifier-invoke)   | En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Supprime l’actuel `Module::ReleaseNotifier` si l’objet a été construit avec un paramètre de l’objet `true`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module::ReleaseNotifier :: ~ ReleaseNotifier

Annule l’initialisation de l’instance actuelle de la `Module::ReleaseNotifier` classe.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module::ReleaseNotifier :: Invoke

En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

Supprime l’actuel `Module::ReleaseNotifier` si l’objet a été construit avec un paramètre de l’objet `true`.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::ReleaseNotifier::ReleaseNotifier

Initialise une nouvelle instance de la classe `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Paramètres

*release*  
`true` Pour supprimer cette instance lorsque la `Release` méthode est appelée ; `false` de ne pas supprimer cette instance.
