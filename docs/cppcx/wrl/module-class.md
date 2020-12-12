---
description: 'En savoir plus sur : classe de module'
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
ms.openlocfilehash: 00063bca4d35ca2d7eab09ad9d03d57dcdc85593
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186387"
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
Combinaison d’une ou de plusieurs valeurs d’énumération [ModuleType](moduletype-enumeration.md) .

## <a name="members"></a>Membres

### <a name="protected-classes"></a>Classes protégées

Nom                                                                                | Description
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module :: GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par sur un lambda, un functor ou un pointeur vers une fonction.
[Module :: MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le gestionnaire d’événements est spécifié par un objet et son membre pointeur-à-a-Method.
[Module :: ReleaseNotifier](module-releasenotifier-class.md)               | Appelle un gestionnaire d’événements lorsque le dernier objet d’un module est relâché.

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | -----------------------------------------------------------
[Module :: ~ module](#tilde-module) | Désinitialise l’instance actuelle de la `Module` classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                      | Description
------------------------- | ---------------------------------------------------
[Module :: module](#module) | Initialise une nouvelle instance de la classe `Module`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                    | Description
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module :: Create](#create)                               | Crée une instance d’un module.
[Module ::D ecrementObjectCount](#decrementobjectcount)   | Décrémente le nombre d’objets suivis par le module.
[Module :: GetActivationFactory](#getactivationfactory)   | Obtient une fabrique d’activation pour le module.
[Module :: GetClassObject,](#getclassobject)               | Récupère un cache de fabriques de classes.
[Module :: GetModule](#getmodule)                         | Crée une instance d’un module.
[Module :: Getobjectcount,](#getobjectcount)               | Récupère le nombre d’objets managés par ce module.
[Module :: Incrementobjectcount,](#incrementobjectcount)   | Incrémente le nombre d’objets suivis par le module.
[Module :: Registercomobject,](#registercomobject)         | Inscrit un ou plusieurs objets COM afin que d’autres applications puissent s’y connecter.
[Module :: Registerobjects,](#registerobjects)             | Inscrit des objets COM ou Windows Runtime pour permettre à d’autres applications de s’y connecter.
[Module :: Registerwinrtobject,](#registerwinrtobject)     | Inscrit un ou plusieurs objets Windows Runtime pour permettre à d’autres applications de s’y connecter.
[Module :: Terminate](#terminate)                         | Entraîne l’arrêt de toutes les fabriques instanciées par le module.
[Module :: Unregistercomobject,](#unregistercomobject)     | Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche d’autres applications de s’y connecter.
[Module :: Unregisterobjects,](#unregisterobjects)         | Annule l’inscription des objets dans le module spécifié afin que d’autres applications ne puissent pas s’y connecter.
[Module :: Unregisterwinrtobject,](#unregisterwinrtobject) | Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que d’autres applications ne puissent pas s’y connecter.

### <a name="protected-methods"></a>Méthodes protégées

Nom                      | Description
------------------------- | --------------------------------
[Module :: Create](#create) | Crée une instance d’un module.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                         | Description
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module :: objectCount_](#objectcount)         | Effectue le suivi du nombre de classes qui ont été créées avec la fonction [Make](make-function.md) .
[Module :: releaseNotifier_](#releasenotifier) | Contient un pointeur vers un `ReleaseNotifier` objet.

### <a name="macros"></a>Macros

Nom                                                                   | Description
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée. Cette macro spécifie les paramètres d’ID de groupe et de fabrique par défaut.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée. Cette macro vous permet de spécifier un paramètre Factory particulier.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée. Cette macro vous permet de spécifier des paramètres d’ID de fabrique et de groupe particuliers.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a> Module :: ~ module

Désinitialise l’instance actuelle de la `Module` classe.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a> Module :: Create

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
Appelé lorsque le dernier objet d’instance du module est relâché.

*object*<br/>
Les paramètres d' *objet* et de *méthode* sont utilisés en combinaison. Pointe vers le dernier objet d’instance lorsque le dernier objet d’instance du module est relâché.

*method*<br/>
Les paramètres d' *objet* et de *méthode* sont utilisés en combinaison. Pointe vers la méthode du dernier objet d’instance lorsque le dernier objet d’instance du module est relâché.

### <a name="return-value"></a>Valeur renvoyée

Référence au module.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a> Module ::D ecrementObjectCount

Décrémente le nombre d’objets suivis par le module.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre avant l’opération de décrémentation.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a> Module :: GetActivationFactory

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
IID d’une classe Runtime.

*ppIFactory*<br/>
IActivationFactory pour la classe d’exécution spécifiée.

*serverName*<br/>
Nom d’un sous-ensemble de fabriques de classes dans le module actuel. Spécifiez le nom du serveur utilisé dans la macro [ActivatableClassWithFactoryEx](activatableclass-macros.md) ou spécifiez **`nullptr`** pour récupérer le nom du serveur par défaut.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT retourné par GetActivationFactory.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a> Module :: GetClassObject,

Extrait un cache de fabriques de classes.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
ID de classe.

*riid*<br/>
ID d’interface que vous demandez.

*ppv*<br/>
Pointeur vers un objet retourné.

*serverName*<br/>
Nom du serveur spécifié dans la `ActivatableClassWithFactory` macro, ou, `ActivatableClassWithFactoryEx` `ActivatableClass` ou **`nullptr`** pour récupérer le nom du serveur par défaut.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement pour COM, et non pour le Windows Runtime. Cette méthode expose uniquement les `IClassFactory` méthodes.

## <a name="modulegetmodule"></a><a name="getmodule"></a> Module :: GetModule

Crée une instance d’un module.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à un module.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a> Module :: Getobjectcount,

Récupère le nombre d’objets managés par ce module.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre actuel d’objets gérés par ce module.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a> Module :: Incrementobjectcount,

Incrémente le nombre d’objets suivis par le module.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre avant l’opération d’incrémentation.

## <a name="modulemodule"></a><a name="module"></a> Module :: module

Initialise une nouvelle instance de la classe `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Notes

Ce constructeur est protégé et ne peut pas être appelé avec le **`new`** mot clé. Au lieu de cela, appelez [module :: GetModule](#getmodule) ou [module :: Create](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a> Module :: objectCount_

Effectue le suivi du nombre de classes qui ont été créées avec la fonction [Make](make-function.md) .

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a> Module :: Registercomobject,

Inscrit un ou plusieurs objets COM afin que d’autres applications puissent s’y connecter.

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
Nom complet d’un serveur.

*CLSID*<br/>
Tableau de CLSID à inscrire.

*factories*<br/>
Tableau d’interfaces IUnknown des objets de classe dont la disponibilité est en cours de publication.

*cookies*<br/>
Lorsque l’opération est terminée, un tableau de pointeurs vers des valeurs qui identifient les objets de classe qui ont été inscrits. Ces valeurs sont utilisées ultérieurement pour révoquer l’inscription.

*count*<br/>
Nombre de CLSID à inscrire.

### <a name="return-value"></a>Valeur renvoyée

S_OK si réussies ; Sinon, HRESULT comme CO_E_OBJISREG qui indique la raison de l’échec de l’opération.

### <a name="remarks"></a>Notes

Les objets COM sont inscrits avec l’énumérateur CLSCTX_LOCAL_SERVER de l’énumération CLSCTX.

Le type de connexion aux objets inscrits est spécifié par une combinaison du paramètre de modèle *comindicateur* actuel et de l’énumérateur REGCLS_SUSPENDED de l’énumération REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a> Module :: Registerobjects,

Inscrit des objets COM ou Windows Runtime pour permettre à d’autres applications de s’y connecter.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*modules*<br/>
Tableau d’objets COM ou Windows Runtime.

*serverName*<br/>
Nom du serveur qui a créé les objets.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT qui indique la raison de l’échec de l’opération.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a> Module :: Registerwinrtobject,

Inscrit un ou plusieurs objets Windows Runtime pour permettre à d’autres applications de s’y connecter.

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
Tableau de CLSID activables à inscrire.

*cookie*<br/>
Valeur qui identifie les objets de classe qui ont été inscrits. Cette valeur est utilisée ultérieurement pour révoquer l’inscription.

*count*<br/>
Nombre d’objets à inscrire.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, une erreur HRESULT telle que CO_E_OBJISREG qui indique la raison de l’échec de l’opération.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a> Module :: releaseNotifier_

Contient un pointeur vers un `ReleaseNotifier` objet.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a> Module :: Terminate

Entraîne l’arrêt de toutes les fabriques instanciées par le module.

```cpp
void Terminate();
```

### <a name="remarks"></a>Notes

Libère les fabriques dans le cache.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a> Module :: Unregistercomobject,

Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche d’autres applications de s’y connecter.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Paramètres

*serverName*<br/>
Inutilisé

*cookies*<br/>
Tableau de pointeurs vers des valeurs qui identifient les objets de classe dont l’inscription doit être annulée. Le tableau a été créé par la méthode [registercomobject,](#registercomobject) .

*count*<br/>
Nombre de classes dont l’inscription doit être annulée.

### <a name="return-value"></a>Valeur renvoyée

S_OK si cette opération réussit ; Sinon, une erreur HRESULT qui indique la raison de l’échec de l’opération.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a> Module :: Unregisterobjects,

Annule l’inscription des objets dans le module spécifié afin que d’autres applications ne puissent pas s’y connecter.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*modules*<br/>
Pointeur vers un module.

*serverName*<br/>
Nom qualifiant qui spécifie un sous-ensemble d’objets affectés par cette opération.

### <a name="return-value"></a>Valeur renvoyée

S_OK si cette opération réussit ; Sinon, une erreur HRESULT qui indique la raison de l’échec de cette opération.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a> Module :: Unregisterwinrtobject,

Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que d’autres applications ne puissent pas s’y connecter.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Paramètres

*cookie*<br/>
Pointeur vers une valeur qui identifie l’objet de classe dont l’inscription doit être révoquée.
