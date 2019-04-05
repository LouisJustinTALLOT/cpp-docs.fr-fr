---
title: Microsoft::WRL::Details, espace de noms
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: fce6e620600164e73d3708d98d8a7fa979e8ab42
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027472"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details, espace de noms

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[ComPtrRef (classe)](comptrref-class.md)|Représente une référence à un objet de type ComPtr\<T >.|
|[ComPtrRefBase (classe)](comptrrefbase-class.md)|Représente la classe de base pour le [ComPtrRef](comptrref-class.md) classe.|
|[DontUseNewUseMake (classe)](dontusenewusemake-class.md)|Empêche l’utilisation d’opérateur `new` dans `RuntimeClass`. Par conséquent, vous devez utiliser le [Make, fonction](make-function.md) à la place.|
|[EventTargetArray, classe](eventtargetarray-class.md)|Représente un tableau des gestionnaires d’événements.|
|[MakeAllocator (classe)](makeallocator-class.md)|Alloue la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.|
|[ModuleBase, classe](modulebase-class.md)|Représente la classe de base de la [Module](module-class.md) classes.|
|[RemoveIUnknown, classe](removeiunknown-class.md)|Crée un type qui est équivalent à une `IUnknown`-type de base, a, mais non virtuelle `QueryInterface`, `AddRef`, et `Release` méthodes.|
|[WeakReference, classe](weakreference-class.md)|Représente un *référence faible* qui peut être utilisé avec le Windows Runtime ou le COM classique. Une référence faible représente un objet qui peut être accessible ou non.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[ArgTraits (structure)](argtraits-structure.md)|Déclare un délégué spécifié interface et une fonction membre anonyme qui a un nombre spécifié de paramètres.|
|[ArgTraitsHelper (structure)](argtraitshelper-structure.md)|Permet de définir les caractéristiques communes d’arguments du délégué.|
|[BoolStruct (structure)](boolstruct-structure.md)|Définit si un `ComPtr` gère la durée de vie d’une interface. `BoolStruct` est utilisé en interne par le [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) opérateur.|
|[CreatorMap (structure)](creatormap-structure.md)|Contient des informations sur la façon d’initialiser, inscrire et annuler l’inscription d’objets.|
|[DerefHelper (structure)](derefhelper-structure.md)|Représenter un pointeur déréférencé au `T*` paramètre de modèle.|
|[EnableIf (structure)](enableif-structure.md)|Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la valeur `true`.|
|[FactoryCache (structure)](factorycache-structure.md)|Contient l’emplacement d’une fabrique de classe et une valeur qui identifie un objet de classe Windows Runtime ou COM inscrit.|
|[ImplementsBase (structure)](implementsbase-structure.md)|Permet de valider les types de paramètre de modèle dans [Implements (Structure)](implements-structure.md).|
|[ImplementsHelper (structure)](implementshelper-structure.md)|Permet d’implémenter le [implémente](implements-structure.md) structure.|
|[InterfaceList (structure)](interfacelist-structure.md)|Utilisé pour créer une liste récursive des interfaces.|
|[InterfaceListHelper (structure)](interfacelisthelper-structure.md)|Génère un `InterfaceList` type en appliquant les arguments de paramètre de modèle spécifié de manière récursive.|
|[InterfaceTraits (structure)](interfacetraits-structure.md)|Caractéristiques communes d’implémente d’une interface.|
|[InvokeHelper (structure)](invokehelper-structure.md)|Fournit une implémentation de la `Invoke()` méthode basée sur le nombre spécifié et le type d’arguments.|
|[IsBaseOfStrict (structure)](isbaseofstrict-structure.md)|Teste si un type est la base d'un autre.|
|[IsSame (structure)](issame-structure.md)|Teste si un spécifié le type est identique à un autre de type spécifié.|
|[Nil, structure](nil-structure.md)|Utilisé pour indiquer un paramètre de modèle non spécifié, facultatif.|
|[RemoveReference (structure)](removereference-structure.md)|Supprime la caractéristique de référence ou référence rvalue à partir du paramètre de modèle de classe spécifiée.|
|[RuntimeClassBase, structure](runtimeclassbase-structure.md)|Permet de détecter `RuntimeClass` dans le [rendre](make-function.md) (fonction).|
|[RuntimeClassBaseT, structure](runtimeclassbaset-structure.md)|Fournit des méthodes d’assistance pour `QueryInterface` opérations et l’obtention des ID d’interface.|
|[VerifyInheritanceHelper (structure)](verifyinheritancehelper-structure.md)|Teste si une interface est dérivée d’une autre interface.|
|[VerifyInterfaceHelper (structure)](verifyinterfacehelper-structure.md)|Vérifie que l’interface spécifiée par le paramètre de modèle répond à certaines exigences.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[AsyncStatusInternal (énumération)](asyncstatusinternal-enumeration.md)|Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la `Windows::Foundation::AsyncStatus` énumération.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[ActivationFactoryCallback (fonction)](activationfactorycallback-function.md)|Obtient la fabrique d’activation pour l’ID d’activation spécifié.|
|[Move (fonction)](move-function.md)|Déplace l’argument spécifié à partir d’un emplacement vers un autre.|
|[RaiseException (fonction)](raiseexception-function.md)|Lève une exception dans le thread appelant.|
|[Swap, fonction (WRL)](swap-function-wrl.md)|Échange les valeurs des deux arguments spécifiés.|
|[TerminateMap, fonction](terminatemap-function.md)|Arrête les fabriques de classe dans le module spécifié.|

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)