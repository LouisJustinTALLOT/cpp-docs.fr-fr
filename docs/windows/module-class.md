---
title: Classe de module | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
dev_langs:
- C++
helpviewer_keywords:
- Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a4c437035713634736a02afbce1325d14ba18229
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604409"
---
# <a name="module-class"></a>Module (classe)
Représente une collection d’objets connexes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<ModuleType moduleType>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
### <a name="parameters"></a>Paramètres  
 *type de module*  
 Une combinaison d’une ou plusieurs [ModuleType](../windows/moduletype-enumeration.md) valeurs d’énumération.  
  
## <a name="members"></a>Membres  
  
### <a name="protected-classes"></a>Classes protégées  
  
|Name|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier, classe](../windows/module-genericreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par dans une expression lambda, functor ou pointeur de fonction.|  
|[Module::MethodReleaseNotifier, classe](../windows/module-methodreleasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par un objet et son membre pointeur-à la méthode.|  
|[Module::ReleaseNotifier, classe](../windows/module-releasenotifier-class.md)|Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::~Module, destructeur](../windows/module-tilde-module-destructor.md)|Annule l’initialisation de l’instance actuelle de la **Module** classe.|  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::Module, constructeur](../windows/module-module-constructor.md)|Initialise une nouvelle instance de la **Module** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::Create, méthode](../windows/module-create-method.md)|Crée une instance d’un module.|  
|[Module::DecrementObjectCount, méthode](../windows/module-decrementobjectcount-method.md)|Décrémente le nombre d’objets suivis par le module.|  
|[Module::GetActivationFactory, méthode](../windows/module-getactivationfactory-method.md)|Obtient une fabrique d’activation pour le module.|  
|[Module::GetClassObject, méthode](../windows/module-getclassobject-method.md)|Récupère un cache des fabriques de classes.|  
|[Module::GetModule, méthode](../windows/module-getmodule-method.md)|Crée une instance d’un module.|  
|[Module::GetObjectCount, méthode](../windows/module-getobjectcount-method.md)|Récupère le nombre d’objets gérés par ce module.|  
|[Module::IncrementObjectCount, méthode](../windows/module-incrementobjectcount-method.md)|Incrémente le nombre d’objets suivis par le module.|  
|[Module::RegisterCOMObject, méthode](../windows/module-registercomobject-method.md)|Inscrit un ou plusieurs objets COM afin d’autres applications peuvent se connecter à leur.|  
|[Module::RegisterObjects, méthode](../windows/module-registerobjects-method.md)|Enregistre les objets COM ou Windows Runtime pour d’autres applications peuvent se connecter à leur.|  
|[Module::RegisterWinRTObject, méthode](../windows/module-registerwinrtobject-method.md)|Inscrit un ou plusieurs objets Windows Runtime pour d’autres applications peuvent se connecter à leur.|  
|[Module::Terminate, méthode](../windows/module-terminate-method.md)|Provoque toutes les fabriques instanciés par le module à arrêter.|  
|[Module::UnregisterCOMObject, méthode](../windows/module-unregistercomobject-method.md)|Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche les autres applications de se connecter à leur.|  
|[Module::UnregisterObjects, méthode](../windows/module-unregisterobjects-method.md)|Annule l’inscription d’objets dans le module spécifié afin que les autres applications ne peuvent pas s’y connecter.|  
|[Module::UnregisterWinRTObject, méthode](../windows/module-unregisterwinrtobject-method.md)|Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que les autres applications ne peuvent pas s’y connecter.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::Create, méthode](../windows/module-create-method.md)|Crée une instance d’un module.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[Module::objectCount_, données de membre](../windows/module-objectcount-data-member.md)|Effectue le suivi des classes combien ont été créés avec le [rendre](../windows/make-function.md) (fonction).|  
|[Module::releaseNotifier_, données de membre](../windows/module-releasenotifier-data-member.md)|Contient un pointeur vers un objet ReleaseNotifier.|  
  
### <a name="macros"></a>Macros  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro spécifie les paramètres de ID de fabrique et de groupe par défaut.|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro vous permet de spécifier un paramètre d’usine donnée.|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro vous permet de spécifier une usine donnée et les paramètres d’ID de groupe.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)