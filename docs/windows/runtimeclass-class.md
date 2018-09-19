---
title: Runtimeclass, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/11/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3bc016367495be8cc10c09605e8018811bde5ca9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118906"
---
# <a name="runtimeclass-class"></a>RuntimeClass, classe

Représente une classe WinRT ou COM qui hérite des interfaces spécifiées et fournit le Runtime Windows spécifié, COM classique et prise en charge de la référence faible.

Cette classe fournit l’implémentation de code réutilisable de classes COM et WinRT, qui fournit l’implémentation de `QueryInterface`, `AddRef`, `Release` etc., gère le décompte de références du module et prend en charge en fournissant la fabrique de classe pour objets pouvant être activés.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Paramètres

*classFlags*  
Paramètre facultatif. Une combinaison d’une ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeurs d’énumération. Le `__WRL_CONFIGURATION_LEGACY__` macro peut être définie pour modifier la valeur par défaut classFlags pour toutes les classes de runtime dans le projet. S’il est défini, les instances de RuntimeClass sont non agiles par défaut. Lorsque ne pas défini, RuntimeClass instances sont agiles par défaut. Pour éviter toute ambiguïté toujours spécifier le `Microsoft::WRL::FtmBase` dans `TInterfaces` ou `RuntimeClassType::InhibitFtmBase`. Notez que, si InhibitFtmBase et FtmBase sont que tous deux utilisés de l’objet sera agile.

*TInterfaces*  
La liste des interfaces de l’objet implémente au-delà `IUnknown`, `IInspectable` ou d’autres interfaces contrôlés par [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). Il peut également répertorier les autres classes à être dérivé, notamment `Microsoft::WRL::FtmBase` pour rendre l’objet agile et le rendre implémenter `IMarshal`.

## <a name="members"></a>Membres

`RuntimeClassInitialize`<br/>
Une fonction qui initialise l’objet si le `MakeAndInitialize` fonction de modèle est utilisée pour construire l’objet. Elle retourne S_OK si l’objet a été correctement initialisé, ou un code d’erreur COM en cas d’échec de l’initialisation. Le code d’erreur COM est propagé en tant que valeur de retour de `MakeAndInitialize`. Notez que le `RuntimeClassInitialize` méthode n’est pas appelée si le `Make` fonction de modèle est utilisée pour construire l’objet.

### <a name="public-constructors"></a>Constructeurs publics

| Nom                                               | Description                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Initialise l’instance actuelle de la `RuntimeClass` classe.   |
| [RuntimeClass :: ~ RuntimeClass](#tilde-runtimeclass) | Annule l’initialisation de l’instance actuelle de la `RuntimeClass` classe. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                      | Description                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Incrémente le décompte de références pour actuel `RuntimeClass` objet.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Décrémente le décompte de références pour actuel `RuntimeClass` objet.                              |
| [RuntimeClass::GetIids](#getiids)                         | Obtient un tableau qui contient l’interface implémentées par actuel des ID `RuntimeClass` objet. |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Obtient le nom de classe runtime d’actuel `RuntimeClass` objet.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Obtient le niveau de confiance de l’actuel `RuntimeClass` objet.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Obtient un pointeur vers l’objet de référence faible pour actuel `RuntimeClass` objet.                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Incrémente le décompte de références actuel `RuntimeClass` objet.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Récupère un pointeur vers l’ID de l’interface spécifiée.                                                 |
| [RuntimeClass::Release](#release)                         | Effectue une opération de libération de COM sur actuel `RuntimeClass` objet.                             |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

Il s’agit d’un détail d’implémentation.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="tilde-runtimeclass"></a>RuntimeClass :: ~ RuntimeClass

Annule l’initialisation de l’instance actuelle de la `RuntimeClass` classe.

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>RuntimeClass::AddRef

Incrémente le décompte de références pour actuel `RuntimeClass` objet.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="decrementreference"></a>RuntimeClass::DecrementReference

Décrémente le décompte de références pour actuel `RuntimeClass` objet.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="getiids"></a>RuntimeClass::GetIids

Obtient un tableau qui contient l’interface implémentées par actuel des ID `RuntimeClass` objet.

```cpp
STDMETHOD(
   GetIids
)  
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*iidCount*  
Lorsque cette opération se termine, le nombre total d’éléments du tableau *IID*.

*IID*  
Lorsque cette opération se termine, un pointeur vers un tableau d’ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_OUTOFMEMORY.

## <a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Obtient le nom de classe runtime d’actuel `RuntimeClass` objet.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Paramètres

*runtimeName*  
Lorsque cette opération se termine, le nom de la classe runtime.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Une erreur d’assertion est émise si `__WRL_STRICT__` ou `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` n’est pas définie.

## <a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Obtient le niveau de confiance de l’actuel `RuntimeClass` objet.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Paramètres

*trustLvl*  
Lorsque cette opération se termine, le niveau de confiance de l’actuel `RuntimeClass` objet.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.

### <a name="remarks"></a>Notes

Une erreur d’assertion est émise si `__WRL_STRICT__` ou `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` n’est pas définie.

## <a name="getweakreference"></a>RuntimeClass::GetWeakReference

Obtient un pointeur vers l’objet de référence faible pour actuel `RuntimeClass` objet.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Paramètres

*weakReference*  
Lorsque cette opération se termine, un pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="internaladdref"></a>RuntimeClass::InternalAddRef

Incrémente le décompte de références actuel `RuntimeClass` objet.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de références qui en résulte.

## <a name="queryinterface"></a>RuntimeClass::QueryInterface

Récupère un pointeur vers l’ID de l’interface spécifiée.

```cpp
STDMETHOD(
   QueryInterface
)  
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*  
ID d’interface.

*ppvObject*  
Quand cette opereation est terminée, un pointeur vers l’interface spécifiée par le *riid* paramètre.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="release"></a>RuntimeClass::Release

Effectue une opération de libération de COM sur actuel `RuntimeClass` objet.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si le décompte de références devient égal à zéro, le `RuntimeClass` objet est supprimé.

## <a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Initialise l’instance actuelle de la `RuntimeClass` classe.

```cpp
RuntimeClass();
```
