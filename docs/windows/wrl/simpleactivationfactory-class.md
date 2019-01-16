---
title: SimpleActivationFactory (classe)
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 1831a816d0967c2ca53f941128639ea368c1b727
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336392"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (classe)

Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Paramètres

*Base*<br/>
Une classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la [ActivatableClassWithFactoryEx](activatableclass-macros.md) (macro).

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, méthode](#activateinstance)|Crée une instance de l’interface spécifiée.|
|[SimpleActivationFactory::GetRuntimeClassName, méthode](#getruntimeclassname)|Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le *Base* paramètre de modèle de classe.|
|[SimpleActivationFactory::GetTrustLevel, méthode](#gettrustlevel)|Obtient le niveau de confiance d’une instance de la classe spécifiée par le *Base* paramètre de modèle de classe.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

`SimpleActivationFactory`

## <a name="requirements"></a>Spécifications

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="activateinstance"></a>Simpleactivationfactory::activateinstance, méthode

Crée une instance de l’interface spécifiée.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Paramètres

*ppvObject*<br/>
Lorsque cette opération se termine, pointeur vers une instance de l’objet spécifié par le `Base` paramètre de modèle de classe.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si n’est pas dérivée de la classe de base spécifiée dans le paramètre de modèle de classe [RuntimeClass](runtimeclass-class.md), ou n’est pas configuré avec le WinRt ou WinRtClassicComMix [ RuntimeClassType](runtimeclasstype-enumeration.md) valeur d’énumération.

## <a name="getruntimeclassname"></a>Simpleactivationfactory::getruntimeclassname, méthode

Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Paramètres

*runtimeName*<br/>
Lorsque cette opération se termine, le nom de la classe runtime.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si la classe spécifiée par le `Base` n’est pas dérivé de paramètre de modèle de classe [RuntimeClass](runtimeclass-class.md), ou n’est pas configuré avec le WinRt ou WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) valeur d’énumération.

## <a name="gettrustlevel"></a>Simpleactivationfactory::gettrustlevel, méthode

Obtient le niveau de confiance d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération se termine, le niveau de confiance de l’objet de classe actuel.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.
