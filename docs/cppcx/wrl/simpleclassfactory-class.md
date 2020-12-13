---
description: 'En savoir plus sur : classe SimpleClassFactory'
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
ms.openlocfilehash: cd771909790f80048d8fee678b842f820e2f7be2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135198"
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
Classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser `SimpleClassFactory` avec la macro [ActivatableClassWithFactoryEx](activatableclass-macros.md) .

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

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a> SimpleClassFactory :: CreateInstance, méthode

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
Doit être **`nullptr`** ; sinon, la valeur de retour est CLASS_E_NOAGGREGATION.

SimpleClassFactory ne prend pas en charge l’agrégation. Si l’agrégation était prise en charge et que l’objet en cours de création faisait partie d’un agrégat, *pUnkOuter* serait un pointeur vers l' `IUnknown` interface de contrôle de l’agrégat.

*riid*<br/>
ID d’interface de l’objet à créer.

*ppvObject*<br/>
Lorsque cette opération est terminée, pointeur vers une instance de l’objet spécifié par le paramètre *riid* .

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Si `__WRL_STRICT__` est défini, une erreur d’assertion est émise si la classe de base spécifiée dans le paramètre de modèle de classe n’est pas dérivée de [RuntimeClass](runtimeclass-class.md)ou n’est pas configurée avec la valeur d’énumération ClassicCom ou WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) .
