---
title: API WRL principales par catégorie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: 8ac89f3286866ac61bac5ae256bdb448fe88f07d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213822"
---
# <a name="key-wrl-apis-by-category"></a>API WRL principales par catégorie

Les tableaux suivants répertorient les C++ principales classes, structures, fonctions et macros de la bibliothèque de modèles Windows Runtime. Les constructions dans les espaces de noms et les classes d’assistance sont omises. Ces listes augmentent la documentation de l’API, qui est organisée par espace de noms.

## <a name="classes"></a>Classes

|Intitulé|Description|
|-----------|-----------------|
|[ActivationFactory, classe](activationfactory-class.md)|Permet à une ou plusieurs classes d'être activées par le Windows Runtime.|
|[AsyncBase, classe](asyncbase-class.md)|Implémente la machine d'état asynchrone du Windows Runtime.|
|[ClassFactory, classe](classfactory-class.md)|Implémente les fonctionnalités de base de l'interface `IClassFactory`.|
|[ComPtr, classe](comptr-class.md)|Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. ComPtr met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface quand le décompte de références atteint zéro.|
|[Event, classe (bibliothèque de modèles Windows Runtime C++)](event-class-wrl.md)|Représente un événement.|
|[EventSource Class](eventsource-class.md)|Représente un événement. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements.|
|[FtmBase, classe](ftmbase-class.md)|Représente un objet marshaler libre de threads.|
|[HandleT, classe](handlet-class.md)|Représente un handle vers un objet.|
|[HString, classe](hstring-class.md)|Prend en charge la manipulation des handles HSTRING.|
|[HStringReference, classe](hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Module, classe](module-class.md)|Représente une collection d’objets connexes.|
|[Module::GenericReleaseNotifier, classe](module-genericreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par sur un lambda, un functor ou un pointeur vers une fonction.|
|[Module::MethodReleaseNotifier, classe](module-methodreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par un objet et son membre pointeur-à-a-Method.|
|[Module::ReleaseNotifier, classe](module-releasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.|
|[RoInitializeWrapper, classe](roinitializewrapper-class.md)|Initialise le Windows Runtime.|
|[RuntimeClass, classe](runtimeclass-class.md)|Représente une classe instanciée qui hérite du nombre spécifié d'interfaces et fournit le Windows Runtime spécifié, le COM classique et la prise en charge de références faibles.|
|[SimpleActivationFactory, classe](simpleactivationfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.|
|[SimpleClassFactory, classe](simpleclassfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base.|
|[WeakRef, classe](weakref-class.md)|Représente une *référence faible* qui peut être utilisée uniquement par le Windows Runtime, pas par le COM classique. Une référence faible représente un objet qui peut être accessible ou non.|

## <a name="structures"></a>Structures

|Intitulé|Description|
|-----------|-----------------|
|[ChainInterfaces, structure](chaininterfaces-structure.md)|Spécifie les fonctions de vérification et d'initialisation pouvant être appliquées à un ensemble d'ID d'interface.|
|[CloakedIid, structure](cloakediid-structure.md)|Indique aux modèles `RuntimeClass`, `Implements` et `ChainInterfaces` que l’interface spécifiée n’est pas accessible dans la liste IID.|
|[Implements, structure](implements-structure.md)|Implémente `QueryInterface` et `GetIid` pour les interfaces spécifiées.|
|[MixIn, structure](mixin-structure.md)|Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.|

## <a name="functions"></a>Fonctions

|Intitulé|Description|
|-----------|-----------------|
|[ActivateInstance, fonction](activateinstance-function.md)|Inscrit et récupère une instance d’un type spécifié défini dans un ID de classe spécifié.|
|[AsWeak, fonction](asweak-function.md)|Récupère une référence faible à une instance spécifiée.|
|[Fonction de rappel](callback-function-wrl.md)|Crée un objet dont la fonction membre est une méthode de rappel.|
|[CreateActivationFactory, fonction](createactivationfactory-function.md)|Crée une fabrique qui produit des instances de la classe spécifiée pouvant être activées par le Windows Runtime.|
|[CreateClassFactory, fonction](createclassfactory-function.md)|Crée une fabrique produisant des instances de la classe spécifiée.|
|[GetActivationFactory, fonction](getactivationfactory-function.md)|Récupère une fabrique d’activation pour le type spécifié par le paramètre de modèle.|
|[Make, fonction](make-function.md)|Initialise la classe de Windows Runtime spécifiée.|

## <a name="macros"></a>Macros

|Intitulé|Description|
|-----------|-----------------|
|[ActivatableClass, macros](activatableclass-macros.md)|Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée.|
|[InspectableClass, macro](inspectableclass-macro.md)|Définit le nom de la classe d’exécution et le niveau de confiance.|

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)
