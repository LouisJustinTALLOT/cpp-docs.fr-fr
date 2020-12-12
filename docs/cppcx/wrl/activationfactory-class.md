---
description: 'En savoir plus sur : classe ActivationFactory'
title: ActivationFactory (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 7204a3c2f981947a03efba648dd91b69d582fee1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287838"
---
# <a name="activationfactory-class"></a>ActivationFactory (classe)

Permet à une ou plusieurs classes d'être activées par le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Paramètres

*I0*<br/>
Interface avant toute chose.

*I1*<br/>
Première interface.

*I2*<br/>
Deuxième interface.

## <a name="remarks"></a>Notes

`ActivationFactory` fournit des méthodes d’inscription et des fonctionnalités de base pour l' `IActivationFactory` interface. `ActivationFactory` vous permet également de fournir une implémentation de fabrique personnalisée.

Le fragment de code suivant illustre symboliquement comment utiliser ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Le fragment de code suivant montre comment utiliser la structure [Implements](implements-structure.md) pour spécifier plus de trois ID d’interface.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                       | Description
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory :: ActivationFactory](#activationfactory) | Initialise la classe `ActivationFactory`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                           | Description
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory :: AddRef](#addref)                           | Incrémente le décompte de références de l' `ActivationFactory` objet actuel.
[ActivationFactory :: Getiids,](#getiids)                         | Récupère un tableau d’ID d’interface implémentés.
[ActivationFactory :: Getruntimeclassname,](#getruntimeclassname) | Obtient le nom de la classe Runtime de l’objet que le en cours `ActivationFactory` instancie.
[ActivationFactory :: Gettrustlevel,](#gettrustlevel)             | Obtient le niveau de confiance de l’objet instancié par le actuel `ActivationFactory` .
[ActivationFactory :: QueryInterface](#queryinterface)           | Récupère un pointeur vers l’interface spécifiée.
[ActivationFactory :: Release](#release)                         | Décrémente le décompte de références de l' `ActivationFactory` objet actuel.

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

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a> ActivationFactory :: ActivationFactory

Initialise la classe `ActivationFactory`.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a> ActivationFactory :: AddRef

Incrémente le décompte de références de l' `ActivationFactory` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactorygetiids"></a><a name="getiids"></a> ActivationFactory :: Getiids,

Récupère un tableau d’ID d’interface implémentés.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*Iidcount,*<br/>
Lorsque cette opération est terminée, il s’agit du nombre d’ID interface dans le tableau *IID* .

*IID*<br/>
Lorsque cette opération est terminée, un tableau d’ID d’interface implémentée.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. E_OUTOFMEMORY est un HRESULT d’échec possible.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a> ActivationFactory :: Getruntimeclassname,

Obtient le nom de la classe Runtime de l’objet que le en cours `ActivationFactory` instancie.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Paramètres

*runtimeName*<br/>
Lorsque cette opération est terminée, un handle vers une chaîne qui contient le nom de la classe Runtime de l’objet instancié par le actuel `ActivationFactory` .

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a> ActivationFactory :: Gettrustlevel,

Obtient le niveau de confiance de l’objet instancié par le actuel `ActivationFactory` .

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération est terminée, le niveau de confiance de la classe Runtime que `ActivationFactory` instancie.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; dans le cas contraire, une erreur d’assertion est émise et *trustLvl* a la valeur `FullTrust` .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a> ActivationFactory :: QueryInterface

Récupère un pointeur vers l’interface spécifiée.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération est terminée, pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactoryrelease"></a><a name="release"></a> ActivationFactory :: Release

Décrémente le décompte de références de l' `ActivationFactory` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
