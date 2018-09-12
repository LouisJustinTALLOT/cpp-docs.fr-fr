---
title: Simpleactivationfactory, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07c37dbf1629461141d592eb1987ce071324e22c
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691469"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (classe)

Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Paramètres

*base de*  
Une classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) (macro).

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

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="activateinstance"></a>Simpleactivationfactory::activateinstance, méthode

Crée une instance de l’interface spécifiée.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Paramètres

*ppvObject*  
Lorsque cette opération se termine, pointeur vers une instance de l’objet spécifié par le `Base` paramètre de modèle de classe.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si n’est pas dérivée de la classe de base spécifiée dans le paramètre de modèle de classe [RuntimeClass](../windows/runtimeclass-class.md), ou n’est pas configuré avec le WinRt ou WinRtClassicComMix [ RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeur d’énumération.

## <a name="getruntimeclassname"></a>Simpleactivationfactory::getruntimeclassname, méthode

Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Paramètres

*runtimeName*  
Lorsque cette opération se termine, le nom de la classe runtime.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si la classe spécifiée par le `Base` n’est pas dérivé de paramètre de modèle de classe [RuntimeClass](../windows/runtimeclass-class.md), ou n’est pas configuré avec le WinRt ou WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeur d’énumération.

## <a name="gettrustlevel"></a>Simpleactivationfactory::gettrustlevel, méthode

Obtient le niveau de confiance d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Paramètres

*trustLvl*  
Lorsque cette opération se termine, le niveau de confiance de l’objet de classe actuel.

### <a name="return-value"></a>Valeur de retour

Toujours S_OK.
