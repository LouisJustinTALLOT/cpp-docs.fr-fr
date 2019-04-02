---
title: SimpleClassFactory (classe)
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784434"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory (classe)

Fournit un mécanisme fondamental pour créer une classe de base.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Paramètres

*Base*<br/>
Une classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser `SimpleClassFactory` avec la [ActivatableClassWithFactoryEx](activatableclass-macros.md) (macro).

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance, méthode](#createinstance)|Crée une instance de l’interface spécifiée.|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="createinstance"></a>Simpleclassfactory::CreateInstance, méthode

Crée une instance de l’interface spécifiée.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
Doit être `nullptr`; sinon, la valeur de retour est CLASS_E_NOAGGREGATION.

SimpleClassFactory ne prend pas en charge d’agrégation. Si l’agrégation ont été prise en charge et de l’objet en cours de création faisait partie d’un agrégat, *pUnkOuter* serait un pointeur vers le contrôle `IUnknown` interface de l’agrégat.

*riid*<br/>
ID d’interface de l’objet à créer.

*ppvObject*<br/>
Lorsque cette opération se termine, pointeur vers une instance de l’objet spécifié par le *riid* paramètre.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si n’est pas dérivée de la classe de base spécifiée dans le paramètre de modèle de classe [RuntimeClass](runtimeclass-class.md), ou n’est pas configuré avec le ClassicCom ou WinRtClassicComMix [ RuntimeClassType](runtimeclasstype-enumeration.md) valeur d’énumération.
