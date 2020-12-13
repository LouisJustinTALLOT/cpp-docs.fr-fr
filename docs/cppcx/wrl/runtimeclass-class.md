---
description: 'En savoir plus sur : classe RuntimeClass'
title: RuntimeClass, classe
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: f62eec0b5ac9b8fc8ecac390ea07077743fdcb51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330757"
---
# <a name="runtimeclass-class"></a>RuntimeClass, classe

Représente une classe WinRT ou COM qui hérite des interfaces spécifiées et fournit le Windows Runtime, le COM classique et la prise en charge de référence faible spécifiés.

Cette classe fournit l’implémentation réutilisable des classes WinRT et com, en fournissant l’implémentation de `QueryInterface` , `AddRef` , `Release` etc., gère le décompte de références du module et prend en charge la fourniture de la fabrique de classe pour les objets activables.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Paramètres

*classFlags*<br/>
Paramètre facultatif. Combinaison d’une ou de plusieurs valeurs d’énumération [RuntimeClassType](runtimeclasstype-enumeration.md) . La `__WRL_CONFIGURATION_LEGACY__` macro peut être définie pour modifier la valeur par défaut de classFlags pour toutes les classes de Runtime du projet. S’ils sont définis, les instances RuntimeClass sont non agiles par défaut. Lorsqu’elles ne sont pas définies, les instances RuntimeClass sont agiles par défaut. Pour éviter toute ambiguïté, spécifiez toujours le `Microsoft::WRL::FtmBase` dans `TInterfaces` ou `RuntimeClassType::InhibitFtmBase` . Notez que si InhibitFtmBase et FtmBase sont tous deux utilisés, l’objet sera agile.

*TInterfaces*<br/>
Liste des interfaces que l’objet implémente au-delà `IUnknown` `IInspectable` ou d’autres interfaces contrôlées par [RuntimeClassType](runtimeclasstype-enumeration.md). Il peut également répertorier d’autres classes à dériver de, notamment `Microsoft::WRL::FtmBase` pour rendre l’objet agile et l’implémenter `IMarshal` .

## <a name="members"></a>Membres

`RuntimeClassInitialize`<br/>
Fonction qui initialise l’objet si la `MakeAndInitialize` fonction de modèle est utilisée pour construire l’objet. Elle retourne S_OK si l’objet a été initialisé avec succès ou un code d’erreur COM en cas d’échec de l’initialisation. Le code d’erreur COM est propagé comme valeur de retour de `MakeAndInitialize` . Notez que la `RuntimeClassInitialize` méthode n’est pas appelée si la `Make` fonction de modèle est utilisée pour construire l’objet.

### <a name="public-constructors"></a>Constructeurs publics

| Nom                                               | Description                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass :: RuntimeClass](#runtimeclass)        | Initialise l’instance actuelle de la `RuntimeClass` classe.   |
| [RuntimeClass :: ~ RuntimeClass](#tilde-runtimeclass) | Désinitialise l’instance actuelle de la `RuntimeClass` classe. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                      | Description                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass :: AddRef](#addref)                           | Incrémente le décompte de références pour l' `RuntimeClass` objet actuel.                              |
| [RuntimeClass ::D ecrementReference](#decrementreference)   | Décrémente le décompte de références pour l' `RuntimeClass` objet actuel.                              |
| [RuntimeClass :: Getiids,](#getiids)                         | Obtient un tableau qui peut contenir les ID d’interface implémentés par l' `RuntimeClass` objet actuel. |
| [RuntimeClass :: Getruntimeclassname,](#getruntimeclassname) | Obtient le nom de la classe d’exécution de l' `RuntimeClass` objet actuel.                                  |
| [RuntimeClass :: Gettrustlevel,](#gettrustlevel)             | Obtient le niveau de confiance de l' `RuntimeClass` objet actuel.                                         |
| [RuntimeClass :: Getweakreference,](#getweakreference)       | Obtient un pointeur vers l’objet de référence faible pour l' `RuntimeClass` objet actuel.                 |
| [RuntimeClass :: Internaladdref,](#internaladdref)           | Incrémente le décompte de références à l' `RuntimeClass` objet actuel.                               |
| [RuntimeClass :: QueryInterface](#queryinterface)           | Récupère un pointeur vers l’ID d’interface spécifié.                                                 |
| [RuntimeClass :: Release](#release)                         | Exécute une opération de mise en service COM sur l' `RuntimeClass` objet actuel.                             |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

Il s'agit d'un détail d'implémentation.

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a> RuntimeClass :: ~ RuntimeClass

Désinitialise l’instance actuelle de la `RuntimeClass` classe.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a> RuntimeClass :: AddRef

Incrémente le décompte de références pour l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a> RuntimeClass ::D ecrementReference

Décrémente le décompte de références pour l' `RuntimeClass` objet actuel.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a> RuntimeClass :: Getiids,

Obtient un tableau qui peut contenir les ID d’interface implémentés par l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*Iidcount,*<br/>
Lorsque cette opération est terminée, il s’agit du nombre total d’éléments dans les *IID* de tableau.

*IID*<br/>
Lorsque cette opération est terminée, pointeur vers un tableau d’ID d’interface.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a> RuntimeClass :: Getruntimeclassname,

Obtient le nom de la classe d’exécution de l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Paramètres

*runtimeName*<br/>
Lorsque cette opération est terminée, le nom de la classe d’exécution.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Une erreur d’assertion est émise si `__WRL_STRICT__` ou `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` n’est pas défini.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a> RuntimeClass :: Gettrustlevel,

Obtient le niveau de confiance de l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération est terminée, le niveau de confiance de l' `RuntimeClass` objet actuel.

### <a name="return-value"></a>Valeur renvoyée

Toujours S_OK.

### <a name="remarks"></a>Notes

Une erreur d’assertion est émise si `__WRL_STRICT__` ou `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` n’est pas défini.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a> RuntimeClass :: Getweakreference,

Obtient un pointeur vers l’objet de référence faible pour l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Paramètres

*weakReference*<br/>
Lorsque cette opération est terminée, pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur renvoyée

Toujours S_OK.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a> RuntimeClass :: Internaladdref,

Incrémente le décompte de références à l' `RuntimeClass` objet actuel.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur renvoyée

Le décompte de références résultant.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a> RuntimeClass :: QueryInterface

Récupère un pointeur vers l’ID d’interface spécifié.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque ce opereation est terminé, pointeur vers l’interface spécifiée par le paramètre *riid* .

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassrelease"></a><a name="release"></a> RuntimeClass :: Release

Exécute une opération de mise en service COM sur l' `RuntimeClass` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si le nombre de références est égal à zéro, l' `RuntimeClass` objet est supprimé.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a> RuntimeClass :: RuntimeClass

Initialise l’instance actuelle de la `RuntimeClass` classe.

```cpp
RuntimeClass();
```
