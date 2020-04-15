---
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
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376231"
---
# <a name="runtimeclass-class"></a>RuntimeClass, classe

Représente une classe WinRT ou COM qui hérite des interfaces spécifiées et fournit le Windows Runtime spécifié, com classique et faible support de référence.

Cette classe fournit la mise en œuvre de la `QueryInterface` `AddRef`plaque `Release` chauffante des classes WinRT et COM, fournissant la mise en œuvre de , , etc, gère le nombre de références du module et a le soutien pour fournir l’usine de classe pour les objets activatables.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Paramètres

*classesFlags*<br/>
Paramètre facultatif. Une combinaison d’une ou plusieurs valeurs d’énumération [RuntimeClassType.](runtimeclasstype-enumeration.md) La `__WRL_CONFIGURATION_LEGACY__` macro peut être définie pour modifier la valeur par défaut de classFlags pour toutes les classes de runtime dans le projet. Si elles sont définies, les instances RuntimeClass ne sont pas agiles par défaut. Lorsqu’elles ne sont pas définies, les instances RuntimeClass sont agiles par défaut. Pour éviter l’ambiguïté toujours spécifier l’in `Microsoft::WRL::FtmBase` `TInterfaces` ou `RuntimeClassType::InhibitFtmBase`. Notez que si InhibitFtmBase et FtmBase sont tous deux utilisés, l’objet sera agile.

*TInterfaces*<br/>
La liste des interfaces de `IUnknown` `IInspectable` l’objet implémente au-delà , ou d’autres interfaces contrôlées par [RuntimeClassType](runtimeclasstype-enumeration.md). Il peut également énumérer d’autres `Microsoft::WRL::FtmBase` classes à tirer, notamment `IMarshal`pour rendre l’objet agile et le faire implémenter .

## <a name="members"></a>Membres

`RuntimeClassInitialize`<br/>
Une fonction qui initialise l’objet si la fonction de `MakeAndInitialize` modèle est utilisée pour construire l’objet. Il renvoie S_OK si l’objet a été initialisé avec succès, ou un code d’erreur COM en cas d’échec de l’initialisation. Le code d’erreur COM est propagé `MakeAndInitialize`comme la valeur de retour de . Notez `RuntimeClassInitialize` que la méthode `Make` n’est pas appelée si la fonction de modèle est utilisée pour construire l’objet.

### <a name="public-constructors"></a>Constructeurs publics

| Nom                                               | Description                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Initialise l’instance actuelle `RuntimeClass` de la classe.   |
| [RuntimeClass: :-RuntimeClass](#tilde-runtimeclass) | Désinitialise l’instance actuelle `RuntimeClass` de la classe. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                      | Description                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Incréments le nombre de `RuntimeClass` références pour l’objet actuel.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Décrément le nombre de `RuntimeClass` références pour l’objet actuel.                              |
| [RuntimeClass::GetIids](#getiids)                         | Obtient un tableau qui peut contenir les interfaces ID implémentées par l’objet actuel. `RuntimeClass` |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Obtient le nom de classe `RuntimeClass` de temps d’exécution de l’objet actuel.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Obtient le niveau de `RuntimeClass` confiance de l’objet actuel.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Obtient un pointeur à l’objet de référence faible pour l’objet actuel. `RuntimeClass`                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Incréments le compte de `RuntimeClass` référence à l’objet actuel.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Récupère un pointeur sur l’id d’interface spécifié.                                                 |
| [RuntimeClass::Libération](#release)                         | Effectue une opération de version `RuntimeClass` COM sur l’objet actuel.                             |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

Il s'agit d'un détail d'implémentation.

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>RuntimeClass: :-RuntimeClass

Désinitialise l’instance actuelle `RuntimeClass` de la classe.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>RuntimeClass::AddRef

Incréments le nombre de `RuntimeClass` références pour l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>RuntimeClass::DecrementReference

Décrément le nombre de `RuntimeClass` références pour l’objet actuel.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>RuntimeClass::GetIids

Obtient un tableau qui peut contenir les interfaces ID implémentées par l’objet actuel. `RuntimeClass`

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*iidCompte*<br/>
Lorsque cette opération se termine, le nombre total d’éléments dans *les iids*de tableau .

*iids*<br/>
Lorsque cette opération se termine, un pointeur vers un tableau d’interface iD.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Obtient le nom de classe `RuntimeClass` de temps d’exécution de l’objet actuel.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Paramètres

*runtimeName runtimeName runtimeName runtime*<br/>
Lorsque cette opération se termine, le nom de classe de temps d’exécution.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Une erreur d’affirmation `__WRL_STRICT__` `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` est émise si ou n’est pas définie.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Obtient le niveau de `RuntimeClass` confiance de l’objet actuel.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Paramètres

*trustLvl (en anglais)*<br/>
Lorsque cette opération se termine, le `RuntimeClass` niveau de confiance de l’objet actuel.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.

### <a name="remarks"></a>Notes

Une erreur d’affirmation `__WRL_STRICT__` `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` est émise si ou n’est pas définie.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>RuntimeClass::GetWeakReference

Obtient un pointeur à l’objet de référence faible pour l’objet actuel. `RuntimeClass`

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Paramètres

*faibleReference*<br/>
Lorsque cette opération se termine, un pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>RuntimeClass::InternalAddRef

Incréments le compte de `RuntimeClass` référence à l’objet actuel.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de références qui en résulte.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>RuntimeClass::QueryInterface

Récupère un pointeur sur l’id d’interface spécifié.

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
Lorsque cette opereation se termine, un pointeur à l’interface spécifiée par le paramètre *riid.*

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="runtimeclassrelease"></a><a name="release"></a>RuntimeClass::Libération

Effectue une opération de version `RuntimeClass` COM sur l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si le nombre de `RuntimeClass` références devient nul, l’objet est supprimé.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Initialise l’instance actuelle `RuntimeClass` de la classe.

```cpp
RuntimeClass();
```
