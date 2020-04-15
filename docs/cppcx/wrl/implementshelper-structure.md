---
title: ImplementsHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371397"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassFlagsT RuntimeClassFlagsT*<br/>
Un champ de drapeaux qui spécifie un ou plusieurs enumérateurs [RuntimeClassType.](runtimeclasstype-enumeration.md)

*ILst ILst*<br/>
Une liste d’interfaces IDs.

*IsDelegateToClass*<br/>
Spécifier **vrai** `Implements` si l’exemple actuel est une classe de base de la première interface ID dans *ILst*; autrement, **faux**.

## <a name="remarks"></a>Notes

Aide à mettre en œuvre la structure [des outils.](implements-structure.md)

Ce modèle traverse une liste d’interfaces et les ajoute comme `QueryInterface`classes de base, et comme information nécessaire pour permettre .

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                    | Description
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Obtient un pointeur à l’ID d’interface spécifiée.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Obtient un pointeur `IUnknown` à l’interface sous-jacente pour la structure actuelle. `Implements`
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Insère l’id d’interface spécifié par le paramètre de modèle zéro actuel dans l’élément de tableau spécifié.
[ImplementsHelper::IidCount](#iidcount)                 | Détient le nombre d’interfaces implémentées dans l’objet actuel. `Implements`

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ImplementsHelper`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper::CanCastTo

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Référence à une interface ID.

*Ppv*<br/>
Si cette opération est réussie, un pointeur à l’interface spécifiée par *riid* ou *iid*.

*Iid*<br/>
Référence à une interface ID.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Obtient un pointeur à l’ID d’interface spécifiée.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers `IUnknown` l’interface sous-jacente.

### <a name="remarks"></a>Notes

Obtient un pointeur `IUnknown` à l’interface sous-jacente pour la structure actuelle. `Implements`

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Un index à base nulle qui indique l’élément de tableau de départ de cette opération. Lorsque cette opération se termine, *l’indice* est incrémenté par 1.

*iids*<br/>
Un tableau de type IIDs.

### <a name="remarks"></a>Notes

Insère l’id d’interface spécifié par le paramètre de modèle zéro actuel dans l’élément de tableau spécifié.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper::IidCount

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Notes

Détient le nombre d’interfaces implémentées dans l’objet actuel. `Implements`
