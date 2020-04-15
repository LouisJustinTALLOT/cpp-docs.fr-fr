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
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377173"
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

### <a name="parameters"></a>Paramètres

*TMemberFunction*<br/>
Paramètre typename pour une structure ArgTraits qui ne peut égaler aucune `Invoke` signature de méthode.

*TDelegateInterface*<br/>
Une interface déléguée.

*TArg1*<br/>
Le type du premier `Invoke` argument de la méthode.

*TArg2*<br/>
Le type du deuxième `Invoke` argument de la méthode.

*Targ3*<br/>
Le type du troisième `Invoke` argument de la méthode.

*TArg4 (en)*<br/>
Le type du quatrième `Invoke` argument de la méthode.

*TArg5*<br/>
Le type du cinquième `Invoke` argument de la méthode.

*TArg6 (TArg6)*<br/>
Le type du sixième `Invoke` argument de la méthode.

*TArg7 (en)*<br/>
Le type du septième `Invoke` argument de la méthode.

*TArg8*<br/>
Le type du huitième `Invoke` argument de la méthode.

*TArg9 (TArg9)*<br/>
Le type du neuvième `Invoke` argument de la méthode.

## <a name="remarks"></a>Notes

La `ArgTraits` structure déclare une interface de délégué spécifiée et une fonction de membre anonyme qui a un nombre spécifié de paramètres.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom       | Description
---------- | ----------------------
`Arg1Type` | Le tapdef pour TArg1.
`Arg2Type` | Le tapdef pour TArg2.
`Arg3Type` | Le tapdef pour TArg3.
`Arg4Type` | Le tapdef pour TArg4.
`Arg5Type` | Le tapdef pour TArg5.
`Arg6Type` | Le tapdef pour TArg6.
`Arg7Type` | Le tapdef pour TArg7.
`Arg8Type` | Le tapdef pour TArg8.
`Arg9Type` | Le tapdef pour TArg9.

### <a name="public-constants"></a>Constantes publiques

Nom                     | Description
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Conserve le nombre de paramètres `Invoke` sur la méthode d’une interface déléguée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ArgTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** event.h

**Espace nom:** Microsoft::WRL::Details

## <a name="argtraitsargs"></a><a name="args"></a>ArgTraits::args

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Notes

Conserve le nombre de paramètres `Invoke` sur la méthode d’une interface déléguée. Quand `args` est égal à -1, il `Invoke` ne peut y avoir de correspondance pour la signature de la méthode.
