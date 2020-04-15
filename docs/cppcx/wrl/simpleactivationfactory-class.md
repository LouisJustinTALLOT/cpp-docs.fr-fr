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
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370935"
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

L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la macro [ActivatableClassWithFactoryEx.](activatableclass-macros.md)

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, méthode](#activateinstance)|Crée une instance de l’interface spécifiée.|
|[SimpleActivationFactory::GetRuntimeClassName, méthode](#getruntimeclassname)|Obtient le nom de classe de temps d’exécution d’une instance de la classe spécifiée par le paramètre de modèle de classe *de base.*|
|[SimpleActivationFactory::GetTrustLevel, méthode](#gettrustlevel)|Obtient le niveau de confiance d’une instance de la classe spécifiée par le paramètre du modèle de classe *de base.*|

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

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>SimpleActivationFactory::ActivateInstance Method

Crée une instance de l’interface spécifiée.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Paramètres

*ppvObject*<br/>
Lorsque cette opération se termine, indiquez une `Base` instance de l’objet spécifiée par le paramètre du modèle de classe.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` elle est définie, une erreur d’affirmation est émise si la classe de base spécifiée dans le paramètre du modèle de classe n’est pas dérivée de [RuntimeClass](runtimeclass-class.md), ou n’est pas configurée avec la valeur d’énumération WinRt ou WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>SimpleActivationFactory::GetRuntimeClassName Méthode

Obtient le nom de classe de temps d’exécution d’une instance de la classe spécifiée par le paramètre de `Base` modèle de classe.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Paramètres

*runtimeName runtimeName runtimeName runtime*<br/>
Lorsque cette opération se termine, le nom de classe de temps d’exécution.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` elle est définie, une erreur d’affirmation `Base` est émise si la classe spécifiée par le paramètre du modèle de classe n’est pas dérivée de [RuntimeClass](runtimeclass-class.md), ou n’est pas configurée avec la valeur d’énumération WinRt ou WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>SimpleActivationFactory::GetTrustLevel Méthode

Obtient le niveau de confiance d’une `Base` instance de la classe spécifiée par le paramètre du modèle de classe.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Paramètres

*trustLvl (en anglais)*<br/>
Lorsque cette opération se termine, le niveau de confiance de l’objet de classe actuel.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.
