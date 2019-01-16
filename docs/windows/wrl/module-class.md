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
ms.openlocfilehash: db3eb123382ac70f6198d094c5eb3fe44d3bbcd9
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336029"
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
Une combinaison d’une ou plusieurs [ModuleType](moduletype-enumeration.md) valeurs d’énumération.

## <a name="members"></a>Membres

### <a name="protected-classes"></a>Classes protégées

Name                                                                                | Description
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par dans une expression lambda, functor ou pointeur de fonction.
[Module::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par un objet et son membre pointeur-à la méthode.
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | -----------------------------------------------------------
[Module :: ~ Module](#tilde-module) | Annule l’initialisation de l’instance actuelle de la `Module` classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                      | Description
------------------------- | ---------------------------------------------------
[Module::Module](#module) | Initialise une nouvelle instance de la classe `Module`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                    | Description
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::Create](#create)                               | Crée une instance d’un module.
[Module::DecrementObjectCount](#decrementobjectcount)   | Décrémente le nombre d’objets suivis par le module.
[Module::GetActivationFactory](#getactivationfactory)   | Obtient une fabrique d’activation pour le module.
[Module::GetClassObject](#getclassobject)               | Récupère un cache des fabriques de classes.
[Module::GetModule](#getmodule)                         | Crée une instance d’un module.
[Module::GetObjectCount](#getobjectcount)               | Récupère le nombre d’objets gérés par ce module.
[Module::IncrementObjectCount](#incrementobjectcount)   | Incrémente le nombre d’objets suivis par le module.
[Module::RegisterCOMObject](#registercomobject)         | Inscrit un ou plusieurs objets COM afin d’autres applications peuvent se connecter à leur.
[Module::RegisterObjects](#registerobjects)             | Enregistre les objets COM ou Windows Runtime pour d’autres applications peuvent se connecter à leur.
[Module::RegisterWinRTObject](#registerwinrtobject)     | Inscrit un ou plusieurs objets Windows Runtime pour d’autres applications peuvent se connecter à leur.
[Module::Terminate](#terminate)                         | Provoque toutes les fabriques instanciés par le module à arrêter.
[Module::UnregisterCOMObject](#unregistercomobject)     | Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche les autres applications de se connecter à leur.
[Module::UnregisterObjects](#unregisterobjects)         | Annule l’inscription d’objets dans le module spécifié afin que les autres applications ne peuvent pas s’y connecter.
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que les autres applications ne peuvent pas s’y connecter.

### <a name="protected-methods"></a>Méthodes protégées

Nom                      | Description
------------------------- | --------------------------------
[Module::Create](#create) | Crée une instance d’un module.

### <a name="protected-data-members"></a>Membres de données protégés

Name                                         | Description
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectCount_](#objectcount)         | Effectue le suivi des classes combien ont été créés avec le [rendre](make-function.md) (fonction).
[Module::releaseNotifier_](#releasenotifier) | Contient un pointeur vers un `ReleaseNotifier` objet.

### <a name="macros"></a>Macros

Nom | Description------| --- [ActivatableClass](activatableclass-macros.md) |  Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro spécifie les paramètres de ID de fabrique et de groupe par défaut.
[ActivatableClassWithFactory](activatableclass-macros.md) | Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro vous permet de spécifier un paramètre d’usine donnée.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée. Cette macro vous permet de spécifier une usine donnée et les paramètres d’ID de groupe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Spécifications

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="tilde-module"></a>Module :: ~ Module

Annule l’initialisation de l’instance actuelle de la `Module` classe.

```cpp
virtual ~Module();
```

## <a name="create"></a>Module::Create

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

*callback*<br/>
Appelé lorsque le dernier objet d’instance du module est relâché.

*object*<br/>
Le *objet* et *méthode* paramètres sont utilisés conjointement. Pointe vers le dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.

*method*<br/>
Le *objet* et *méthode* paramètres sont utilisés conjointement. Points à la méthode du dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.

### <a name="return-value"></a>Valeur de retour

Référence au module.

## <a name="decrementobjectcount"></a>Module::DecrementObjectCount

Décrémente le nombre d’objets suivis par le module.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre avant l’opération de décrémentation.

## <a name="getactivationfactory"></a>Module::GetActivationFactory

Obtient une fabrique d’activation pour le module.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*pActivatibleClassId*<br/>
IID d’une classe runtime.

*ppIFactory*<br/>
IActivationFactory pour la classe runtime spécifié.

*serverName*<br/>
Le nom d’un sous-ensemble des fabriques de classes du module en cours. Spécifiez le nom du serveur utilisé dans le [ActivatableClassWithFactoryEx](activatableclass-macros.md) (macro), ou spécifiez `nullptr` pour obtenir le nom du serveur par défaut.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, le HRESULT retourné par GetActivationFactory.

## <a name="getclassobject"></a>Module::GetClassObject

Récupère un cache des fabriques de classes.

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
ID de classe.

*riid*<br/>
ID d’interface que vous demandez.

*ppv*<br/>
Pointeur vers l’objet retourné.

*serverName*<br/>
Le nom du serveur qui est spécifié dans le `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, ou `ActivatableClass` macro ; ou `nullptr` pour obtenir le nom du serveur par défaut.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement pour COM, pas l’exécution de Windows. Cette méthode expose uniquement `IClassFactory` méthodes.

## <a name="getmodule"></a>Module::GetModule

Crée une instance d’un module.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Valeur de retour

Une référence à un module.

## <a name="getobjectcount"></a>Module::GetObjectCount

Récupère le nombre d’objets gérés par ce module.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre actuel d’objets gérés par ce module.

## <a name="incrementobjectcount"></a>Module::IncrementObjectCount

Incrémente le nombre d’objets suivis par le module.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre avant l’opération d’incrémentation.

## <a name="module"></a>Module::Module

Initialise une nouvelle instance de la classe `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Notes

Ce constructeur est protégé et ne peut pas être appelé avec le `new` mot clé. Au lieu de cela, appelez [Module::GetModule](#getmodule) ou [Module::Create](#create).

## <a name="objectcount"></a>Module::objectCount_

Effectue le suivi des classes combien ont été créés avec le [rendre](make-function.md) (fonction).

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module::RegisterCOMObject

Inscrit un ou plusieurs objets COM afin d’autres applications peuvent se connecter à leur.

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
Nom qualifié complet d’un serveur.

*clsids*<br/>
Tableau de CLSID à inscrire.

*factories*<br/>
Tableau d’interfaces IUnknown des objets de classe dont la disponibilité est en cours de publication.

*cookies*<br/>
Lorsque l’opération se termine, un tableau de pointeurs vers des valeurs qui identifient la classe des objets qui ont été enregistrés. Ces valeurs sont utilisées ultérieurement révoque l’inscription.

*count*<br/>
Le nombre de CLSID à inscrire.

### <a name="return-value"></a>Valeur de retour

S_OK si réussies ; Sinon, un HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

### <a name="remarks"></a>Notes

Les objets COM sont enregistrés avec l’énumérateur CLSCTX_LOCAL_SERVER de l’énumération CLSCTX.

Le type de connexion pour les objets inscrits est spécifié par une combinaison de cours *comflag* paramètre de modèle et de l’énumérateur REGCLS_SUSPENDED de l’énumération REGCLS.

## <a name="registerobjects"></a>Module::RegisterObjects

Enregistre les objets COM ou Windows Runtime pour d’autres applications peuvent se connecter à leur.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Un tableau d’objets COM ou Windows Runtime.

*serverName*<br/>
Nom du serveur qui a créé les objets.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique la raison pour laquelle l’opération a échoué.

## <a name="registerwinrtobject"></a>Module::RegisterWinRTObject

Inscrit un ou plusieurs objets Windows Runtime pour d’autres applications peuvent se connecter à leur.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
Nom qui spécifie un sous-ensemble d’objets affectés par cette opération.

*activatableClassIds*<br/>
Tableau des CLSID activables à inscrire.

*cookie*<br/>
Une valeur qui identifie les objets de classe qui ont été inscrits. Cette valeur est utilisée ultérieurement pour révoquer l’inscription.

*count*<br/>
Le nombre d’objets à inscrire.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

## <a name="releasenotifier"></a>Module::releaseNotifier_

Contient un pointeur vers un `ReleaseNotifier` objet.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module::Terminate

Provoque toutes les fabriques instanciés par le module à arrêter.

```cpp
void Terminate();
```

### <a name="remarks"></a>Notes

Libère les fabriques dans le cache.

## <a name="unregistercomobject"></a>Module::UnregisterCOMObject

Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche les autres applications de se connecter à leur.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
(Non utilisé)

*cookies*<br/>
Un tableau de pointeurs vers des valeurs qui identifient les objets de classe doit être annulée. Le tableau a été créé par le [RegisterCOMObject](#registercomobject) (méthode).

*count*<br/>
Le nombre de classes pour annuler l’inscription.

### <a name="return-value"></a>Valeur de retour

S_OK si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la raison pour laquelle l’opération a échoué.

## <a name="unregisterobjects"></a>Module::UnregisterObjects

Annule l’inscription d’objets dans le module spécifié afin que les autres applications ne peuvent pas s’y connecter.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Pointeur vers un module.

*serverName*<br/>
Nom de qualification qui spécifie un sous-ensemble d’objets affectés par cette opération.

### <a name="return-value"></a>Valeur de retour

S_OK si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="unregisterwinrtobject"></a>Module::UnregisterWinRTObject

Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que les autres applications ne peuvent pas s’y connecter.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Paramètres

*cookie*<br/>
Pointeur vers une valeur qui identifie l’objet de classe dont l’inscription doit être révoqué.
