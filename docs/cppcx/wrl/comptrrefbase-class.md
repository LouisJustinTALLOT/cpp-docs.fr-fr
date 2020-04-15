---
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
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372616"
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
Un [ComPtr\<T>](comptr-class.md) type ou un type dérivé de lui, pas seulement l’interface représentée par le `ComPtr`.

## <a name="remarks"></a>Notes

Représente la classe de base pour la classe [ComPtrRef.](comptrref-class.md)

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | -------------------------------------------------
`InterfaceType` | Un synonyme pour le type de paramètre de modèle *T*.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                       | Description
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::opérateur IInspectable](#operator-iinspectable-star-star) | Lance le membre actuel [ptr_](#ptr) de données à un pointeur-à-un-pointeur-à l’interface. `IInspectable`
[ComPtrRefBase::opérateur IUnknown](#operator-iunknown-star-star)         | Lance le membre actuel [ptr_](#ptr) de données à un pointeur-à-un-pointeur-à l’interface. `IUnknown`

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr](#ptr) | Pointeur sur le type spécifié par le paramètre du modèle actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace nom:** Microsoft::WRL::Details

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase::opérateur IInspectable\* \* Opérateur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Notes

Lance le membre actuel [ptr_](#ptr) de données à un pointeur-à-un-pointeur-à l’interface. `IInspectable`

Une erreur est émise `ComPtrRefBase` si le courant `IInspectable`ne dérive pas de .

Ce casting n’est disponible que s’il `__WRL_CLASSIC_COM__` est défini.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase::opérateur IUnknown OPÉRATEUR

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Notes

Lance le membre actuel [ptr_](#ptr) de données à un pointeur-à-un-pointeur-à l’interface. `IUnknown`

Une erreur est émise `ComPtrRefBase` si le courant `IUnknown`ne dérive pas de .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Notes

Pointeur sur le type spécifié par le paramètre du modèle actuel. `ptr_`est le membre protégé des données.
