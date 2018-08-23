---
title: Module::methodreleasenotifier, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cee634ab62e699b4de6af54a57b0fe3d6b5e9a40
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606606"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier, classe

Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par un objet et son membre pointeur-à la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Paramètres

*T*  
Le type de l’objet dont la fonction membre est le Gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Module::MethodReleaseNotifier::MethodReleaseNotifier, constructeur](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Initialise une nouvelle instance de la **Module::MethodReleaseNotifier** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Module::MethodReleaseNotifier::Invoke, méthode](../windows/module-methodreleasenotifier-invoke-method.md)|Appelle le Gestionnaire d’événements associé actuel **Module::MethodReleaseNotifier** objet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[Module::MethodReleaseNotifier::method_, données de membre](../windows/module-methodreleasenotifier-method-data-member.md)|Contient un pointeur vers le Gestionnaire d’événements actuel **Module::MethodReleaseNotifier** objet.|
|[Module::MethodReleaseNotifier::object_, données de membre](../windows/module-methodreleasenotifier-object-data-member.md)|Contient un pointeur vers l’objet dont la fonction membre est le Gestionnaire d’événements actuel **Module::MethodReleaseNotifier** objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[Module, classe](../windows/module-class.md)