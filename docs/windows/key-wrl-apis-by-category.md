---
title: Clé API WRL par catégorie | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9936c85443f893111b3c2b9de17ca80e6fb382b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881456"
---
# <a name="key-wrl-apis-by-category"></a>API WRL principales par catégorie
Les tableaux suivants répertorient les principaux classes, structs, fonctions et macros de bibliothèque de modèles Windows Runtime C++. Constructions dans les classes et les espaces de noms d’assistance sont omises. Ces listes complètent la documentation de l’API, organisée par espace de noms.  
  
### <a name="classes"></a>Classes  
  
|Titre|Description|  
|-----------|-----------------|  
|[ActivationFactory, classe](../windows/activationfactory-class.md)|Permet à une ou plusieurs classes d'être activées par le Windows Runtime.|  
|[AsyncBase, classe](../windows/asyncbase-class.md)|Implémente la machine d'état asynchrone du Windows Runtime.|  
|[ClassFactory, classe](../windows/classfactory-class.md)|Implémente les fonctionnalités de base de l'interface `IClassFactory`.|  
|[ComPtr, classe](../windows/comptr-class.md)|Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. ComPtr met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface quand le décompte de références atteint zéro.|  
|[Event, classe (bibliothèque de modèles Windows Runtime C++)](../windows/event-class-windows-runtime-cpp-template-library.md)|Représente un événement.|  
|[EventSource, classe](../windows/eventsource-class.md)|Représente un événement. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements.|  
|[FtmBase, classe](../windows/ftmbase-class.md)|Représente un objet marshaler libre de threads.|  
|[HandleT, classe](../windows/handlet-class.md)|Représente un handle d’un objet.|  
|[HString, classe](../windows/hstring-class.md)|Prend en charge pour la manipulation des descripteurs de HSTRING.|  
|[HStringReference, classe](../windows/hstringreference-class.md)|Représente un HSTRING est créé à partir d’une chaîne existante.|  
|[Module, classe](../windows/module-class.md)|Représente une collection d’objets connexes.|  
|[Module::GenericReleaseNotifier, classe](../windows/module-genericreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est libéré. Le Gestionnaire d’événements est spécifié par sur une expression lambda, functor ou pointeur de fonction.|  
|[Module::MethodReleaseNotifier, classe](../windows/module-methodreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est libéré. Le Gestionnaire d’événements est spécifié par un objet et son membre de pointeur de méthode.|  
|[Module::ReleaseNotifier, classe](../windows/module-releasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.|  
|[RoInitializeWrapper, classe](../windows/roinitializewrapper-class.md)|Initialise le Windows Runtime.|  
|[RuntimeClass, classe](../windows/runtimeclass-class.md)|Représente une classe instanciée qui hérite du nombre spécifié d'interfaces et fournit le Windows Runtime spécifié, le COM classique et la prise en charge de références faibles.|  
|[SimpleActivationFactory, classe](../windows/simpleactivationfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.|  
|[SimpleClassFactory, classe](../windows/simpleclassfactory-class.md)|Fournit un mécanisme fondamental pour créer une classe de base.|  
|[WeakRef, classe](../windows/weakref-class.md)|Représente une *référence faible* qui peut être utilisée uniquement par le Windows Runtime, pas par le COM classique. Une référence faible représente un objet qui peut être accessible ou non.|  
  
### <a name="structures"></a>Structures  
  
|Titre|Description|  
|-----------|-----------------|  
|[ChainInterfaces, structure](../windows/chaininterfaces-structure.md)|Spécifie les fonctions de vérification et d'initialisation pouvant être appliquées à un ensemble d'ID d'interface.|  
|[CloakedIid, structure](../windows/cloakediid-structure.md)|Indique à la `RuntimeClass`, `Implements` et `ChainInterfaces` modèles que l’interface spécifiée n’est pas accessible dans la liste des IID.|  
|[Implements, structure](../windows/implements-structure.md)|Implémente `QueryInterface` et `GetIid` pour les interfaces spécifiées.|  
|[MixIn, structure](../windows/mixin-structure.md)|Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.|  
  
### <a name="functions"></a>Fonctions  
  
|Titre|Description|  
|-----------|-----------------|  
|[ActivateInstance, fonction](../windows/activateinstance-function.md)|Enregistre et récupère une instance d’un type spécifié défini dans un ID de classe spécifiée.|  
|[AsWeak, fonction](../windows/asweak-function.md)|Récupère une référence faible à une instance spécifiée.|  
|[Fonction de rappel](../windows/callback-function-windows-runtime-cpp-template-library.md)|Crée un objet dont la fonction membre est une méthode de rappel.|  
|[CreateActivationFactory, fonction](../windows/createactivationfactory-function.md)|Crée une fabrique qui produit des instances de la classe spécifiée pouvant être activées par le Windows Runtime.|  
|[CreateClassFactory, fonction](../windows/createclassfactory-function.md)|Crée une fabrique produisant des instances de la classe spécifiée.|  
|[GetActivationFactory, fonction](../windows/getactivationfactory-function.md)|Récupère la fabrique d’activation pour le type spécifié par le paramètre de modèle.|  
|[Make, fonction](../windows/make-function.md)|Initialise la classe Windows Runtime spécifiée.|  
  
### <a name="macros"></a>Macros  
  
|Titre|Description|  
|-----------|-----------------|  
|[ActivatableClass, macros](../windows/activatableclass-macros.md)|Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée.|  
|[InspectableClass, macro](../windows/inspectableclass-macro.md)|Définit le niveau de confiance et de nom de la classe runtime.|  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)