---
description: 'En savoir plus sur : classe SimpleActivationFactory'
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
ms.openlocfilehash: 83643c69977b887e58e430bbd500fcf7c2e81ca6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135211"
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
Classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la macro [ActivatableClassWithFactoryEx](activatableclass-macros.md) .

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, méthode](#activateinstance)|Crée une instance de l’interface spécifiée.|
|[SimpleActivationFactory::GetRuntimeClassName, méthode](#getruntimeclassname)|Obtient le nom de la classe d’exécution d’une instance de la classe spécifiée par le paramètre de modèle de classe de *base* .|
|[SimpleActivationFactory::GetTrustLevel, méthode](#gettrustlevel)|Obtient le niveau de confiance d’une instance de la classe spécifiée par le paramètre de modèle de classe de *base* .|

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

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a> SimpleActivationFactory :: Activateinstance,, méthode

Crée une instance de l’interface spécifiée.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Paramètres

*ppvObject*<br/>
Lorsque cette opération est terminée, pointeur vers une instance de l’objet spécifié par le `Base` paramètre de modèle de classe.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si la classe de base spécifiée dans le paramètre de modèle de classe n’est pas dérivée de [RuntimeClass](runtimeclass-class.md), ou n’est pas configurée avec la valeur d’énumération [RuntimeClassType](runtimeclasstype-enumeration.md) WinRt ou WinRtClassicComMix.

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a> SimpleActivationFactory :: Getruntimeclassname,, méthode

Obtient le nom de la classe d’exécution d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Paramètres

*runtimeName*<br/>
Lorsque cette opération est terminée, le nom de la classe d’exécution.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si la classe spécifiée par le `Base` paramètre de modèle de classe n’est pas dérivée de [RuntimeClass](runtimeclass-class.md)ou n’est pas configurée avec la valeur d’énumération [RuntimeClassType](runtimeclasstype-enumeration.md) WinRt ou WinRtClassicComMix.

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a> SimpleActivationFactory :: Gettrustlevel,, méthode

Obtient le niveau de confiance d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération est terminée, le niveau de confiance de l’objet de classe actuel.

### <a name="return-value"></a>Valeur renvoyée

Toujours S_OK.
