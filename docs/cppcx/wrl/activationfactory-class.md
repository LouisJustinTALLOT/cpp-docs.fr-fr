---
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
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368705"
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
L’interface zéro.

*I1 (en)*<br/>
La première interface.

*I2 (en)*<br/>
La deuxième interface.

## <a name="remarks"></a>Notes

`ActivationFactory`fournit des méthodes d’enregistrement `IActivationFactory` et des fonctionnalités de base pour l’interface. `ActivationFactory`vous permet également de fournir une mise en œuvre d’usine personnalisée.

Le fragment de code suivant illustre symboliquement comment utiliser ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Le fragment de code suivant montre comment utiliser la structure [Des impléments](implements-structure.md) pour spécifier plus de trois interfaces iD.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                       | Description
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Initialise la classe `ActivationFactory`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                           | Description
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Incréments le nombre de `ActivationFactory` références de l’objet actuel.
[ActivationFactory::GetIids](#getiids)                         | Récupère une gamme d’interfaces implémentées.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Obtient le nom de classe de `ActivationFactory` temps d’exécution de l’objet que les instantanés actuels.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Obtient le niveau de confiance `ActivationFactory` de l’objet que les instantanés actuels.
[ActivationFactory::QueryInterface](#queryinterface)           | Récupère un pointeur sur l’interface spécifiée.
[ActivationFactory::Libération](#release)                         | Décrément le nombre de `ActivationFactory` références de l’objet actuel.

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

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>ActivationFactory::ActivationFactory

Initialise la classe `ActivationFactory`.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>ActivationFactory::AddRef

Incréments le nombre de `ActivationFactory` références de l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactorygetiids"></a><a name="getiids"></a>ActivationFactory::GetIids

Récupère une gamme d’interfaces implémentées.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*iidCompte*<br/>
Lorsque cette opération se termine, le nombre d’ID interaces dans le tableau *iids.*

*iids*<br/>
Lorsque cette opération se termine, une gamme d’interfaces implémentées.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. E_OUTOFMEMORY est un échec possible HRESULT.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Obtient le nom de classe de `ActivationFactory` temps d’exécution de l’objet que les instantanés actuels.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Paramètres

*runtimeName runtimeName runtimeName runtime*<br/>
Lorsque cette opération se termine, une poignée à une chaîne qui contient `ActivationFactory` le nom de classe runtime de l’objet que le courant instantanément.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Obtient le niveau de confiance `ActivationFactory` de l’objet que les instantanés actuels.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Paramètres

*trustLvl (en anglais)*<br/>
Lorsque cette opération se termine, le niveau de `ActivationFactory` confiance de la classe de temps d’exécution que les instantanés.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, une erreur d’affirmation est émise `FullTrust`et *trustLvl* est réglé à .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>ActivationFactory::QueryInterface

Récupère un pointeur sur l’interface spécifiée.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération est terminée, un pointeur à l’interface spécifiée par le *paramètre riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="activationfactoryrelease"></a><a name="release"></a>ActivationFactory::Libération

Décrément le nombre de `ActivationFactory` références de l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
