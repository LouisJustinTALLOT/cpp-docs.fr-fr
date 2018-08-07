---
title: Microsoft::wrl::Details Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49256b556eddb1feadbfd01b298aba62ad1a51ee
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604224"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details, espace de noms
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL::Details;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="classes"></a>Classes  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtrRef, classe](../windows/comptrref-class.md)|Représente une référence à un objet de type ComPtr\<T >.|  
|[ComPtrRefBase, classe](../windows/comptrrefbase-class.md)|Représente la classe de base pour le [ComPtrRef](../windows/comptrref-class.md) classe.|  
|[DontUseNewUseMake, classe](../windows/dontusenewusemake-class.md)|Empêche l’utilisation d’opérateur **nouveau** dans `RuntimeClass`. Par conséquent, vous devez utiliser le [Make, fonction](../windows/make-function.md) à la place.|  
|[EventTargetArray, classe](../windows/eventtargetarray-class.md)|Représente un tableau des gestionnaires d’événements.|  
|[MakeAllocator, classe](../windows/makeallocator-class.md)|Alloue la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.|  
|[ModuleBase, classe](../windows/modulebase-class.md)|Représente la classe de base de la [Module](../windows/module-class.md) classes.|  
|[RemoveIUnknown, classe](../windows/removeiunknown-class.md)|Crée un type qui est équivalent à une `IUnknown`-type de base, a, mais non virtuelle `QueryInterface`, `AddRef`, et `Release` méthodes.|  
|[WeakReference (classe)](../windows/weakreference-class1.md)|Représente un *référence faible* qui peut être utilisé avec le Windows Runtime ou le COM classique. Une référence faible représente un objet qui peut être accessible ou non.|  
  
### <a name="structures"></a>Structures  
  
|Nom|Description|  
|----------|-----------------|  
|[ArgTraits, structure](../windows/argtraits-structure.md)|Déclare un délégué spécifié interface et une fonction membre anonyme qui a un nombre spécifié de paramètres.|  
|[ArgTraitsHelper, structure](../windows/argtraitshelper-structure.md)|Permet de définir les caractéristiques communes d’arguments du délégué.|  
|[BoolStruct, structure](../windows/boolstruct-structure.md)|Définit si un ComPtr gère la durée de vie d’une interface. BoolStruct est utilisé en interne par le [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) opérateur.|  
|[CreatorMap, structure](../windows/creatormap-structure.md)|Contient des informations sur la façon d’initialiser, inscrire et annuler l’inscription d’objets.|  
|[DerefHelper, structure](../windows/derefhelper-structure.md)|Représenter un pointeur déréférencé au `T*` paramètre de modèle.|  
|[EnableIf, structure](../windows/enableif-structure.md)|Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la valeur **true**.|  
|[FactoryCache, structure](../windows/factorycache-structure.md)|Contient l’emplacement d’une fabrique de classe et une valeur qui identifie un objet de classe Windows Runtime ou COM inscrit.|  
|[ImplementsBase, structure](../windows/implementsbase-structure.md)|Permet de valider les types de paramètre de modèle dans [Implements (Structure)](../windows/implements-structure.md).|  
|[ImplementsHelper, structure](../windows/implementshelper-structure.md)|Permet d’implémenter le [implémente](../windows/implements-structure.md) structure.|  
|[InterfaceList, structure](../windows/interfacelist-structure.md)|Utilisé pour créer une liste récursive des interfaces.|  
|[InterfaceListHelper, structure](../windows/interfacelisthelper-structure.md)|Génère un `InterfaceList` type en appliquant les arguments de paramètre de modèle spécifié de manière récursive.|  
|[InterfaceTraits, structure](../windows/interfacetraits-structure.md)|Caractéristiques communes d’implémente d’une interface.|  
|[InvokeHelper, structure](../windows/invokehelper-structure.md)|Fournit une implémentation de la `Invoke()` méthode basée sur le nombre spécifié et le type d’arguments.|  
|[IsBaseOfStrict, structure](../windows/isbaseofstrict-structure.md)|Teste si un type est la base d'un autre.|  
|[IsSame, structure](../windows/issame-structure.md)|Teste si un spécifié le type est identique à un autre de type spécifié.|  
|[Nil, structure](../windows/nil-structure.md)|Utilisé pour indiquer un paramètre de modèle non spécifié, facultatif.|  
|[RemoveReference, structure](../windows/removereference-structure.md)|Supprime la caractéristique de référence ou référence rvalue à partir du paramètre de modèle de classe spécifiée.|  
|[RuntimeClassBase, structure](../windows/runtimeclassbase-structure.md)|Permet de détecter `RuntimeClass` dans le [rendre](../windows/make-function.md) (fonction).|  
|[RuntimeClassBaseT, structure](../windows/runtimeclassbaset-structure.md)|Fournit des méthodes d’assistance pour `QueryInterface` opérations et l’obtention des ID d’interface.|  
|[VerifyInheritanceHelper, structure](../windows/verifyinheritancehelper-structure.md)|Teste si une interface est dérivée d’une autre interface.|  
|[VerifyInterfaceHelper, structure](../windows/verifyinterfacehelper-structure.md)|Vérifie que l’interface spécifiée par le paramètre de modèle répond à certaines exigences.|  
  
### <a name="enumerations"></a>Énumérations  
  
|Name|Description|  
|----------|-----------------|  
|[AsyncStatusInternal, énumération](../windows/asyncstatusinternal-enumeration.md)|Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la `Windows::Foundation::AsyncStatus` énumération.|  
  
### <a name="functions"></a>Fonctions  
  
|Nom|Description|  
|----------|-----------------|  
|[ActivationFactoryCallback, fonction](../windows/activationfactorycallback-function.md)|Obtient la fabrique d’activation pour l’ID d’activation spécifié.|  
|[move, fonction](../windows/move-function.md)|Déplace l’argument spécifié à partir d’un emplacement vers un autre.|  
|[RaiseException, fonction](../windows/raiseexception-function.md)|Lève une exception dans le thread appelant.|  
|[Swap, fonction (bibliothèque de modèles Windows Runtime C++)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Échange les valeurs des deux arguments spécifiés.|  
|[TerminateMap, fonction](../windows/terminatemap-function.md)|Arrête les fabriques de classe dans le module spécifié.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)