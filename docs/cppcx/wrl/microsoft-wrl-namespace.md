---
description: 'En savoir plus sur : Microsoft :: WRL, espace de noms'
title: Microsoft::WRL, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: fdf7f0fbdca5cd5d95772052dd5dfb5018cabb18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335537"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL, espace de noms

Définit les types fondamentaux qui composent la bibliothèque de modèles C++ Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[ActivationFactory, classe](activationfactory-class.md)|Permet à une ou plusieurs classes d'être activées par le Windows Runtime.|
|[AsyncBase, classe](asyncbase-class.md)|Implémente la machine d'état asynchrone du Windows Runtime.|
|[ClassFactory, classe](classfactory-class.md)|Implémente les fonctionnalités de base de l'interface `IClassFactory`.|
|[ComPtr, classe](comptr-class.md)|Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. ComPtr met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface quand le décompte de références atteint zéro.|
|[DeferrableEventArgs, classe](deferrableeventargs-class.md)|Classe de modèle utilisée pour les types d'arguments des événements différés.|
|[EventSource Class](eventsource-class.md)|Représente un événement. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements.|
|[FtmBase, classe](ftmbase-class.md)|Représente un objet marshaler libre de threads.|
|[Module, classe](module-class.md)|Représente une collection d’objets connexes.|
|[RuntimeClass, classe](runtimeclass-class.md)|Représente une classe instanciée qui hérite du nombre spécifié d'interfaces et fournit le Windows Runtime spécifié, le COM classique et la prise en charge de références faibles.|
|[SimpleActivationFactory, classe](simpleactivationfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.|
|[SimpleClassFactory, classe](simpleclassfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base.|
|[WeakRef, classe](weakref-class.md)|Représente une *référence faible* qui peut être utilisée uniquement par le Windows Runtime, pas par le COM classique. Une référence faible représente un objet qui peut être accessible ou non.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[ChainInterfaces (structure)](chaininterfaces-structure.md)|Spécifie les fonctions de vérification et d'initialisation pouvant être appliquées à un ensemble d'ID d'interface.|
|[CloakedIid, structure](cloakediid-structure.md)|Indique aux `RuntimeClass` modèles, `Implements` et `ChainInterfaces` que l’interface spécifiée n’est pas accessible dans la liste iid.|
|[Implements (structure)](implements-structure.md)|Implémente `QueryInterface` et `GetIid` pour les interfaces spécifiées.|
|[MixIn, structure](mixin-structure.md)|Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.|
|[RuntimeClassFlags (structure)](runtimeclassflags-structure.md)|Contient le type d’une instance d’un [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[AsyncResultType (énumération)](asyncresulttype-enumeration.md)|Spécifie le type de résultat retourné par la `GetResults()` méthode.|
|[ModuleType (énumération)](moduletype-enumeration.md)|Spécifie si un module doit prendre en charge un serveur in-process ou un serveur out-of-process.|
|[RuntimeClassType (énumération)](runtimeclasstype-enumeration.md)|Spécifie le type d’instance [RuntimeClass](runtimeclass-class.md) qui est pris en charge.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[Asweak, fonction)](asweak-function.md)|Récupère une référence faible à une instance spécifiée.|
|[Fonction de rappel (WRL)](callback-function-wrl.md)|Crée un objet dont la fonction membre est une méthode de rappel.|
|[Createactivationfactory, fonction)](createactivationfactory-function.md)|Crée une fabrique qui produit des instances de la classe spécifiée pouvant être activées par le Windows Runtime.|
|[Createclassfactory, fonction)](createclassfactory-function.md)|Crée une fabrique produisant des instances de la classe spécifiée.|
|[Make, fonction](make-function.md)|Initialise la classe de Windows Runtime spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h, client. h, corewrappers. h, Event. h, FTM. h, Implements. h, Internal. h, module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL :: wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)
