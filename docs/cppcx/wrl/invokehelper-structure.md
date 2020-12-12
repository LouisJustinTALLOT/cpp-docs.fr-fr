---
description: 'En savoir plus sur : structure InvokeHelper'
title: InvokeHelper (structure)
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 0b9bb8abb59cce5a3c25d795d0946ffbe88d0076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299018"
---
# <a name="invokehelper-structure"></a>InvokeHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Type d’interface délégué.

*TCallback*<br/>
Type de la fonction de gestionnaire d’événements.

*argCount*<br/>
Nombre d’arguments dans une `InvokeHelper` spécialisation.

## <a name="remarks"></a>Notes

Fournit une implémentation de la `Invoke()` méthode basée sur le nombre et le type d’arguments spécifiés.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom     | Description
-------- | -----------------------------------------------------------------------------
`Traits` | Synonyme de la classe qui définit le type de chaque argument de gestionnaire d’événements.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                        | Description
------------------------------------------- | -------------------------------------------------------
[InvokeHelper :: InvokeHelper](#invokehelper) | Initialise une nouvelle instance de la classe `InvokeHelper`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                            | Description
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper :: Invoke](#invoke) | Appelle le gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

### <a name="public-data-members"></a>Membres de données publics

Nom                                 | Description
------------------------------------ | ----------------------------------------------------------
[InvokeHelper :: callback_](#callback) | Représente le gestionnaire d’événements à appeler lorsqu’un événement se produit.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InvokeHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Event. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="invokehelpercallback_"></a><a name="callback"></a> InvokeHelper :: callback_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Notes

Représente le gestionnaire d’événements à appeler lorsqu’un événement se produit.

Le `TCallback` paramètre de modèle spécifie le type du gestionnaire d’événements.

## <a name="invokehelperinvoke"></a><a name="invoke"></a> InvokeHelper :: Invoke

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>Paramètres

*arg1*<br/>
Argument 1.

*arg2*<br/>
Argument 2.

*Arg3*<br/>
Argument 3.

*Arg4*<br/>
Argument 4.

*Arg5*<br/>
Argument 5.

*arg6*<br/>
Argument 6.

*arg7*<br/>
Argument 7.

*arg8*<br/>
Argument 8.

*arg9*<br/>
Argument 9.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Appelle le gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a> InvokeHelper :: InvokeHelper

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Paramètres

*rappel*<br/>
Gestionnaire d'événements.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `InvokeHelper`.

Le `TCallback` paramètre de modèle spécifie le type du gestionnaire d’événements.
