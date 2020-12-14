---
description: 'En savoir plus sur : structure ImplementsHelper'
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
ms.openlocfilehash: 142cc532a89758c35c3387c398311acd077b8385
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249813"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassFlagsT*<br/>
Champ d’indicateurs qui spécifie un ou plusieurs énumérateurs [RuntimeClassType](runtimeclasstype-enumeration.md) .

*ILst*<br/>
Liste des ID d’interface.

*IsDelegateToClass*<br/>
Spécifiez **`true`** si l’instance actuelle de `Implements` est une classe de base du premier ID d’interface dans *ILst*; sinon, **`false`** .

## <a name="remarks"></a>Notes

Aide à implémenter la structure [Implements](implements-structure.md) .

Ce modèle parcourt une liste d’interfaces et les ajoute en tant que classes de base, ainsi que les informations nécessaires à l’activation `QueryInterface` .

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                    | Description
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper :: CanCastTo,](#cancastto)               | Obtient un pointeur vers l’ID d’interface spécifié.
[ImplementsHelper :: Casttounknown,](#casttounknown)       | Obtient un pointeur vers l’interface sous-jacente `IUnknown` pour la `Implements` structure actuelle.
[ImplementsHelper :: Fillarraywithiid,](#fillarraywithiid) | Insère l’ID d’interface spécifié par le paramètre de modèle avant toute chose actuel dans l’élément de tableau spécifié.
[ImplementsHelper :: Iidcount,](#iidcount)                 | Contient le nombre d’ID d’interface implémentés dans l' `Implements` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ImplementsHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a> ImplementsHelper :: CanCastTo,

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
Référence à un ID d’interface.

*ppv*<br/>
Si cette opération réussit, pointeur vers l’interface spécifiée par *riid* ou *IID*.

*vaut*<br/>
Référence à un ID d’interface.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Obtient un pointeur vers l’ID d’interface spécifié.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a> ImplementsHelper :: Casttounknown,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface sous-jacente `IUnknown` .

### <a name="remarks"></a>Notes

Obtient un pointeur vers l’interface sous-jacente `IUnknown` pour la `Implements` structure actuelle.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a> ImplementsHelper :: Fillarraywithiid,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Index de base zéro qui indique l’élément de départ du tableau pour cette opération. Lorsque cette opération est terminée, l' *index* est incrémenté de 1.

*IID*<br/>
Tableau de types iid.

### <a name="remarks"></a>Notes

Insère l’ID d’interface spécifié par le paramètre de modèle avant toute chose actuel dans l’élément de tableau spécifié.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a> ImplementsHelper :: Iidcount,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Notes

Contient le nombre d’ID d’interface implémentés dans l' `Implements` objet actuel.
