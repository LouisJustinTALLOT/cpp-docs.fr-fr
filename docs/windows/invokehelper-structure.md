---
title: InvokeHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6eccc9a7eacf9cdd3b98796f575d966b7b566864
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169535"
---
# <a name="invokehelper-structure"></a>InvokeHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename TDelegateInterface,
   typename TCallback,
   unsigned int argCount
>
struct InvokeHelper;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 0> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 1> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 2> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 3> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 4> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 5> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 6> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 7> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 8> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 9> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
*TCallback*  
Le type de la fonction de gestionnaire d’événements.

*argCount*<br/>
Le nombre d’arguments dans un `InvokeHelper` spécialisation.

## <a name="remarks"></a>Notes

Fournit une implémentation de la `Invoke()` méthode basée sur le nombre spécifié et le type d’arguments.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom     | Description
-------- | -----------------------------------------------------------------------------
`Traits` | Synonyme de la classe qui définit le type de chaque argument de gestionnaire d’événements.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                        | Description
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Initialise une nouvelle instance de la classe `InvokeHelper`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                            | Description
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

### <a name="public-data-members"></a>Membres de données publics

Nom                                 | Description
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Représente le Gestionnaire d’événements à appeler lorsqu’un événement se produit.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InvokeHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="callback"></a>InvokeHelper::callback_

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Notes

Représente le Gestionnaire d’événements à appeler lorsqu’un événement se produit.

Le `TCallback` paramètre de modèle spécifie le type du Gestionnaire d’événements.

## <a name="invoke"></a>InvokeHelper::Invoke

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*Arg2*<br/>
Argument 2.

*Arg3*<br/>
Argument 3.

*Arg4*<br/>
Argument 4.

*Arg5*<br/>
Argument 5.

*Arg6*<br/>
Argument 6.

*Arg7*<br/>
Argument 7.

*Arg8*<br/>
Argument 8.

*Arg9*<br/>
Argument 9.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.

## <a name="invokehelper"></a>InvokeHelper::InvokeHelper

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Paramètres

*rappel*<br/>
Un gestionnaire d’événements.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `InvokeHelper`.

Le `TCallback` paramètre de modèle spécifie le type du Gestionnaire d’événements.
