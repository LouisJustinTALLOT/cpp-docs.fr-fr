---
title: Module (classe)
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371314"
---
# <a name="module-class"></a>Module (classe)

Représente une collection d’objets connexes.

## <a name="syntax"></a>Syntaxe

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Paramètres

*moduleType*<br/>
Une combinaison d’une ou plusieurs valeurs d’énumération [ModuleType.](moduletype-enumeration.md)

## <a name="members"></a>Membres

### <a name="protected-classes"></a>Classes protégées

Nom                                                                                | Description
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Invoque un gestionnaire d’événements lorsque le dernier objet du module actuel est libéré. Le gestionnaire d’événements est spécifié par sur un lambda, functor, ou pointeur-à-fonction.
[Module::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Invoque un gestionnaire d’événements lorsque le dernier objet du module actuel est libéré. Le gestionnaire d’événements est spécifié par un objet et son membre pointeur à une méthode.
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | Invoque un gestionnaire d’événements lorsque le dernier objet d’un module est libéré.

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | -----------------------------------------------------------
[Module::Module](#tilde-module) | Désinitialise l’instance actuelle `Module` de la classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                      | Description
------------------------- | ---------------------------------------------------
[Module::Module](#module) | Initialise une nouvelle instance de la classe `Module`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                    | Description
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::Créer](#create)                               | Crée une instance d’un module.
[Module::DecrementObjectCount](#decrementobjectcount)   | Décroisse le nombre d’objets suivis par le module.
[Module::GetActivationFactory](#getactivationfactory)   | Obtient une usine d’activation pour le module.
[Module::GetClassObject](#getclassobject)               | Récupère une cache d’usines de classe.
[Module::GetModule](#getmodule)                         | Crée une instance d’un module.
[Module::GetObjectCount](#getobjectcount)               | Récupère le nombre d’objets gérés par ce module.
[Module::IncrementObjectCount](#incrementobjectcount)   | Incréments le nombre d’objets suivis par le module.
[Module::RegisterCOMObject](#registercomobject)         | Enregistre un ou plusieurs objets COM afin que d’autres applications puissent se connecter à eux.
[Module::RegisterObjects](#registerobjects)             | Enregistre les objets COM ou Windows Runtime afin que d’autres applications puissent se connecter à eux.
[Module::RegisterWinRTObject](#registerwinrtobject)     | Enregistre un ou plusieurs objets Windows Runtime afin que d’autres applications puissent se connecter à eux.
[Module::Terminate](#terminate)                         | Provoque l’arrêt de toutes les usines instantanées par le module.
[Module::UnregisterCOMObject](#unregistercomobject)     | Désenregistre un ou plusieurs objets COM, ce qui empêche d’autres applications de se connecter à eux.
[Module::UnregisterObjects](#unregisterobjects)         | Désenregistre les objets dans le module spécifié afin que d’autres applications ne puissent pas se connecter à eux.
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | Déenregistre un ou plusieurs objets Windows Runtime afin que d’autres applications ne puissent pas se connecter à eux.

### <a name="protected-methods"></a>Méthodes protégées

Nom                      | Description
------------------------- | --------------------------------
[Module::Créer](#create) | Crée une instance d’un module.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                         | Description
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectCount_](#objectcount)         | Garde une trace du nombre de classes créées avec la fonction [Make.](make-function.md)
[Module::releaseNotifier_](#releasenotifier) | Tient un pointeur à un `ReleaseNotifier` objet.

### <a name="macros"></a>Macros

Nom                                                                   | Description
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Remplit un cache interne qui contient une usine qui peut créer une instance de la classe spécifiée. Cette macro spécifie les paramètres d’identification par défaut de l’usine et du groupe.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Remplit un cache interne qui contient une usine qui peut créer une instance de la classe spécifiée. Cette macro vous permet de spécifier un paramètre d’usine particulier.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Remplit un cache interne qui contient une usine qui peut créer une instance de la classe spécifiée. Cette macro vous permet de spécifier des paramètres d’identification d’usine et de groupe particuliers.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Spécifications

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Module::Module

Désinitialise l’instance actuelle `Module` de la classe.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Module::Créer

Crée une instance d’un module.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de module.

*rappel*<br/>
Appelé lorsque le dernier objet de instance du module est libéré.

*Objet*<br/>
Les paramètres *de l’objet* et de *la méthode* sont utilisés en combinaison. Indique l’objet de dernière instance lorsque l’objet de dernière instance dans le module est libéré.

*Méthode*<br/>
Les paramètres *de l’objet* et de *la méthode* sont utilisés en combinaison. Indique la méthode de l’objet de dernière instance lorsque l’objet de dernière instance dans le module est libéré.

### <a name="return-value"></a>Valeur de retour

Référence au module.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Module::DecrementObjectCount

Décroisse le nombre d’objets suivis par le module.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Valeur de retour

Le compte avant l’opération de décroissement.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Module::GetActivationFactory

Obtient une usine d’activation pour le module.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*pActivatibleClassId*<br/>
IID d’un cours de runtime.

*ppIFactory*<br/>
L’IActivationFactory pour la classe de temps d’exécution spécifiée.

*serverName*<br/>
Le nom d’un sous-ensemble d’usines de classe dans le module actuel. Spécifiez le nom du serveur utilisé dans la `nullptr` macro [ActivatableClassWithFactoryEx,](activatableclass-macros.md) ou spécifiez pour obtenir le nom du serveur par défaut.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, le HRESULT retourné par GetActivationFactory.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Module::GetClassObject

Retreive une cache d’usines de classe.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
Id de classe.

*riid*<br/>
Interface ID que vous demandez.

*Ppv*<br/>
Pointeur à l’objet retourné.

*serverName*<br/>
Le nom du serveur qui `ActivatableClassWithFactory` `ActivatableClassWithFactoryEx`est `ActivatableClass` spécifié dans le , , ou macro; ou `nullptr` pour obtenir le nom du serveur par défaut.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement pour COM, pas le Windows Runtime. Cette méthode n’expose que `IClassFactory` les méthodes.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Module::GetModule

Crée une instance d’un module.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Valeur de retour

Une référence à un module.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Module::GetObjectCount

Récupère le nombre d’objets gérés par ce module.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre actuel d’objets gérés par ce module.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Module::IncrementObjectCount

Incréments le nombre d’objets suivis par le module.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Valeur de retour

Le compte avant l’opération d’incrément.

## <a name="modulemodule"></a><a name="module"></a>Module::Module

Initialise une nouvelle instance de la classe `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Notes

Ce constructeur est protégé et ne `new` peut pas être appelé avec le mot clé. Au lieu de cela, appelez soit [Module::GetModule](#getmodule) ou [Module::Créer](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Module::objectCount_

Garde une trace du nombre de classes créées avec la fonction [Make.](make-function.md)

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Module::RegisterCOMObject

Enregistre un ou plusieurs objets COM afin que d’autres applications puissent se connecter à eux.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
Nom entièrement qualifié d’un serveur.

*clsids*<br/>
Un éventail de CLSIDs à enregistrer.

*factories*<br/>
Une gamme d’interfaces IUnknown des objets de classe dont la disponibilité est publiée.

*Cookies*<br/>
Lorsque l’opération se termine, un tableau de points à des valeurs qui identifient les objets de classe qui ont été enregistrés. Ces valeurs sont plus tard utilisées révoquer l’enregistrement.

*count*<br/>
Le nombre de CLSID à enregistrer.

### <a name="return-value"></a>Valeur de retour

S_OK si successfu; autrement, un HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

### <a name="remarks"></a>Notes

Les objets COM sont enregistrés auprès du CLSCTX_LOCAL_SERVER enumérateur de l’énumération CLSCTX.

Le type de connexion aux objets enregistrés est spécifié par une combinaison du paramètre actuel du modèle de *comflag* et du REGCLS_SUSPENDED’enumérateur de l’énumération REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Module::RegisterObjects

Enregistre les objets COM ou Windows Runtime afin que d’autres applications puissent se connecter à eux.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Une gamme d’objets COM ou Windows Runtime.

*serverName*<br/>
Nom du serveur qui a créé les objets.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, un HRESULT qui indique la raison pour laquelle l’opération a échoué.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Module::RegisterWinRTObject

Enregistre un ou plusieurs objets Windows Runtime afin que d’autres applications puissent se connecter à eux.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
Un nom qui spécifie un sous-ensemble d’objets affectés par cette opération.

*activatableClassIds*<br/>
Un éventail de CLSID activatables à enregistrer.

*Cookie*<br/>
Une valeur qui identifie les objets de classe qui ont été enregistrés. Cette valeur est utilisée plus tard pour révoquer l’enregistrement.

*count*<br/>
Le nombre d’objets à enregistrer.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, une erreur HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Module::releaseNotifier_

Tient un pointeur à un `ReleaseNotifier` objet.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Module::Terminate

Provoque l’arrêt de toutes les usines instantanées par le module.

```cpp
void Terminate();
```

### <a name="remarks"></a>Notes

Libère les usines dans le cache.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Module::UnregisterCOMObject

Désenregistre un ou plusieurs objets COM, ce qui empêche d’autres applications de se connecter à eux.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
(Inutilisé)

*Cookies*<br/>
Un éventail de points sur les valeurs qui identifient les objets de classe à non enregistrés. Le tableau a été créé par la méthode [RegisterCOMObject.](#registercomobject)

*count*<br/>
Le nombre de classes à non enregistrés.

### <a name="return-value"></a>Valeur de retour

S_OK si cette opération est couronnée de succès; autrement, une erreur HRESULT qui indique la raison pour laquelle l’opération a échoué.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Module::UnregisterObjects

Désenregistre les objets dans le module spécifié afin que d’autres applications ne puissent pas se connecter à eux.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Pointeur vers un module.

*serverName*<br/>
Un nom de qualification qui spécifie un sous-ensemble d’objets affectés par cette opération.

### <a name="return-value"></a>Valeur de retour

S_OK si cette opération est couronnée de succès; autrement, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Module::UnregisterWinRTObject

Déenregistre un ou plusieurs objets Windows Runtime afin que d’autres applications ne puissent pas se connecter à eux.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Paramètres

*Cookie*<br/>
Un pointeur à une valeur qui identifie l’objet de classe dont l’enregistrement doit être révoqué.
