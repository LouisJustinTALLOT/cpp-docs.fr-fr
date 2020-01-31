---
title: ArgTraits (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821712"
---
# <a name="argtraits-structure"></a>ArgTraits (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parameters

*TMemberFunction*<br/>
Paramètre TypeName pour une structure ArgTraits qui ne peut pas correspondre à une signature de méthode `Invoke`.

*TDelegateInterface*<br/>
Interface de délégué.

*TArg1*<br/>
Type du premier argument de la méthode `Invoke`.

*TArg2*<br/>
Type du deuxième argument de la méthode `Invoke`.

*TArg3*<br/>
Type du troisième argument de la méthode `Invoke`.

*TArg4*<br/>
Type du quatrième argument de la méthode `Invoke`.

*TArg5*<br/>
Type du cinquième argument de la méthode `Invoke`.

*TArg6*<br/>
Type du sixième argument de la méthode `Invoke`.

*TArg7*<br/>
Type du septième argument de la méthode `Invoke`.

*TArg8*<br/>
Type du huitième argument de la méthode `Invoke`.

*TArg9*<br/>
Type du neuvième argument de la méthode `Invoke`.

## <a name="remarks"></a>Notes

La structure `ArgTraits` déclare une interface de délégué spécifiée et une fonction membre anonyme qui a un nombre spécifié de paramètres.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs publics

Name       | Description
---------- | ----------------------
`Arg1Type` | Typedef pour TArg1.
`Arg2Type` | Typedef pour TArg2.
`Arg3Type` | Typedef pour TArg3.
`Arg4Type` | Typedef pour TArg4.
`Arg5Type` | Typedef pour TArg5.
`Arg6Type` | Typedef pour TArg6.
`Arg7Type` | Typedef pour TArg7.
`Arg8Type` | Typedef pour TArg8.
`Arg9Type` | Typedef pour TArg9.

### <a name="public-constants"></a>Constantes publiques

Name                     | Description
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Conserve le nombre de paramètres sur la méthode `Invoke` d’une interface de délégué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ArgTraits`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** Event. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="args"></a>ArgTraits::args

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Notes

Conserve le nombre de paramètres sur la méthode `Invoke` d’une interface de délégué. Lorsque `args` est égal à-1, il ne peut y avoir aucune correspondance pour la signature de méthode `Invoke`.
