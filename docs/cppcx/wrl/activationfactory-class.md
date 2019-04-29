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
ms.openlocfilehash: 8e5132f4a8711f6420cd9b52751550a96d10d8fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303888"
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
L’interface de zéro.

*I1*<br/>
La première interface.

*I2*<br/>
La seconde interface.

## <a name="remarks"></a>Notes

`ActivationFactory` Fournit des méthodes d’inscription et fonctionnalités de base pour le `IActivationFactory` interface. `ActivationFactory` vous permet également de fournir une implémentation de la fabrique personnalisée.

Symboliquement, le fragment de code suivant illustre comment utiliser ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Le fragment de code suivant montre comment utiliser le [implémente](implements-structure.md) structure pour spécifier plus de trois ID d’interface.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                       | Description
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Initialise le `ActivationFactory` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                           | Description
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Incrémente le décompte de références de l’actuel `ActivationFactory` objet.
[ActivationFactory::GetIids](#getiids)                         | Récupère un tableau d’ID d’interface implémentée.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Obtient le nom de classe runtime de l’objet qui actuel `ActivationFactory` instancie.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Obtient le niveau de confiance de l’objet qui actuel `ActivationFactory` instancie.
[ActivationFactory::QueryInterface](#queryinterface)           | Récupère un pointeur vers l’interface spécifiée.
[ActivationFactory::Release](#release)                         | Décrémente le décompte de références de l’actuel `ActivationFactory` objet.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="activationfactory"></a>ActivationFactory::ActivationFactory

Initialise le `ActivationFactory` classe.

```cpp
ActivationFactory();
```

## <a name="addref"></a>ActivationFactory::AddRef

Incrémente le décompte de références de l’actuel `ActivationFactory` objet.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="getiids"></a>ActivationFactory::GetIids

Récupère un tableau d’ID d’interface implémentée.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*iidCount*<br/>
Lorsque cette opération se termine, le nombre d’ID interface dans le *IID* tableau.

*iids*<br/>
Lorsque cette opération est terminée, un tableau d’implémenté des ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. E_OUTOFMEMORY est un HRESULT d’échec possible.

## <a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Obtient le nom de classe runtime de l’objet qui actuel `ActivationFactory` instancie.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Paramètres

*runtimeName*<br/>
Lorsque cette opération se termine, un handle vers une chaîne qui contient le nom de classe runtime de l’objet qui actuel `ActivationFactory` instancie.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Obtient le niveau de confiance de l’objet qui actuel `ActivationFactory` instancie.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération est terminée, le niveau de confiance du runtime de classe qui le `ActivationFactory` instancie.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur d’assertion est émise et *trustLvl* est défini sur `FullTrust`.

## <a name="queryinterface"></a>ActivationFactory::QueryInterface

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
Lorsque cette opération est terminée, un pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="release"></a>ActivationFactory::Release

Décrémente le décompte de références de l’actuel `ActivationFactory` objet.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
