---
title: ImplementsHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d734e98d8d7713451be1a16e08e58676f2b0cde4
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163684"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassFlagsT*<br/>
Un champ d’indicateurs qui spécifie un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.

*ILst*<br/>
Liste des ID d’interface.

*IsDelegateToClass*<br/>
Spécifiez **true** si l’instance actuelle de `Implements` est une classe de base de l’ID d’interface première dans *ILst*; sinon, **false**.

## <a name="remarks"></a>Notes

Permet d’implémenter le [implémente](../windows/implements-structure.md) structure.

Ce modèle parcourt une liste d’interfaces et les ajoute comme classes de base et en tant que les informations nécessaires pour activer `QueryInterface`.

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                    | Description
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Obtient un pointeur vers l’ID de l’interface spécifiée.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Obtient un pointeur vers sous-jacent `IUnknown` interface actif `Implements` structure.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié.
[ImplementsHelper::IidCount](#iidcount)                 | Contient le nombre d’ID d’interface implémentée dans le courant `Implements` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ImplementsHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="cancastto"></a>ImplementsHelper::CanCastTo

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*PPV*<br/>
Si cette opération réussite, un pointeur vers l’interface spécifiée par *riid* ou *iid*.

*IID*<br/>
Référence à un ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Obtient un pointeur vers l’ID de l’interface spécifiée.

## <a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet sous-jacent `IUnknown` interface.

### <a name="remarks"></a>Notes

Obtient un pointeur vers sous-jacent `IUnknown` interface actif `Implements` structure.

## <a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Index de base zéro qui indique l’élément de tableau de départ pour cette opération. Lorsque cette opération se termine, *index* est incrémentée de 1.

*IID*<br/>
Tableau de type IID.

### <a name="remarks"></a>Notes

Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié.

## <a name="iidcount"></a>ImplementsHelper::IidCount

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Notes

Contient le nombre d’ID d’interface implémentée dans le courant `Implements` objet.
