---
description: 'En savoir plus sur : Microsoft :: WRL ::D espace de noms étails'
title: Microsoft::WRL::Details, espace de noms
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: c82d7389c80d35aa041dccc7c6bc8d202fba9c29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195110"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details, espace de noms

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[ComPtrRef, classe](comptrref-class.md)|Représente une référence à un objet de type ComPtr \<T> .|
|[ComPtrRefBase, classe](comptrrefbase-class.md)|Représente la classe de base pour la classe [ComPtrRef](comptrref-class.md) .|
|[DontUseNewUseMake, classe](dontusenewusemake-class.md)|Empêche l’utilisation `new` de l’opérateur dans `RuntimeClass` . Par conséquent, vous devez utiliser la [fonction Make](make-function.md) à la place.|
|[EventTargetArray, classe](eventtargetarray-class.md)|Représente un tableau de gestionnaires d’événements.|
|[MakeAllocator, classe](makeallocator-class.md)|Alloue de la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.|
|[ModuleBase, classe](modulebase-class.md)|Représente la classe de base des classes de [module](module-class.md) .|
|[Removeiunknown,, classe](removeiunknown-class.md)|Rend un type équivalent à un `IUnknown` type basé sur, mais qui a des `QueryInterface` méthodes, et non virtuelles `AddRef` `Release` .|
|[WeakReference, classe](weakreference-class.md)|Représente une *référence faible* qui peut être utilisée avec le Windows Runtime ou le com classique. Une référence faible représente un objet qui peut être accessible ou non.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[ArgTraits (structure)](argtraits-structure.md)|Déclare une interface de délégué spécifiée et une fonction membre anonyme qui a un nombre spécifié de paramètres.|
|[ArgTraitsHelper, structure](argtraitshelper-structure.md)|Permet de définir les caractéristiques communes des arguments de délégué.|
|[BoolStruct (structure)](boolstruct-structure.md)|Définit si un `ComPtr` gère la durée de vie des objets d’une interface. `BoolStruct` est utilisé en interne par l’opérateur [booltype, ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .|
|[CreatorMap, structure](creatormap-structure.md)|Contient des informations sur l’initialisation, l’inscription et l’annulation de l’inscription d’objets.|
|[DerefHelper (structure)](derefhelper-structure.md)|Représente un pointeur déréférencé vers le `T*` paramètre de modèle.|
|[EnableIf (structure)](enableif-structure.md)|Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la valeur **`true`** .|
|[FactoryCache (structure)](factorycache-structure.md)|Contient l’emplacement d’une fabrique de classe et d’une valeur qui identifie un Windows Runtime inscrit ou un objet de classe COM.|
|[ImplementsBase (structure)](implementsbase-structure.md)|Utilisé pour valider les types de paramètres de modèle dans la [structure Implements](implements-structure.md).|
|[ImplementsHelper (structure)](implementshelper-structure.md)|Aide à implémenter la structure [Implements](implements-structure.md) .|
|[InterfaceList, structure](interfacelist-structure.md)|Utilisé pour créer une liste récursive d’interfaces.|
|[InterfaceListHelper (structure)](interfacelisthelper-structure.md)|Génère un `InterfaceList` type en appliquant de manière récursive les arguments de paramètre de modèle spécifiés.|
|[InterfaceTraits, structure](interfacetraits-structure.md)|Implémente les caractéristiques communes d’une interface.|
|[InvokeHelper (structure)](invokehelper-structure.md)|Fournit une implémentation de la `Invoke()` méthode basée sur le nombre et le type d’arguments spécifiés.|
|[IsBaseOfStrict (structure)](isbaseofstrict-structure.md)|Teste si un type est la base d'un autre.|
|[IsSame (structure)](issame-structure.md)|Teste si un type spécifié est le même qu’un autre type spécifié.|
|[Nil, structure](nil-structure.md)|Utilisé pour indiquer un paramètre de modèle facultatif non spécifié.|
|[RemoveReference (structure)](removereference-structure.md)|Supprime la référence ou la caractéristique de référence rvalue du paramètre de modèle de classe spécifié.|
|[RuntimeClassBase, structure](runtimeclassbase-structure.md)|Utilisé pour détecter `RuntimeClass` dans la fonction [Make](make-function.md) .|
|[RuntimeClassBaseT, structure](runtimeclassbaset-structure.md)|Fournit des méthodes d’assistance pour les `QueryInterface` opérations et l’obtention des ID d’interface.|
|[VerifyInheritanceHelper (structure)](verifyinheritancehelper-structure.md)|Teste si une interface est dérivée d’une autre interface.|
|[VerifyInterfaceHelper (structure)](verifyinterfacehelper-structure.md)|Vérifie que l’interface spécifiée par le paramètre de modèle répond à certaines exigences.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[AsyncStatusInternal (énumération)](asyncstatusinternal-enumeration.md)|Spécifie un mappage entre les énumérations internes pour l’état des opérations asynchrones et l' `Windows::Foundation::AsyncStatus` énumération.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[Activationfactorycallback (fonction)](activationfactorycallback-function.md)|Obtient la fabrique d’activation pour l’ID d’activation spécifié.|
|[Move, fonction](move-function.md)|Déplace l’argument spécifié d’un emplacement à un autre.|
|[RaiseException fonction)](raiseexception-function.md)|Lève une exception dans le thread appelant.|
|[Swap, fonction (WRL)](swap-function-wrl.md)|Échange les valeurs des deux arguments spécifiés.|
|[Terminatemap, fonction)](terminatemap-function.md)|Arrête les fabriques de classes dans le module spécifié.|

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h, client. h, corewrappers. h, Event. h, FTM. h, Implements. h, Internal. h, module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Microsoft :: WRL :: wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)
