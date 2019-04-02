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
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784662"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un [ComPtr\<T >](comptr-class.md) type ou un type dérivé, pas simplement l’interface représentée par le `ComPtr`.

## <a name="remarks"></a>Notes

Représente la classe de base pour le [ComPtrRef](comptrref-class.md) classe.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | -------------------------------------------------
`InterfaceType` | Un synonyme du type de paramètre de modèle *T*.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                       | Description
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable **](#operator-iinspectable-star-star) | Effectue un cast en cours [ptr_](#ptr) données membres à un pointeur-à-un-pointeur-to la `IInspectable` interface.
[ComPtrRefBase::operator IUnknown **](#operator-iunknown-star-star)         | Effectue un cast en cours [ptr_](#ptr) données membres à un pointeur-à-un-pointeur-to la `IUnknown` interface.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Pointeur vers le type spécifié par le paramètre de modèle actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operator IInspectable\* \* opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Notes

Effectue un cast en cours [ptr_](#ptr) données membres à un pointeur-à-un-pointeur-to la `IInspectable` interface.

Une erreur est générée si actuel `ComPtrRefBase` ne dérive pas de `IInspectable`.

Ce cast est disponible uniquement si `__WRL_CLASSIC_COM__` est défini.

## <a name="operator-iunknown-star-star"></a>ComPtrRefBase::operator IUnknown **, opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Notes

Effectue un cast en cours [ptr_](#ptr) données membres à un pointeur-à-un-pointeur-to la `IUnknown` interface.

Une erreur est générée si actuel `ComPtrRefBase` ne dérive pas de `IUnknown`.

## <a name="ptr"></a>ComPtrRefBase::ptr_

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Notes

Pointeur vers le type spécifié par le paramètre de modèle actuel. `ptr_` est le membre de données protégées.
