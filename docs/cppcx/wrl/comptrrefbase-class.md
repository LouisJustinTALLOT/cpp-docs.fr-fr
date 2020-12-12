---
description: 'En savoir plus sur : classe ComPtrRefBase'
title: ComPtrRefBase (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: 4dce58e8292092084916c24153d543f2a45856fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273135"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type [ComPtr \<T> ](comptr-class.md) ou type dérivé de celui-ci, pas simplement l’interface représentée par `ComPtr` .

## <a name="remarks"></a>Notes

Représente la classe de base pour la classe [ComPtrRef](comptrref-class.md) .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | -------------------------------------------------
`InterfaceType` | Synonyme du type de paramètre de modèle *T*.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                       | Description
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase :: Operator IInspectable * *](#operator-iinspectable-star-star) | Effectue un cast du membre de données de [PTR_](#ptr) actuel en pointeur vers l' `IInspectable` interface.
[ComPtrRefBase :: Operator IUnknown * *](#operator-iunknown-star-star)         | Effectue un cast du membre de données de [PTR_](#ptr) actuel en pointeur vers l' `IUnknown` interface.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase ::p tr_](#ptr) | Pointeur vers le type spécifié par le paramètre de modèle actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase :: Operator IInspectable, \* \* opérateur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Notes

Effectue un cast du membre de données de [PTR_](#ptr) actuel en pointeur vers l' `IInspectable` interface.

Une erreur est émise si le actuel `ComPtrRefBase` ne dérive pas de `IInspectable` .

Ce cast est disponible uniquement si `__WRL_CLASSIC_COM__` est défini.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a> ComPtrRefBase :: Operator IUnknown * *, opérateur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Notes

Effectue un cast du membre de données de [PTR_](#ptr) actuel en pointeur vers l' `IUnknown` interface.

Une erreur est émise si le actuel `ComPtrRefBase` ne dérive pas de `IUnknown` .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a> ComPtrRefBase ::p tr_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Notes

Pointeur vers le type spécifié par le paramètre de modèle actuel. `ptr_` est le membre de données protégé.
